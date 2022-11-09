---
title: "Articles"
layout: post
permalink: /articles
hide_newsletter: false
---

    <div class="container">
        <div class="row align-items-center justify-content-center">
            <div class="col-lg-8">
                <div class="center-heading mb-60">
                    <h3 class="heading-title">Articles</h3>
                    (see the full list at <a href="/articles">the articles page</a>)
                </div>
            </div>
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
    </div>