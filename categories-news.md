---
layout: default
title: "Новости проекта"
permalink: /categories/news-list/
author_profile: true
header:
  overlay_image: /assets/images/main-banner.jpg
  overlay_filter: 0.4
---

<!-- Создаем один общий белый лист во всю ширину, как у layout: single -->
<div class="page__inner-wrap" style="background-color: #ffffff !important; padding: 30px !important; border-radius: 8px !important; box-shadow: 0 4px 15px rgba(0,0,0,0.05) !important; color: #222222 !important; margin-top: 20px !important;">

  <p>Самые свежие новости проекта, важные объявления, анонсы и события из мира аквариумистики.</p>
  <hr style="border: 0; height: 1px; background: #eee; margin: 20px 0;">

  {% assign news_posts = site.categories['news'] %}
  {% for post in news_posts %}
    <h2><a href="{{ post.url | relative_url }}" style="color: #00bcd4 !important; text-decoration: none; font-weight: bold;">{{ post.title }}</a></h2>
    <p style="font-size: 14px; color: #888; margin-top: -10px;"><i>Дата публикации: {{ post.date | date: "%d.%m.%Y" }}</i></p>

    <p style="color: #333333 !important; font-size: 15px; line-height: 1.6;">{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
    
    <p><a href="{{ post.url | relative_url }}" class="btn btn--info" style="border-radius: 4px;">Читать далее...</a></p>
    
    <!-- Рисуем разделительную линию между новостями, кроме самой последней -->
    {% unless forloop.last %}
      <hr style="border: 0; height: 1px; background: #eee; margin: 30px 0;">
    {% endunless %}
  {% endfor %}

</div>
