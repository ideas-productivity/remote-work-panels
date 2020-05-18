---
layout: home
---
## List of by Person (Web format)

{% assign sequence = site.people | sort: "person-id" %}
{% for item in sequence %}

{{ item.person-id }}: [**{{ item.firstname }} {{ item.lastname }}**]({{ site.baseurl }}{{ item.url }})

{% include person-attributes-table person=item %}

{% endfor %}
