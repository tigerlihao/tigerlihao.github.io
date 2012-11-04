---
layout: page
title: Welcome!
tagline: This is tigerlihao's website.
---
{% include JB/setup %}



## 我的项目展示

* [HTML5 Canvas实现魔方](/html5demo/cubic/)
* [HTML5+CSS3仿真Timor台历](/html5demo/timor/)

    
## 我的博客文章

<ul>
  {% for post in site.posts limit:5 %}
    <li><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a> <span class="muted">{{ post.date | date: "%Y-%m-%d" }}</span></li>
  {% endfor %}
</ul>

## 我的摄影作品

* [点点：泰格影像志](http://tigerphoto.diandian.com/archive)
* [Flickr：tigerlihao](http://www.flickr.com/photos/tigerlihao)