---
title: OWL-S Editor和Protégé的版本匹配问题
date: 2011-04-22 00:00:00 Z
categories:
- study
tags:
- OWL
- OWL-S
- Web Service
layout: post
---

最近做实验，需要对服务进行OWL-S语义描述，于是就找到OWL-S Editor这个工具。这个工具的最新的版本是build 23，居然是2006年的，居然这么久都没有更新。不过话又说回来，只要能用就好，新的也不一定是最好的。这个OWL-S Editor是以Protégé插件的形式存在的，还好装有Protégé，于是下了OWL-S Editor放到Protégé的plugin下面，重启Protégé，在插件列表里能看到OWL-S Editor，但就是找不到owlstab。

后来发现是Protégé的版本问题，Protégé不同版本的插件是不兼容的，我装的又是最新版的Protégé 4.0.2，Protégé 4和3已经有很大的改变了，难怪。于是换了Protégé 3里的最新的3.4.5，但问题依旧。可怜的OWL-S Editor官网连主页都没了，只搜到个下载页，插件里也没有说适用于哪个版本的Protégé。没办法，一个一个试吧，于是下载了Protégé 3.1.1、3.2.1、3.3.1，最后终于发现这个OWL-S Editor build 23是和Protégé 3.2.x兼容的。

下载地址：

*  [OWL-S Editor build 23](http://projects.semwebcentral.org/frs/download.php/285/owlseditor-build23.zip)
*  [Protégé 3.2.1](http://protege.cim3.net/download/old-releases/3.2.1/full/)