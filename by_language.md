---
layout: hidden
permalink: /by_language
---
<br>
# Projects by Language
{% assign mydocs = site.projects | group_by: 'language' | sort: "language" | reverse %}
{% for cat in mydocs %}
<h3>{{ cat.name }}</h3>
  <ul>
      {% assign items = cat.items | sort: 'date' | reverse %}
      {% for item in items %}
        <li><a href="{{ item.url }}">{{ item.title }}</a></li>
      {% endfor %}
  </ul>
{% endfor %}

<br>
