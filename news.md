---
title: News
description: Lab updates, papers, positions, and announcements.
permalink: /news/
hide_title: true
---

<div class="container content-page">
  <h1 class="plain-page-title">News</h1>

  <div class="news-list">
{% for post in site.posts %}
  <article class="news-item">
    <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %-d, %Y" }}</time>
    {% if post.external_url %}
    <h2><a href="{{ post.external_url }}">{{ post.title }}</a></h2>
    {% else %}
    <h2>{{ post.title }}</h2>
    {% endif %}
    <div class="news-content">
      {{ post.content }}
    </div>
  </article>
{% endfor %}
  </div>
</div>
