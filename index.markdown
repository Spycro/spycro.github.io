---
title: Index
layout: default
---

<ul>
    {% for post in site.posts %}
        <li>
            <a href="{{ post.url }}">{{ post.title }}</a> - *{{ post.date | date: "%-d %B %Y"}}*
        </li>
    {% endfor %}

    {% for post in site.categories.ctf %}
        <li>
            {{ post.title }}
        </li>
    {% endfor %}
</ul>


[About this blog]({{ site.url }}/about/)