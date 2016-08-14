---
layout: archive
permalink: /archive/
title: "Archive"
---

<div class="list">
{% for post in site.posts %}
  {% assign currentyear = post.date | date: "%Y" %}
  {% if currentyear != year %}
	{% unless forloop.first %}</p>{% endunless %}
	<h3 id="y{{post.date | date: "%Y"}}">{{ currentyear }}</h3>
	<p>
	{% assign year = currentyear %}
  {% endif %}
  	{% assign page = post %}
	{% include archive-list.html %}
  {% if forloop.last %}</p>{% endif %}
{% endfor %}
</div>