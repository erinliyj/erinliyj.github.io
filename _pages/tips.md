---
layout: archive
author_profile: true
title: "Notes and Tips"
excerpt: "Tips for getting things done, fast"
image:
  feature: pen.jpg
id: home
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/running-dog.jpg
---

<div class="tiles">
{% for post in site.categories.tips %}
  {% include post-grid.html %}
{% endfor %}
</div><!-- /.tiles -->