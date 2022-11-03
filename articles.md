---
title: "Articles"
layout: post
permalink: /articles
hide_newsletter: false
---

<div class="row">
<h3 class="heading-title">Articles</h3>
</div>

<div class="row">
I am constantly posting new content on effective software testing. If you want to receive it in your inbox as soon as the post is out, subscribe to the newsletter!
</div>


<div class="row">

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

</div>

