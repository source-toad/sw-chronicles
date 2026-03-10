---
layout: page
title: Planets
icon: fas fa-globe
order: 2
permalink: /planets/
---

{% if site.planets.size > 0 %}
  {% assign sorted = site.planets | sort: "title" %}
  {% for planet in sorted %}
  - [{{ planet.title }}]({{ planet.url | relative_url }})
  {% endfor %}
{% else %}
_No planets yet_
{% endif %}
