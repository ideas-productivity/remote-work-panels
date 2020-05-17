---
layout: home
---
## List of All Generated Formats, by Event

[BSSw Curated Content](swr-panels-cc.md)

{% assign sequence = site.events | sort: "panel-id" | reverse %}
{% for panel in sequence %}

{% include upcoming-event event=panel.date %}
{% include ready-to-advertise panel=panel %}
{% include ready-for-event panel=panel %}

{% assign be = site.bssw-events | where: "panel-id", panel.panel-id %}
{% assign bed = site.bssw-events-digest | where: "panel-id", panel.panel-id %}
{% assign ipw = site.ipweb-entries | where: "panel-id", panel.panel-id %}
{% assign yt = site.youtube-videos | where: "panel-id", panel.panel-id %}
{% assign ce = site.connection-emails | where: "panel-id", panel.panel-id %}

{{ panel.panel-id }}\. **{{ panel.title }}** ({{ panel.date | date: "%F" }})

{% include panel-attributes-table panel=panel %}

*Formats* | [Web]({{ site.baseurl }}{{ panel.url }}) | [BSSw Event]({{ site.baseurl }}{{ be[0].url }}) | [BSSw Digest]({{ site.baseurl }}{{ bed[0].url }}) | [i-p.o WordPress]({{ site.baseurl }}{{ ipw[0].url }})
 | [YouTube]({{ site.baseurl }}{{ yt[0].url }}) | [Connection Email]({{ site.baseurl }}{{ ce[0].url }})

{% endfor %}
