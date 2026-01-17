---
layout: default
title: Blog
permalink: /blog/
---

Welcome to my blog. Here I share my thoughts on software engineering, algorithms, and system design.

<ul>
  {% for post in site.posts %}
    <li>
      <h2><a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></h2>
      <p>{{ post.date | date: "%B %-d, %Y" }}</p>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>
