---
layout: default
title: Posts and Articles
---

{% for articles in site.articles %}


<h1><a href="{{ articles.url | prepend: site.baseurl }}">{{ articles.title }}</a></h1>

<p class="post-excerpt">{{ articles.description | truncate: 160 }}</p>

{% endfor %}      
