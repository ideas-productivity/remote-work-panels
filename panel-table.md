---
layout: default
---
{% assign archive_base = "https://ideas-productivity.org/events/strategies-for-working-remotely-panels//#panel" %}
<table>
  <tr>
    <th>No.</th>
    <th>Date</th>
    <th>Title, Panelist(s)</th>
  </tr>

{% for panel in site.events %}
  {% capture seqnum %}{{ panel.event-id | prepend: "00" | slice: -3, 3 }}{% endcapture %}
  <tr>
    <td>{{ panel.event-id }}</td>
    <td>{{ panel.date | date: "%a %-d %b %Y %-I:%M %P %Z" }}</td>
    <td><em><a href="{{ archive_base }}{{ seqnum }}">{{ panel.title}}</a>,</em> 
	  {{ panel.author }}
    </td>
  </tr>
{% endfor %}
</table>
