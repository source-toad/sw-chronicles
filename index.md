---
layout: page
title: Home
icon: fas fa-old-republic
order: 1
---

{% include lang.html %}

<div class="container py-4">

  <!-- Hero / Title Section -->
  <div class="text-center mb-5">
    <h1 class="display-4"><i class="fas fa-old-republic me-2"></i>{{ page.title }}</h1>
    <p class="lead fst-italic">Explore the Star Wars Chronicles - Lore, Systems, Planets, and more.</p>
  </div>

  <!-- Collections Grid -->
  <div class="row g-4">

    {% assign collections_list = "lore,planets,systems,characters" | split: "," %}
    {% for collection_name in collections_list %}
      {% assign collection_pages = site.pages | where: "collection", collection_name | sort: "title" %}

      {% if collection_pages.size > 0 %}
      <div class="col-md-6 col-lg-3">
        <div class="card h-100 shadow-sm">
          <div class="card-body d-flex flex-column">
            <div class="mb-3 text-center">
              {% assign default_icon = "fas fa-book" %}
              {% if collection_name == "planets" %}
                {% assign default_icon = "fas fa-globe" %}
              {% elsif collection_name == "systems" %}
                {% assign default_icon = "fas fa-star" %}
              {% elsif collection_name == "characters" %}
                {% assign default_icon = "fas fa-user-astronaut" %}
              {% endif %}

              <i class="{{ default_icon }} fa-3x text-primary"></i>
            </div>
            <h5 class="card-title text-center">{{ collection_name | capitalize }}</h5>
            <p class="card-text text-center text-muted">
              {{ collection_pages.size }} {{ collection_name | replace: "_", " " }}
            </p>
            <a href="{{ '/' | append: collection_name | append: '/' | relative_url }}" class="btn btn-outline-primary mt-auto">Explore</a>
          </div>
        </div>
      </div>
      {% endif %}

    {% endfor %}
  </div>

</div>
