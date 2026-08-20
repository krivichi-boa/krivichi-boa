---
layout: single
title: "Мои аквариумы"
permalink: /categories/my-tanks/
author_profile: true
---

В этом разделе собраны все хроники, обзоры оборудования и дневники запусков моих личных аквариумов.

---

{% assign category_posts = site.categories['my-tanks'] %}
{% for post in category_posts %}
  ### [{% if post.title %}{{ post.title }}{% else %}{{ post.id }}{% endif %}]({{ post.url | relative_url }})
  *Дата публикации: {{ post.date | date: "%d.%m.%Y" }}*

  {% if post.excerpt %}
    {{ post.excerpt | strip_html | truncatewords: 30 }}
  {% endif %}
  
  [Читать далее... ]({{ post.url | relative_url }})
  
  ---
{% endfor %}
