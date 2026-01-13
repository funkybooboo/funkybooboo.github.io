---
layout: home
title: Home
---

# Hi, I'm Nate Stott.
## Software Engineer | Computer Scientist

I am a Software Engineer and Computer Science MS candidate at Utah State University. I focus on building scalable systems, engineering software solutions, and applying rigorous development practices.

Check out my [Projects](/projects/) or learn more [About Me](/about/).

### Recent Updates

<ul>
  {% for post in site.posts limit:3 %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a> - {{ post.date | date: "%B %d, %Y" }}
    </li>
  {% endfor %}
</ul>
