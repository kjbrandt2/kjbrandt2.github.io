---
layout: page
title: Blog
permalink: /blog/
---

Practical notes on inspection readiness, quality systems, vendor oversight, and operational execution.

Subscribe via RSS: **[feed.xml](/feed.xml)**

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <small> — {{ post.date | date: "%Y-%m-%d" }}</small>
    </li>
  {% endfor %}
</ul>
