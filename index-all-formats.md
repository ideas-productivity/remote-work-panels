---
layout: home
---
## List of All Generated Formats, by Event

[BSSw Curated Content](swr-panels-cc.md)

{% assign sequence = site.events | sort: "event-id" | reverse %}
{% for panel in sequence %}

{% include upcoming-event event=panel.date %}
{% include ready-to-advertise panel=panel %}
{% include ready-for-event panel=panel %}

{% assign be = site.bssw-events | where: "event-id", panel.event-id %}
{% assign bed = site.bssw-events-digest | where: "event-id", panel.event-id %}
{% assign ipw = site.ipo-events | where: "event-id", panel.event-id %}
{% assign yt = site.youtube-videos | where: "event-id", panel.event-id %}
{% assign ce = site.connection-emails | where: "event-id", panel.event-id %}

{{ panel.event-id }}\. **{{ panel.title }}** ({{ panel.date | date: "%F" }})

{% include event-attributes-table panel=panel %}

*Formats* | [Web]({{ site.baseurl }}{{ panel.url }}) | [BSSw Event]({{ site.baseurl }}{{ be[0].url }}) | [BSSw Digest]({{ site.baseurl }}{{ bed[0].url }}) | [i-p.o WordPress]({{ site.baseurl }}{{ ipw[0].url }})
 | [YouTube]({{ site.baseurl }}{{ yt[0].url }}) | [Connection Email]({{ site.baseurl }}{{ ce[0].url }})

{% endfor %}
