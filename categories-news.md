---
layout: default
title: "Новости проекта"
permalink: /categories/news/
author_profile: true
header:
  overlay_image: /assets/images/main-banner.jpg
  overlay_filter: 0.4
---

<div id="main" role="main">
  {% include sidebar.html %}

  <div class="page__inner-wrap">
    
    <p style="font-size: 16px; line-height: 1.6; margin-top: 0;">Самые свежие новости проекта, важные объявления, анонсы и события из мира аквариумистики.</p>
    <hr>

    {% assign news_posts = site.categories['news'] %}
    {% for post in news_posts %}
      <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
      <p style="font-size: 14px; color: #888; margin-top: -10px;"><i>Дата публикации: {{ post.date | date: "%d.%m.%Y" }}</i></p>

      <p>{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
      
      <p><a href="{{ post.url | relative_url }}" class="btn btn--info">Читать далее...</a></p>
      
      {% unless forloop.last %}
        <hr>
      {% endunless %}
    {% endfor %}

  </div>
</div>
