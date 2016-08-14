---
layout: portfolio
permalink: /writing/
title: "Writing"
---

{::options parse_block_html="true" /}

<div class="sidebar-wrap" id="sidebar">

{% include toc.html %}

</div>

<div class="portfolio-wrap">

# {{ page.title }}
{:.no_toc}

I've been writing seriously since college, when I first took a playwriting course and experienced the joy of seeing my work produced on a stage.

In the years since then, I've tried my hand at a wide variety of mediums, including prose, scripts, essays, business communications and much, much more. I've included selections of my work below.

{% assign portfolio = site.portfolio | where: "category", "writing" | sort: "title" %}

## Web Series

<div class="tiles">
{% for post in portfolio %}
{% if post.subcategory == 'web series' %}
{% include portfolio-grid.html %}
{% endif %}
{% endfor %}
</div><!-- /.tiles -->

## Fiction

<div class="tiles">
{% for post in portfolio %}
{% if post.subcategory == 'fiction' %}
{% include portfolio-grid.html %}
{% endif %}
{% endfor %}
</div><!-- /.tiles -->

## Articles and Reviews

<div class="tiles">
{% for post in portfolio %}
{% if post.subcategory == 'articles' %}
{% include portfolio-grid.html %}
{% endif %}
{% endfor %}
</div><!-- /.tiles -->

## Tweet Collections

<div class="tiles">
{% for post in portfolio %}
{% if post.subcategory == 'twitter' %}
{% include portfolio-grid.html %}
{% endif %}
{% endfor %}
</div><!-- /.tiles -->

## Plays

<div class="tiles">
{% for post in portfolio %}
{% if post.subcategory == 'plays' %}
{% include portfolio-grid.html %}
{% endif %}
{% endfor %}
</div><!-- /.tiles -->

## SEO Content

<div class="tiles">
{% for post in portfolio %}
{% if post.subcategory == 'SEO Content' %}
{% include portfolio-grid.html %}
{% endif %}
{% endfor %}
</div><!-- /.tiles -->

</div>