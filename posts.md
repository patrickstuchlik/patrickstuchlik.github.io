---
layout: default
homepage: false
title: All My Posts
description: Here is a list of all of the posts to this site
---
<ul>
  {% for post in site.posts %}
    <li>
      <ul style="list-style: none;"><li><a href="{{ post.url }}">{{ post.title }}</a></li>
	  <li>{{ post.description }}</li></ul><br>
    </li>
  {% endfor %}
</ul>
