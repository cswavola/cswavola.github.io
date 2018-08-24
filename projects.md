---
layout: default
title: Projects
---

{% for projects in site.projects %}


<h1><a href="{{ projects.url | prepend: site.baseurl }}">{{ projects.title }}</a></h1>

<p class="post-excerpt">{{ projects.description | truncate: 160 }}</p>

{% endfor %}      
