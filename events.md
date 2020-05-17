---
layout: home
---
## List of Events

<dl>
{% assign sequence = site.events | sort: "panel-id" | reverse %}
{% for panel in sequence %}


{% assign psize = panel.panelist-ids | size %}
{% if psize == 1 %}
  {%- assign plabel = "Panelist:" -%}
{% else %}
  {%- assign plabel = "Panelists:" -%}
{% endif %}

{%- assign pstring = "" -%}
{% for pid in panel.panelist-ids %}
  {% if forloop.index > 1 %}
    {% assign pstring = pstring | append: ", " %}
    {% if forloop.last %}
      {% assign pstring = pstring | append: " and " %}
    {% endif %}
  {% endif %}

  {%- assign p = site.people | where: "person-id", pid -%}
  {%- capture pafil -%}{{ p[0].firstname }} {{ p[0].lastname }} ({{- p[0].affiliations | array_to_sentence_string | lstrip | rstrip -}}){%- endcapture -%}
  {%- assign pstring = pstring | append: pafil -%}
{% endfor %}

{% assign msize = panel.moderator-ids | size %}
{% if msize == 1 %}
  {%- assign mlabel = "Moderator:" -%}
{% else %}
  {%- assign mlabel = "Moderators:" -%}
{% endif %}

{%- assign mstring = "" -%}
{% for mid in panel.moderator-ids %}
  {% if forloop.index > 1 %}
    {% assign mstring = mstring | append: ", " %}
    {% if forloop.last %}
      {% assign mstring = mstring | append: " and " %}
    {% endif %}
  {% endif %}

  {%- assign m = site.people | where: "person-id", mid -%}
  {%- capture mafil -%}{{ m[0].firstname }} {{ m[0].lastname }} ({{- m[0].affiliations | array_to_sentence_string | lstrip | rstrip -}}){%- endcapture -%}
  {%- assign mstring = mstring | append: mafil -%}
{% endfor %}

<section style="margin-bottom: 15px">
  <dt>{{ panel.panel-id }}. 
      <strong><a href="{{ site.baseurl }}{{ panel.url }}">{{ panel.title }}</a></strong> ({{ panel.date | date: "%F" }})
  </dt> 
    {% if pstring %}
	<dd style="margin-left: 30px"><strong>{{ plabel }}</strong> {{ pstring | markdownify | remove: "<p>" | remove: "</p>" | strip }}
      </dd>
    {% endif %}
    {% if mstring %}
	<dd style="margin-left: 30px"><strong>{{ mlabel }}</strong> {{ mstring | markdownify | remove: "<p>" | remove: "</p>" | strip }}
      </dd>
    {% endif %}
</section>
{% endfor %}
</dl>
