---
layout: home
---
## List of Events

<dl>
{% assign sequence = site.events | sort: "event-id" | reverse %}
{% for panel in sequence %}


{% include extract-array-subset key="person-id" values=panel.panelist-ids source=site.people %}
{% include set-name-affiliation-array people=extract_subset_array %}
{% capture pnamafil %}{% include array-to-sentence array=name_affiliation_array 
  if_empty="<em>to be announced</em>" %}{% endcapture %}
{% capture pbios %}{% include emit-array-content.html array=extract_subset_array %}{% endcapture %}
{% assign psize = extract_subset_array | size %}
{% capture plabel %}{% include emit-plural text="Panelist" count=psize %}{% endcapture %}
{% capture blabel %}{% include emit-plural text="Panelist Bio" count=psize %}{% endcapture %}
{% include set-gh-profile-links-array people=extract_subset_array gh_base_url=site.github-url -%}
{% assign contributor_gh_profile_links = gh_profile_links_array %}

{% include extract-array-subset key="person-id" values=panel.moderator-ids source=site.people %}
{% include set-name-affiliation-array people=extract_subset_array %}
{% assign moderator_name_affiliations = name_affiliation_array %}
{% capture mnamafil %}{% include array-to-sentence array=name_affiliation_array 
  if_empty="<em>to be announced</em>" %}{% endcapture %}
{% capture mbios %}{% include emit-array-content.html array=extract_subset_array %}{% endcapture %}
{% assign msize = extract_subset_array | size %}
{% capture mlabel %}{% include emit-plural text="Moderator" count=msize %}{% endcapture %}
{% capture mblabel %}{% include emit-plural text="Moderator Bio" count=msize %}{% endcapture %}
{% include set-gh-profile-links-array people=extract_subset_array gh_base_url=site.github-url -%}
{% assign contributor_gh_profile_links = contributor_gh_profile_links | concat: gh_profile_links_array %}

<section style="margin-bottom: 15px">
  <dt>{{ panel.event-id }}. 
      <strong><a href="{{ site.baseurl }}{{ panel.url }}">{{ panel.title }}</a></strong> ({{ panel.date | date: "%F" }})
  </dt> 
	<dd style="margin-left: 30px"><strong>{{ plabel }}:</strong> 
    {{ pnamafil }}
      </dd>
	<dd style="margin-left: 30px"><strong>{{ mlabel }}:</strong> 
    {{ mnamafil }}
      </dd>
</section>
{% endfor %}
</dl>
