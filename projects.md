---
layout: page
title: Projects
permalink: /projects/
---

Here are some of the projects I have been working on.

{% for project in site.projects %}
## [{{ project.title }}]({{ project.url | relative_url }})
*{{ project.description }}*
{% endfor %}
