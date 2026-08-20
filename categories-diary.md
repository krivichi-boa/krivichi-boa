---
layout: single
title: "Заметки и дневник"
permalink: /categories/diary/
author_profile: true
---

Повседневные наблюдения, мысли, эксперименты и небольшие заметки из жизни аквариумиста.

---

{% assign category_posts = site.categories['diary'] %}
{% for post in category_posts %}
  <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
  <p style="font-size: 14px; color: #888; margin-top: -10px;"><i>Дата публикации: {{ post.date | date: "%d.%m.%Y" }}</i></p>

  <p>{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
  
  <p><a href="{{ post.url | relative_url }}" class="btn btn--info">Читать далее...</a></p>
  <hr>
{% endfor %}
