---
layout: archive #single
title: "Teaching"
permalink: /teaching/
author_profile: true
header:
  image: /images/header.jpg
---

{% include base_path %}

{% for post in site.teaching reversed %}
  {% include archive-single.html %}
{% endfor %}
