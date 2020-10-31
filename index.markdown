---
title: Index
layout: default
---

<ul>

{% for post in site.posts %}
    <li>
        <a href="{{ post.url }}">{{ post.title }}</a> - <em>{{ post.date | date: "%-d %B %Y" }}</em>
    </li>
{% endfor %}

</ul>


[About this blog]({{ site.url }}/about/)  
