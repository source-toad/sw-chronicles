---
layout: page
title: Planets
icon: fas fa-globe
order: 2
permalink: /planets/
---

## Planets

{% assign sorted = site.planets | sort: "title" %}
{% for planet in sorted %}
- [{{ planet.title }}]({{ planet.url | relative_url }})
{% endfor %}
