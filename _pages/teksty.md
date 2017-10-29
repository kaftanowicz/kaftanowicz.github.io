---
layout: archive #single
title: "Teksty"
lang: pl
ref: writings

permalink: /teksty/
author_profile: true
header:
  image: /images/header.jpg
---

Teksty, które napisałem po polsku lub przetłumaczyłem na polski, posortowane kategoriami. 

{% assign forbidden_categories = 'Translations' %}

{% include group-by-array collection=site.posts field="categories" %}

{% for category in group_names %}
  {% assign posts = group_items[forloop.index0] | where:"lang", page.lang %}
{% unless posts.size == 0 %}
  <h1 id="{{ category | slugify }}" class="archive__subtitle">{{ category }}</h1>
  {% for post in posts %}
    		{% include archive-single.html %}
  {% endfor %}
{% endunless %}
{% endfor %}

