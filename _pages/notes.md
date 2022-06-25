---
layout: page
permalink: /categories/notes
categories: Notes
title: Notes
---

<div id="archives">
<h2>Most Recent Posts</h2>
{% assign categories = page.categories | join: "-" %}
{% for post in site.posts %}
  {% assign postCategories = post.categories | join: "-" %}
  {% if categories == postCategories %}
    <article class="archive-item">
      <h4><a href="{{ site.baseurl }}{{ post.url }}">{% if post.title and post.title != "" %}{{post.title}}{% else %}{{post.excerpt |strip_html}}{%endif%}</a></h4>
    </article>
  {% endif %}
{% endfor %}
</div>
