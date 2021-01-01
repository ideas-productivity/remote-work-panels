---
layout: home
---
## List of Events

<dl>
{% assign sequence = site.events | sort: "event-id" | reverse %}
{% for panel in sequence %}


{% assign psize = panel.panelist-ids | size %}
{% capture plabel %}{% include emit-plural text="Panelist" count=psize %}{% endcapture %}

{% assign msize = panel.moderator-ids | size %}
{% capture mlabel %}{% include emit-plural text="Moderator" count=msize %}{% endcapture %}

<section style="margin-bottom: 15px">
  <dt>{{ panel.event-id }}. 
      <strong><a href="{{ site.baseurl }}{{ panel.url }}">{{ panel.title }}</a></strong> ({{ panel.date | date: "%F" }})
  </dt> 
	<dd style="margin-left: 30px"><strong>{{ plabel }}:</strong> 
    {% include emit-name-affiliation-string pids=panel.panelist-ids people=site.people 
      if_empty="<em>to be announced</em>" %}
      </dd>
	<dd style="margin-left: 30px"><strong>{{ mlabel }}:</strong> 
      {% include emit-name-affiliation-string pids=panel.moderator-ids people=site.people 
      if_empty="<em>to be announced</em>" %}
      </dd>
</section>
{% endfor %}
</dl>
