---
title: Tags and Categories
subtitle: List of all blog tags and categories
layout: "page"
icon: fa-tags
order: 3
---
<hr>
<h3>Categories:</h3>
{% for category in site.categories %}
  <p>
  <h4>{{ category[0] }}</h4>
  <ul >
    {% for post in category[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
</p>
<hr>
<h3>Tags:</h3>
{% for tag in site.tags %}
  <p>
  <h4>{{ tag[0] }}</h4>
  <ul>
    {% for post in tag[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
</p>

