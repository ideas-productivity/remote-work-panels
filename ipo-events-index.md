---
layout: home
---
## List of ideas-productivity.org Wordpress Fragments

The main panel page on i-p.o has two distinct sections.

For the UPCOMING section, panels should have the UPCOMING and READY-TO-ADVERTISE attributes prior to publication.  This also applies to the Upcoming Events bullet on the main and Events pages of the site.

For the PAST section, panels should have the PAST attribute.  Eventually, as they acquire the ARCHIVES attribute, they will need to be updated.

{% assign seq = site.ipo-events | sort: "panel-id" | reverse %}
{% include list-of-pages.md sequence=seq %}
