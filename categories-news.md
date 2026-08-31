---
layout: default
title: "Новости"
permalink: /categories/news/
author_profile: true
---

<div class="inner" style="margin: 20px 0;">
  <p>Самые свежие новости проекта, важные объявления, анонсы и события из мира аквариумистики.</p>
  <hr style="border: 1px solid #eee; margin: 20px 0;">

  {% assign category_posts = site.categories['news'] %}
  {% for post in category_posts %}
    <div class="list__item" style="background-color: #ffffff !important; padding: 25px !important; border-radius: 8px !important; margin-bottom: 25px !important; box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08) !important; color: #222222 !important;">
      <h2 style="margin-top: 0;"><a href="{{ post.url | relative_url }}" style="color: #00bcd4 !important; text-decoration: none;">{{ post.title }}</a></h2>
      <p style="font-size: 14px; color: #888; margin-top: -10px;"><i>Дата публикации: {{ post.date | date: "%d.%m.%Y" }}</i></p>
      
      <p style="color: #333333 !important; font-size: 16px; line-height: 1.6;">{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
      
      <p style="margin-bottom: 0;"><a href="{{ post.url | relative_url }}" class="btn btn--info" style="border-radius: 4px;">Читать далее...</a></p>
      <p style="margin-bottom: 0;"><a href="{{ post.url | relative_url }}" class="btn btn--info" style="border-radius: 4px;">Читать далее...</a></p>
    </div>
  {% endfor %}
</div>
