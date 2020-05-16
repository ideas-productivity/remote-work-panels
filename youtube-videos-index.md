---
layout: home
---
## List of YouTube Fragments

YouTube publication is part of the archival process.  Panels of
interest here will have the PAST attribute, and publication of the
video to YouTube will contribute to the acquisition of the ARCHIVES
attribute.


{% assign seq = site.youtube-videos | sort: "panel-id" | reverse %}
{% include list-of-pages.md sequence=seq %}
