---
title: Projects
subtitle: Some of my projects
layout: "page"
icon: fa-lightbulb
order: 3
---

Here are some of my projects.
source: [The Guardian](https://www.theguardian.com/books/booksblog/2011/jan/04/best-boring-books)


{% for tag in site.tags %}
  <h3>{{ tag[0] }}</h3>
  <ul>
    {% for post in tag[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
