---
layout: hidden
permalink: /by_category
---
# Projects
{% assign mydocs = site.projects | group_by: 'category' | sort: "category" %}
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

----

# Posts

{% assign mydocs = site.articles | group_by: 'category' | sort: "category" %}
{% for cat in mydocs %}
<h3>{{ cat.name }}</h3>
  <ul>
      {% assign items = cat.items | sort: 'date' | reverse %}
      {% for item in items %}
        <li><a href="{{ item.url }}">{{ item.title }}</a></li>
      {% endfor %}
  </ul>
{% endfor %}
