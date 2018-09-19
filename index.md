---

layout: page
credit: icon
header-img: /assets/images/no_text.png
---
<h2-cheesy>Hello World!</h2-cheesy>
I'm a Data Scientist born from the Engineering world, so the only thing that outweighs my desire to _make it work_ is to make it work **right**. To me, that means ensuring that data provides fair and accurate representation- not cutting corners just to find "an answer," and that people fully understand the outcomes from sharing and using their data. Sometimes that means engaging my inner chemist and diving down to the fundamental mechanics of a problem. Sometimes it brings out the teammate in me to get everyone on the same page. Always, I get to learn something new. That last part is what got me into Data Science; the first part is what keeps me going.  <br><br>

On this site you'll find recent samples from my portfolio, my <a href="{{site.baseurl}}/assets/CSwavola.Resume.pdf">resume</a>, and a bit more about me.
<br><br>

<h2  align="center">Skills and Specialties</h2><br>
![Services]({{ site.baseurl }}/assets/images/services.svg)

<br><br>

<hr class="style-four"><br>
<h2  align="center">Featured Content</h2><br>

<ul>
    {% assign posts = site.articles %}
    {% assign projects = site.projects %}
    {% assign sorted = projects | concat:posts | sort: 'rank' | reverse %}
    {% for item in sorted limit:3 %}
    <!-- {{ item.date | date: "%B %Y" }} -->
    <h2 align="center" ><a href="{{ item.url | prepend: site.baseurl }}">{{ item.title }}</a></h2>
        <h4  align="center">{{ item.description }}</h4>
        <a style="margin-left:45%" href="/by_category" class="category_button"> {{item.category}} </a>
        {% assign content = item.excerpt | split: '</div>' %}
    {{ content[1] }}
    <!-- <p  style="margin-left: 10%">{{ item.excerpt }}</p> -->
    {% if item.image %}
    <img src="{{ site.baseurl }}/{{ item.image }}">
    {% endif %}

    <h4  align="center"><a href="{{ item.url | prepend: site.baseurl }}">Read Full Post</a></h4>
    <br>
    <hr class="style-four">
    <br>
    {% endfor %}
</ul>
