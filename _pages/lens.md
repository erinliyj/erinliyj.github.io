---
layout: archive
author_profile: true
title: "Lens"
excerpt: "A New Look of Data"
image:
  feature: pen.jpg
id: home
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/computer-cats.jpg
---

<div class="tiles">
{% for post in site.categories.lens %}
  {% include post-grid.html %}
{% endfor %}
</div><!-- /.tiles -->