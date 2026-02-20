---
layout: page
title: Blogs
permalink: /blog/
---

<div class="page-content">
  <h1>Blog</h1>
  <p class="page-subtitle">Thoughts on data science, ethics, and the world.</p>

  <div class="post-grid">
    {% for post in site.posts %}
    <a href="{{ post.url }}" class="post-card">
      <p class="post-card-date">{{ post.date | date: "%B %d, %Y" }}</p>
      <h3 class="post-card-title">{{ post.title }}</h3>
      {% if post.excerpt %}
      <p class="post-card-excerpt">{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
      {% endif %}
    </a>
    {% endfor %}
  </div>
</div>
