---
layout: article
title: "Austin.com"
category: writing
subcategory: articles
tags: [Austin, TX, restaurants, movies, plays, reviews, criticism]
image:
  feature: austin-feature.jpg
  teaser: austin-teaser.jpg
  credit: Austin, TX Skyline by Mike Boening Photography
  creditlink: https://flic.kr/p/qoh9yH
excerpt: "In 2013, I wrote a series of freelance articles and reviews for locally-focused site Austin.com."
---

In 2013, I wrote a series of freelance articles and reviews for locally-focused site [Austin.com](http://www.austin.com):

{% assign portfolio = site.portfolio | where: "category", "writing" | sort: "date" %}

<ul>
{% for post in portfolio %}
{% if post.subcategory == 'austin.com' %}
<li><a href="{{ site.url }}{{ post.url }}">{{ post.title }}</a> – <span class="archive-excerpt">{{ post.excerpt | strip_html }}</span>{% if post.date %} – <span class="archive-meta">{{ post.date | date: "%B %d, %Y" }}</span>{% endif %}</li>
{% endif %}
{% endfor %}
</ul>