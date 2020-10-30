---
title: Index
layout: default
---

<ul>
    {% for post in site.posts %}
        <li>
            <a href="{{ post.url }}">{{ post.title }}</a>
        </li>
    {% endfor %}

    {% for categories in site.categories %}
        <li>
            {{ categories }}
        </li>
    {% endfor %}
</ul>