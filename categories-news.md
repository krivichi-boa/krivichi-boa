---
layout: default
title: "Новости проекта"
permalink: /categories/news/
author_profile: true
header:
  overlay_image: /assets/images/main-banner.jpg
  overlay_filter: 0.4
---

<div style="margin: 20px 0; color: #222222 !important;">
  <p style="font-size: 16px; line-height: 1.6;">Самые свежие новости проекта, важные объявления, анонсы и события из мира аквариумистики.</p>
  <hr style="border: 0; height: 1px; background: #eee; margin: 20px 0;">

  <!-- ХИТРЫЙ ВЫВОД ЛЕНТЫ НОВОСТЕЙ КАРТОЧКАМИ -->
  {% assign news_posts = site.categories['news'] %}
  {% for post in news_posts %}
    <div style="background-color: #ffffff !important; padding: 30px !important; border-radius: 8px !important; margin-bottom: 25px !important; box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1) !important; display: block !important; visibility: visible !important;">
      <h2 style="margin-top: 0; margin-bottom: 10px;"><a href="{{ post.url | relative_url }}" style="color: #00bcd4 !important; text-decoration: none; font-weight: bold;">{{ post.title }}</a></h2>
      <p style="font-size: 13px; color: #888; margin-top: 0; margin-bottom: 15px;"><i>Дата публикации: {{ post.date | date: "%d.%m.%Y" }}</i></p>
      
      <p style="color: #333333 !important; font-size: 15px; line-height: 1.6; margin-bottom: 20px;">{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
      
      <p style="margin: 0;"><a href="{{ post.url | relative_url }}" class="btn btn--info" style="border-radius: 4px; padding: 10px 20px; font-weight: bold; text-decoration: none;">Читать далее...</a></p>
    </div>
  {% endfor %}
</div>
