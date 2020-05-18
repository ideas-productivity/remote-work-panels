{% for event in include.sequence %}

{{ event.event-id }}\. [**{{ event.title }}**]({{ site.baseurl }}{{ event.url }}) ({{ event.date | date: "%F" }})
{% include event-attributes-table event=event %}
{% endfor %}
