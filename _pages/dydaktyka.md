---
layout: archive #single
title: "Dydaktyka"
lang: pl
ref: teaching

permalink: /dydaktyka/
author_profile: true
header:
  image: /images/header.jpg
---
{% assign posts=site.teaching | where:"lang", page.lang %}

{% for post in posts reversed %}
  {% include archive-single.html %}
{% endfor %}
