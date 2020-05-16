---
layout: home
---
## List of Panelists

<dl>
{% for panelist in site.panelists %}
<section style="margin-bottom: 15px">
  <dt>
    <a href="{{ site.baseurl }}{{ panelist.url }}">
  	  <strong>{{ panelist.firstname }} {{ panelist.lastname }},</strong>
	</a>
    {% if panelist.affiliations %}
      {{ panelist.affiliations | array_to_sentence_string | markdownify |
          remove: "<p>" | remove: "</p>" }}
    {% endif %}
  </dt> 

{% assign w = site.panels | where: "panelist-ids", panelist.person-id | sort: "panel-id" | reverse %}
  {% if w %}
    {% for w2 in w %}
      <dd style="margin-left: 30px">{{ w2.panel-id }}. 
        <strong><a href="{{ site.baseurl }}{{ w2.url }}">{{ w2.title }}</a></strong> ({{ w2.date | date: "%F" }})
      </dd>
    {% endfor %}
  {% endif %}

</section>
{% endfor %}
</dl>
