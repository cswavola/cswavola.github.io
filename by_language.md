---
layout: hidden
permalink: /by_language
---

<br>
# Projects by Language
{% assign myposts = site.articles %}
{% assign lang2 = site.projects |  group_by: 'language2' | sort: "language2" | reverse %}
{% assign mydocs = site.projects | concat:myposts | group_by: 'language' | sort: "language" | reverse %}
{% for cat in mydocs %}
{% if cat.name != 'false' %}
<h3>{{ cat.name }}</h3>
  <ul>
      {% assign items = cat.items | sort: 'date' | reverse %}
      {% for item in site.projects %}
      {% if item.language2 == cat.name %}
        <li><a href="{{ item.url }}">{{ item.title }}</a>
        </li>
      {% endif %}
      {% endfor %}
      {% for item in items %}
        <li><a href="{{ item.url }}">{{ item.title }}</a>
        {% if item.layout == 'post'%} <sup>(article)</sup>
        {% endif %}
        </li>
      {% endfor %}
  </ul>
  {% endif %}
{% endfor %}

<br>
