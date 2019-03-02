---
layout: default
title: Tags
---

{% for tag in site.tags %}
  <h2 class='tag-header' id="{{ tag[0] }}">{{ tag[0] }}</h2>
  <ul>
    {% assign pages_list = tag[1] %}
    {% assign author = site.authors | where: 'short_name', page.author | first %}

    {% for node in pages_list %}
      {% if node.title != null %}
        {% if group == null or group == node.group %}
          {% if page.url == node.url %}
          <li class="active"><a href="{{ site.baseurl }}{{ node.url }}" class="active">{{ node.title }}</a></li>
          {% else %}
          <li><a href="{{ site.baseurl }}{{ node.url }}">{{node.title}} - {{ node.author }}</a></li>
          {% endif %}
        {% endif %}
      {% endif %}
    {% endfor %}

    {% assign pages_list = nil %}
    {% assign group = nil %}
  </ul>
{% endfor %}