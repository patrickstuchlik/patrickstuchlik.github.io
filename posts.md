---
layout: default
homepage: false
title: Posts
description: What interests me and what I am working on (more to come soon!)
---
<ul>
  {% for post in site.posts %}
    <li>
      <ul style="list-style: none;"><li><a href="{{ post.url }}">{{ post.title }}</a></li>
	  <li>{{ post.description }}</li></ul><br>
    </li>
  {% endfor %}
</ul>
