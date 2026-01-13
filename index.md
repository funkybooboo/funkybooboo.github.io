---
layout: home
title: Home
---

# Hi, I'm Nate Stott.
## Software Engineer | Computer Scientist

Welcome to my portfolio. This is where I document my work in software engineering, share updates on my projects, and occasionally write about technology.

Check out my [Projects](/projects/) to see what I've been building, or visit the [About Me](/about/) page for my full background and resume.

### Recent Updates

<ul>
  {% for post in site.posts limit:3 %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a> - {{ post.date | date: "%B %d, %Y" }}
    </li>
  {% endfor %}
</ul>
