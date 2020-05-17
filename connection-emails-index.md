---
layout: home
---
## List of Connection Information Emails

Events should have the UPCOMING and READY-FOR-EVENT attributes prior to publication.

{% assign seq = site.connection-emails | sort: "panel-id" | reverse %}
{% include list-of-pages.md sequence=seq %}
