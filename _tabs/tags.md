---
layout: page
title: Tags
permalink: /tags/
---

<div id="tags" class="d-flex flex-wrap mx-xl-2">
  {% assign all_tags = "" | split: "" %}

  {% comment %}
  Loop over all pages and collect tags
  {% endcomment %}
  {% for p in site.pages %}
    {% if p.tags %}
      {% for t in p.tags %}
        {% unless all_tags contains t %}
          {% assign all_tags = all_tags | push: t %}
        {% endunless %}
      {% endfor %}
    {% endif %}
  {% endfor %}

  {% assign sorted_tags = all_tags | sort_natural %}

  {% for t in sorted_tags %}
    <div>
      <a class="tag" href="{{ '/tags/' | append: t | relative_url }}">
        {{ t }}
        <span class="text-muted">
          {% assign count = 0 %}
          {% for p in site.pages %}
            {% if p.tags contains t %}
              {% assign count = count | plus: 1 %}
            {% endif %}
          {% endfor %}
          {{ count }}
        </span>
      </a>
    </div>
  {% endfor %}
</div>
