---
layout: page
title: Projects
permalink: /projects/
---

<div class="page-content">
  <h1>Projects</h1>

  {% assign projects = site.data.projects | where_exp: "p", "p.title" %}
  {% if projects.size > 0 %}
    <div class="post-grid">
      {% for project in projects %}
      <div class="post-card">
        <h3 class="post-card-title">
          {% if project.link %}
            <a href="{{ project.link }}" target="_blank" rel="noopener noreferrer">{{ project.title }}</a>
          {% else %}
            {{ project.title }}
          {% endif %}
        </h3>
        {% if project.tech %}
        <p class="post-card-date">{{ project.tech }}</p>
        {% endif %}
        <p class="post-card-excerpt">{{ project.description }}</p>
      </div>
      {% endfor %}
    </div>
  {% else %}
    <div class="coming-soon">
      <div class="coming-soon-icon">⚙</div>
      <h2>Coming Soon</h2>
      <p>I'm working on some projects — check back later. Or refresh the page, maybe they're here now.</p>
    </div>
  {% endif %}
</div>
