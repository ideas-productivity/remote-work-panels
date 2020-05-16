{% for panel in include.sequence %}

{{ panel.panel-id }}\. [**{{ panel.title }}**]({{ site.baseurl }}{{ panel.url }}) ({{ panel.date | date: "%F" }})
{% include panel-attributes-table panel=panel %}
{% endfor %}
