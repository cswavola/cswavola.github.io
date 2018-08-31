---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page

---
<ul>
    {% assign posts = site.articles %}
    {% assign projects = site.projects %}
    {% assign sorted = projects | concat:posts | sort: 'date' | reverse %}
    {% for item in sorted limit:3 %}
    {{ item.date | date: "%B %Y" }}
    <h2 align="center" ><a href="{{ item.url | prepend: site.baseurl }}">{{ item.title }}</a></h2>
        <h4  align="center">{{ item.description }}</h4>
        <a style="text-align:center" href="/by_category" class="category_button"> {{item.category}} </a>
        <br><br>

    <p  style="margin-left: 10%">{{ item.excerpt }}</p>
    <h4  align="center"><a href="{{ item.url | prepend: site.baseurl }}">Read Full Post</a></h4>
    <br>
    <hr class="style-four">
    <br>
    {% endfor %}
</ul>
