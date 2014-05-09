---
layout: page
title: Dr. Henry
tagline: A new effort at a GitHub-friendly blog platform for Jekyll
---
{% include JB/setup %}

## Dr. Henry

This is a derivation of [jekyll-bootstrap](http://jekyllbootstrap.com/), about to undergo a lot of changes, and not suitable for anyone (yet).

Check out the [repository](https://github.com/jhohertz/dr-henry)

### Posts

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

