---
layout: page
title: "תגיות"
permalink: /tags/
---

רשימת תגיות המסייעת לנווט בין כל הניצוצות.

{% if site.tags.size > 0 %}
<ul class="tag-list">
  {% for tag in site.tags %}
  <li>
    <h3 id="{{ tag[0] | slugify }}">{{ tag[0] }}</h3>
    <ul>
      {% for post in tag[1] %}
      <li>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        <span class="post-date">{{ post.date | date: "%d.%m.%Y" }}</span>
      </li>
      {% endfor %}
    </ul>
  </li>
  {% endfor %}
</ul>
{% else %}
אין עדיין תגיות. חזרו בקרוב!
{% endif %}

