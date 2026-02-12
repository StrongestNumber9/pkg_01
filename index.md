---
layout: default
---

To use the repository, create `/etc/yum.repos.d/teragrep-central-releases.repo` with the following content:
{% capture repofile %}{% for file in site.static_files %}{% if file.path contains '.repo' %}{% include_relative {{ file.path }} %}{% endif %}{% endfor %}{% endcapture %}
```ini
{{ repofile | strip }}
```

All central files:
<ul>
  {% for file in site.static_files %}
    {% if file.path contains 'central/' %}
      <li><a href="{{ site.baseurl }}{{ file.path }}">{{ file.path  }}</a></li>
    {% endif %}
  {% endfor %}
</ul>
