---
layout: default
title: Portfolio
by_language: false
---

<br>
<h1>Projects</h1>
##### [View all projects][project]
<ul>
    {% assign sorted = site.projects | sort: 'date' | reverse %}
    {% for item in sorted limit:3 %}
    <!-- {{ item.date | date: "%B %Y" }} -->
    <h2><a href="{{ item.url | prepend: site.baseurl }}">{{ item.title }}</a></h2>
    <p class="post-excerpt" style="margin-left: 5%">{{ item.description | truncate: 160 }}</p>
    <br>
    {% endfor %}
</ul>

<br>

----
<br>
<h1>Essays and Articles</h1>
##### [View all posts][posts]
<ul>
    {% assign sorted = site.articles | sort: 'date' | reverse %}
    {% for item in sorted limit:3 %}
    <!-- {{ item.date | date: "%B %Y" }} -->
    <h2><a href="{{ item.url | prepend: site.baseurl }}">{{ item.title }}</a></h2>
    <p class="post-excerpt" style="margin-left: 5%">{{ item.description | truncate: 160 }}</p>
    <br>
    {% endfor %}
</ul>

[project]:/projects
[posts]:/articles
