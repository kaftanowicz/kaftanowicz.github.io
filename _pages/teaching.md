---
layout: archive #single
title: "Teaching"
lang: en
ref: teaching

permalink: /teaching/
author_profile: true
header:
  image: /images/header.jpg
---
{% include base_path %}

{% assign posts=site.teaching | where:"lang", page.lang %}

{% for post in posts reversed %}
  {% include archive-single.html %}
{% endfor %}
