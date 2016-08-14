---
layout: archive
permalink: /blog/craft/
title: "The Craft of Writing"
---

{% assign sub = site.posts | where: "subcategory", "craft" %}

<div class="tiles">
{% for post in sub %}
  {% include post-grid.html %}
{% endfor %}
</div><!-- /.tiles -->