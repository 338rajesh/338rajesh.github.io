---
layout: page
permalink: /publications/
title: research
description: 
years: [2023, 2022]
nav: true
nav_order: 1
---

***Will update on my current state of research and future directions.***

<!-- _pages/publications.md -->
<div class="publications">

{%- for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f {{ site.scholar.bibliography }} -q @*[year={{y}}]* %}
{% endfor %}

</div>
