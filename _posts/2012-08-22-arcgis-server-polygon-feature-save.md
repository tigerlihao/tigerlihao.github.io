---
title: ArcGIS Server要素服务多边形保存问题
date: 2012-08-22 00:00:00 Z
categories:
- study
tags:
- ArcGIS
- Web Service
- GIS
layout: post
---

### 问题

最近用ArcGIS Server Flex API做开发，需要用Feature Service来保存用户绘制的特殊图形。图形绘制的方法是自己写的，通过生成为多变形要素进行保存。但是在保存自己构建的多边形要素时出现了无法保存的问题。

### 排错

开始以为是服务没有配置好，但是用API本身的Draw Tool绘制的多边形却可以保存，排除。然后检查自己的写的Draw Tool，绘制和显示都没有问题。又吧自己绘制的多边形输出为json，用ArcGIS Server网页上的测试表单提交，问题重现了。通过检查，发现在构建多边形时，环中的坐标串没有把环的第一个坐标再保存为最后一个，而API自带的Draw Tool会把环中第一个坐标复制一份到最后一个坐标。

### 解决

在自己构建多边形要素时，需要确保环的坐标串中收尾点是同一个点，否则ArcGIS Server会认为这不是一个有效的环。