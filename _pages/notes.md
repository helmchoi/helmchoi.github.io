---
title: "Notes"
layout: archive
permalink: categories/notes
author_profile: true
---


{% assign posts = site.categories.Cpp %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
