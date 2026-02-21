---
layout: page
title: פורומים - קטגוריות הבלוג
permalink: /categories/
---

להלן רשימת הקטגוריות המרכזיות בבלוג. כנסו לכל קטגוריה כדי לצפות במאמרים הרלוונטיים:

<div class="categories-grid">
  {% for category in site.data.categories %}
  <a href="{{ site.baseurl }}/category/{{ category.name }}" class="category-card" style="border-top: 4px solid {{ category.color }};">
    <div class="category-icon">{{ category.icon }}</div>
    <div class="category-info">
      <h3>{{ category.title }}</h3>
      <p>{{ category.description }}</p>
    </div>
  </a>
  {% endfor %}
</div>

<style>
.categories-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 20px;
  margin-top: 2rem;
}

.category-card {
  display: flex;
  align-items: center;
  padding: 1.5rem;
  background: var(--surface-color, #1e1e1e);
  border-radius: 8px;
  text-decoration: none;
  color: var(--text-color, #e0e0e0);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
}

.category-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 15px rgba(0,0,0,0.2);
}

.category-icon {
  font-size: 2.5rem;
  margin-left: 1rem; /* RTL padding */
}

.category-info h3 {
  margin: 0 0 0.5rem 0;
  font-size: 1.25rem;
  color: var(--heading-color, #ffffff);
}

.category-info p {
  margin: 0;
  font-size: 0.9rem;
  opacity: 0.8;
  line-height: 1.4;
}
</style>
