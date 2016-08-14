---
layout: archive
permalink: /writing/fiction/
title: "Fiction"
---

{% assign portfolio = site.portfolio | where: "subcategory", "fiction" | sort: "title" %}

<div class="tiles">
{% for post in portfolio %}
   {% include post-grid.html %}
{% endfor %}
</div><!-- /.tiles -->