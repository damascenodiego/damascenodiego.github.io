---
layout: page
permalink: /talks/
title: talks
description: Information on talks I presented.
nav: false
display_categories: [talks]
years: [2021]
horizontal: false
---
<div class="projects">
  {% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized talks -->
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

{% endif %}

</div>
