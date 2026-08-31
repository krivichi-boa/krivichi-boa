---
layout: single
title: "Новости проекта"
permalink: /categories/news-list/
author_profile: true
header:
  overlay_image: /assets/images/main-banner.jpg
  overlay_filter: 0.4
---

Самые свежие новости проекта, важные объявления, анонсы и события из мира аквариумистики.

---

{% assign news_posts = site.categories['news'] %}
{% for post in news_posts %}
  <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
  <p style="font-size: 14px; color: #888; margin-top: -10px;"><i>Дата публикации: {{ post.date | date: "%d.%m.%Y" }}</i></p>

  <p>{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
  
  <p><a href="{{ post.url | relative_url }}" class="btn btn--info">Читать далее...</a></p>
  <hr>
{% endfor %}
