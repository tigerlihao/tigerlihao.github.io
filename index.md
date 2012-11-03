---
layout: page
title: Welcome!
tagline: This is tigerlihao's website.
---
{% include JB/setup %}



## 我的项目展示

* [HTML5 Canvas实现魔方](/html5demo/cubic.html)
* [HTML5+CSS3仿真Timor台历](/html5demo/timor.html)

    
## 我的博客文章

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date: "%Y-%m-%d" }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>


