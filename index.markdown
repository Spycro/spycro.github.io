---
title: Index
layout: default
---

<ul>

{% for post in site.posts %}
    <li>
        [{{ post.title }}]({{ post.url }}) - *{{ post.date | date: "%-d %B %Y" }}*
    </li>
{% endfor %}

</ul>


[About this blog]({{ site.url }}/about/)  
