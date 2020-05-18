---
layout: home
---
## List of All Generated Formats, by Event

[BSSw Curated Content](swr-panels-cc.md)

{% assign sequence = site.events | sort: "event-id" | reverse %}
{% for item in sequence %}

{% assign be = site.bssw-events | where: "event-id", item.event-id %}
{% assign bed = site.bssw-events-digest | where: "event-id", item.event-id %}
{% assign ipo = site.ipo-events | where: "event-id", item.event-id %}
{% assign yt = site.youtube-videos | where: "event-id", item.event-id %}
{% assign ce = site.connection-emails | where: "event-id", item.event-id %}

{{ item.event-id }}\. **{{ item.title }}** ({{ item.date | date: "%F" }})

{% include event-attributes-table event=item %}

*Formats* | [Web]({{ site.baseurl }}{{ item.url }}) | [BSSw Event]({{ site.baseurl }}{{ be[0].url }}) | [BSSw Digest]({{ site.baseurl }}{{ bed[0].url }}) | [i-p.o WordPress]({{ site.baseurl }}{{ ipo[0].url }})
 | [YouTube]({{ site.baseurl }}{{ yt[0].url }}) | [Connection Email]({{ site.baseurl }}{{ ce[0].url }})

{% endfor %}
