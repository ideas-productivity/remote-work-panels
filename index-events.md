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
{% assign mca = site.mc-announcements | where: "event-id", item.event-id %}
{% assign mcf = site.mc-followups | where: "event-id", item.event-id %}

{{ item.event-id }}\. **{{ item.title }}** ({{ item.date | date: "%F" }})

{% if item.archives %}
  {% include validate-artifact name='archives' artifacts=item.archives
    url_or_note=true url_xor_note=false require_format=true %}
{% endif %}

{% if item.panelist-ids %}
  {% include validate-person-ids type="panelist" pids=item.panelist-ids people=site.people %}
{% endif %}

{% if item.moderator-ids %}
  {% include validate-person-ids type="moderator" pids=item.moderator-ids people=site.people %}
{% endif %}

{% include event-attributes-table event=item %}

*Formats* | [Web]({{ site.baseurl }}{{ item.url }}) | [BSSw Event]({{ site.baseurl }}{{ be[0].url }}) | [BSSw Miscellaneous]({{ site.baseurl }}{{ bed[0].url }}) | [i-p.o WordPress]({{ site.baseurl }}{{ ipo[0].url }})
 | [YouTube]({{ site.baseurl }}{{ yt[0].url }}) | [Connection Email]({{ site.baseurl }}{{ ce[0].url }}) | [MailChimp Announcements]({{ site.baseurl }}{{ mca[0].url }}) | [MailChimp Followups]({{ site.baseurl }}{{ mcf[0].url }})

{% endfor %}
