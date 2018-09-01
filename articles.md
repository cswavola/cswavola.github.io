---
layout: default
menu: main
links_as: false
by_language: false
permalink: /articles
---
<h2>Posts and Articles</h2>

<ul>
    {% assign sorted = site.articles | sort: 'date' | reverse %}
    {% for item in sorted %}
    {{ item.date | date: "%b %d, %y" }}
    <h2><a href="{{ item.url | prepend: site.baseurl }}">{{ item.title }}</a></h2>
    <p class="post-excerpt" style="margin-left: 5%">{{ item.description | truncate: 160 }}</p>
    <br>
    {% endfor %}
</ul>


[cat_page]: /by_category
