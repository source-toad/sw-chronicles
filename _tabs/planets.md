---
layout: page
title: Planets
icon: fas fa-globe
order: 2
permalink: /planets/
---

{% assign sorted = site.pages | where:"collection","planets" | sort: "title" %}

{% if sorted.size > 0 %}
<div class="grid gap-6 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4">
  {% for planet in sorted %}
  <a href="{{ planet.url | relative_url }}" class="group block rounded-lg border border-gray-200 dark:border-gray-700 p-4 hover:shadow-lg transition-shadow duration-200">
    <div class="flex items-center justify-center mb-3 h-24 bg-gray-100 dark:bg-gray-800 rounded">
      {% if planet.icon %}
        <i class="{{ planet.icon }} text-3xl text-gray-600 dark:text-gray-400"></i>
      {% else %}
        <i class="fas fa-globe text-3xl text-gray-600 dark:text-gray-400"></i>
      {% endif %}
    </div>
    <h3 class="text-lg font-semibold group-hover:text-blue-500 dark:group-hover:text-blue-400">{{ planet.title }}</h3>
    {% if planet.description %}
    <p class="text-sm text-gray-500 dark:text-gray-400 mt-1">{{ planet.description | truncate: 60 }}</p>
    {% endif %}
  </a>
  {% endfor %}
</div>
{% else %}
<p class="text-gray-600 dark:text-gray-400">_No planets yet..._</p>
{% endif %}
