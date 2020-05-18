---
layout: home
---
## List of All Generated Formats, by Person

{% assign sequence = site.people | sort: "person-id" %}
{% for item in sequence %}

**{{ item.firstname }} {{ item.lastname }}**

{% include person-attributes-table person=item %}

*Formats* | [Web]({{ site.baseurl }}{{ item.url }}) 

{% endfor %}
