---
title: "Articles"
layout: post
permalink: /articles
hide_newsletter: false
---

Want to receive these articles directly in your inbox? Subscribe to the newsletter!


<ul class="article-list">
  {% capture now %}{{'now' | date: '%s' | plus: 0 %}}{% endcapture %}
  {% for post in site.posts %}
    {% capture date %}{{post.date | date: '%s' | plus: 0 %}}{% endcapture %}
    {% if date <= now %}
    <li class="article-item">
      <time class="article-date" datetime="{{ post.date | date_to_xmlschema }}" itemprop="datePublished">{{ post.date | date: "%b %-d, %Y" }}</time>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
    {% endif %}
  {% endfor %}
</ul>
