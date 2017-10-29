---
layout: archive #single
title: "Przekłady"
lang: pl
ref: translations

permalink: /przeklady/
author_profile: true
header:
  image: /images/header.jpg
---

Teksty, które przetłumaczyłem na polski, posortowane kategoriami. 

{% include group-by-array collection=site.posts field="categories" %}

{% for category in group_names %}
  {% assign posts = group_items[forloop.index0] | where:"lang", page.lang | where:"translated", true %}
{% unless posts.size == 0 %}
  <h1 id="{{ category | slugify }}" class="archive__subtitle">{{ category }}</h1>
  {% for post in posts %}
    		{% include archive-single.html %}
  {% endfor %}
{% endunless %}
{% endfor %}

