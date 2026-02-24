---
layout: default
---

{% for repo in site.repos %}
<h1>{{ repo.name }}</h1>

{{ repo.description }}

{% capture repofile %}{% for file in site.static_files %}{% if file.path contains '.repo' and file.path contains repo.path %}{{ file.path }}{% endif %}{% endfor %}{% endcapture %}

To use the repository, create a `/etc/yum.repos.d/{{ repofile | split: "/" | last }}` file with the following content:
```ini
{% include_relative {{ repofile }} -%}
```

All {{ repo.name }} files:
<ul>
  {% for file in site.static_files %}
    {% if file.path contains repo.path %}
      <li><a href="{{ site.baseurl }}{{ file.path }}">{{ file.path }}</a></li>
    {% endif %}
  {% endfor %}
</ul>

{% endfor %}
