---
layout: page
title: Blogs
permalink: /blog/
---

<div class="page-content">
  <h1>Blog</h1>

  <div class="post-grid">
    {% for post in site.posts %}
    <a href="{{ post.url | relative_url }}" class="post-card">
      <h3 class="post-card-title">{{ post.title }}</h3>
    </a>
    {% endfor %}
  </div>
</div>
