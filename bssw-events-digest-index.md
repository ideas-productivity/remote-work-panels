---
layout: home
---
## List of BSSw Event Digest Entries

BSSw Event Digest entries should have the UPCOMING and READY-TO-ADVERTISE attributes prior to publication.

{% assign seq = site.bssw-events-digest | sort: "panel-id" | reverse %}
{% include list-of-pages.md sequence=seq %}
