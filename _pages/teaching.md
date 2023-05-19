---
layout: page
permalink: /teaching/
title: teaching
description: Materials for courses taught.
nav: false
display_categories: [teaching]
years: [Radboud, USP, UFPa]
horizontal: false
---
<div class="projects">
  {% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
    {% for category in page.display_categories %}
        {% for year in page.years %}
          <h2 class="year">{{year}}</h2>
          {% assign categorized_projects = site.projects | where: "category", category | where: "year", year %}
          {% assign sorted_projects = categorized_projects | sort: "importance" | reverse %}
          <!-- Generate cards for each project -->
          {% if page.horizontal %}
            <div class="container">
              <div class="row row-cols-2">
              {% for project in sorted_projects %}
                {% include projects_horizontal.html %}
              {% endfor %}
              </div>
            </div>
          {% else %}
            <div class="grid">
              {% for project in sorted_projects %}
                {% include projects.html %}
              {% endfor %}
            </div>
          {% endif %}
        {% endfor %}
    {% endfor %}

{% else %}
  <!-- Display projects without categories -->
    {% assign sorted_projects = site.projects | sort: "importance" %}
    <!-- Generate cards for each project -->
    {% if page.horizontal %}
      <div class="container">
        <div class="row row-cols-2">
        {% for project in sorted_projects %}
          {% include projects_horizontal.html %}
        {% endfor %}
        </div>
      </div>
    {% else %}
      <div class="grid">
        {% for project in sorted_projects %}
          {% include projects.html %}
        {% endfor %}
      </div>
    {% endif %}

{% endif %}

</div>
