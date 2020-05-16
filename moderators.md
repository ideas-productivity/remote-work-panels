---
layout: home
---
## List of Moderators

<dl>
{% for moderator in site.moderators %}
<section style="margin-bottom: 15px">
  <dt>
    <a href="{{ site.baseurl }}{{ moderator.url }}">
  	  <strong>{{ moderator.firstname }} {{ moderator.lastname }},</strong>
	</a>
    {% if moderator.affiliations %}
      {{ moderator.affiliations | array_to_sentence_string | markdownify |
          remove: "<p>" | remove: "</p>" }}
    {% endif %}
  </dt> 

{% assign w = site.panels | where: "moderator-ids", moderator.person-id | sort: "panel-id" | reverse %}
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
