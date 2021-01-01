{% comment %}
  emit-gh-profile-link.md: emit the GitHub link based on a person's record
    example: "[firstname lastname](gh-link "firstname lastname's GitHub profile")"
    using Markdown link syntax

  arguments:
    `person`: record containing the person's information
    `gh_base_url`: Base URL for GitHub profile links

  Expected elements of person structure
    lastname (string)
    firstname (string)
    github-id (string)

  Notes:
  * if there is no github-id in the record, output just the name, without link markup

  FIXME: why do we have to specify element 0 here?
 {% endcomment %}

{%- assign emit_gh_profile_link_name = include.person[0].firstname | append: " " | append: include.person[0].lastname | strip -%}
{%- if include.person[0].github-id -%}
{%- assign emit_gh_profile_link_url = include.gh_base_url | append: include.person[0].github-id | strip -%}
[{{ emit_gh_profile_link_name }}]({{ emit_gh_profile_link_url }} "{{ emit_gh_profile_link_name }}'s GitHub Profile")
{%- else -%}
{{ emit_gh_profile_link_name }}
{%- endif -%}