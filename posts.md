---
layout: default
homepage: false
title: All My Posts
description: Here is a list of all of the posts to this site
---
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
