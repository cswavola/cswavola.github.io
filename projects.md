---
layout: default
links_as: false
by_language: true
permalink: /projects
---
<h1>Projects</h1>

<ul>
    {% assign sorted = site.projects | sort: 'date' | reverse %}
    {% for item in sorted %}
    <!-- {{ item.date | date: "%B %Y" }} -->
    <h2><a href="{{ item.url | prepend: site.baseurl }}">{{ item.title }}</a></h2>
    <p class="post-excerpt" style="margin-left: 5%">{{ item.description | truncate: 160 }}</p>
    <br>
    {% endfor %}
</ul>

{%comment%}
{% for projects in site.projects %}


<h1><a href="{{ projects.url | prepend: site.baseurl }}">{{ projects.title }}</a></h1>

<p class="post-excerpt">{{ projects.description | truncate: 160 }}</p>

{% endfor %}      
{%endcomment%}


[cat_page]: /by_category
[lang_page]: /by_language
