---
layout: single
title: "Новости"
permalink: /categories/news/
author_profile: true
---

Самые свежие новости проекта, важные объявления, анонсы и события из мира аквариумистики.

---

{% assign category_posts = site.categories['news'] %}
{% for post in category_posts %}
  <div class="list__item" style="background-color: #ffffff !important; padding: 25px !important; border-radius: 6px !important; margin-bottom: 20px !important; box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05) !important;">
    <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
    <p style="font-size: 14px; color: #888; margin-top: -10px;"><i>Дата публикации: {{ post.date | date: "%d.%m.%Y" }}</i></p>

    <p style="color: #222222 !important;">{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
    
    <p><a href="{{ post.url | relative_url }}" class="btn btn--info">Читать далее...</a></p>
  </div>
{% endfor %}
