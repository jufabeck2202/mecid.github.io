---
layout: page
permalink: /archive/
title: Archive
---


<div id="archives">
{% for category in site.categories %}
  <div class="archive-group">
    {% capture category_name %}{{ category | first }}{% endcapture %}
    <div id="#{{ category_name | slugize }}"></div>
    <p></p>

    <h3 class="category-head">{{ category_name }}</h3>
    <a name="{{ category_name | slugize }}"></a>
    {% for post in site.categories[category_name] %}
    <article class="archive-item">
      <h4><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a></h4>
    </article>
    {% endfor %}
  </div>
{% endfor %}
</div>
<hr>
<article class="page">
  <div class="entry">
    
    {% assign previousYear = "" %}
    {% for post in site.posts %}
      {% capture currentYear %}
        {{ post.date | date: "%Y" }}
      {% endcapture %}
    
      {% if currentYear != previousYear %}
        {% assign previousYear = currentYear %}
        <h3>{{ currentYear }}</h3>
      {% endif %}
    
      {{ post.date | date: '%B %d, %Y' }} - <a style="font-weight: bold" href="{{ post.url }}">{{ post.title }}</a>
      <br />
    {% endfor %}    
  </div>
</article>