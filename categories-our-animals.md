---
layout: single
title: "Наши животные"
permalink: /categories/our-animals/
author_profile: true
---

В этом разделе собраны подробные обзоры, фотографии и истории о живых обитателях наших аквариумов и домашних любимцах.

---

{% assign category_posts = site.categories['our-animals'] %}
{% for post in category_posts %}
  <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
  <p style="font-size: 14px; color: #888; margin-top: -10px;"><i>Дата публикации: {{ post.date | date: "%d.%m.%Y" }}</i></p>

  <p>{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
  
  <p><a href="{{ post.url | relative_url }}" class="btn btn--info">Читать далее...</a></p>
  <hr>
{% endfor %}

