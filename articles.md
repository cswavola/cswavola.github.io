---
layout: default
title: Posts and Articles
menu: main
links_as: buttons
---
###### [View content by category][cat_page]
<h1>Posts and Articles</h1>
<ul>
    {% assign sorted = site.articles | sort: 'date' | reverse %}
    {% for item in sorted %}
    {{ item.date | date: "%b %d, %y" }}
    <h2><a href="{{ item.url | prepend: site.baseurl }}">{{ item.title }}</a></h2>
    <p class="post-excerpt">{{ item.description | truncate: 160 }}</p>
    <br>
    {% endfor %}
</ul>


[cat_page]: /by_category
