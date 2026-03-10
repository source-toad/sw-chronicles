---
layout: page
title: Planets
icon: fas fa-globe
order: 2
permalink: /planets/
---

{% assign sorted = site.pages | where:"collection","planets" | sort: "title" %}
{% for planet in sorted %}
- [{{ planet.title }}]({{ planet.url | relative_url }})
{% endfor %}
