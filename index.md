---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page

---
<h1>Welcome!</h1>
I'm a Data Scientist born from the Engineering world, so the only thing that outweighs my desire to _make it work_ is to make it work **right**. To me, that means ensuring that data provides fair and accurate representation- not cutting corners just to find "an answer," and that people fully understand the outcomes from sharing and using their data. Sometimes this means engaging my inner chemist and diving down to the fundamental mechanics of a problem. Sometimes it brings out the teammate in me to get everyone on the same page. Always, I get to learn something new. That last part is what got me into Data Science; the first part is what keeps me going.  

On this site you'll find recent samples from my portfolio, my [resume]({{site.baseurl}}/assets/Cswavola.Resume.pdf), and a bit more about me.
<br><br>




<hr class="style-four">
<ul>
    {% assign posts = site.articles %}
    {% assign projects = site.projects %}
    {% assign sorted = projects | concat:posts | sort: 'date' | reverse %}
    {% for item in sorted limit:3 %}
    {{ item.date | date: "%B %Y" }}
    <h2 align="center" ><a href="{{ item.url | prepend: site.baseurl }}">{{ item.title }}</a></h2>
        <h4  align="center">{{ item.description }}</h4>
        <a style="margin-left:45%" href="/by_category" class="category_button"> {{item.category}} </a>
        {% assign content = item.excerpt | split: '</div>' %}
    {{ content[1] }}
    <!-- <p  style="margin-left: 10%">{{ item.excerpt }}</p> -->
    <img src="{{ site.baseurl }}{{ item.image }}">
    <h4  align="center"><a href="{{ item.url | prepend: site.baseurl }}">Read Full Post</a></h4>
    <br>
    <hr class="style-four">
    <br>
    {% endfor %}
</ul>
