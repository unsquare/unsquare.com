---
layout: archive
permalink: /blog/web/
title: "Web Design"
---

{% assign web = site.posts | where: "subcategory", "web" %}

<div class="tiles">
{% for post in web %}
  {% include post-grid.html %}
{% endfor %}
</div><!-- /.tiles -->