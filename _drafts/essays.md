---
layout: archive #single
permalink: /essays/
author_profile: true
header:
  image: /images/header.jpg
---

{% include base_path %}

{% for post in site.posts %}
  {% include archive-single.html %}
{% endfor %}
