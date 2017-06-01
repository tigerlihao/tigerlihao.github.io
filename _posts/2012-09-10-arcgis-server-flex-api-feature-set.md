---
title: ArcGIS Server Flex API中Feature Set构建问题
date: 2012-09-10 00:00:00 Z
categories:
- study
tags:
- ArcGIS
- Flex
- GIS
layout: post
---

### 问题

最近用ArcGIS Server Flex API做开发，需要调用ArcGIS Server的网络分析服务做最短路径查询。在调用服务的时候需要构建一个`FeatureSet`来保存路径需要经过的点。但是在调试的时候，在某些情况下会报错。

### 排错

跟踪代码，发现问题出在向`FeatureSet`添加新的`Graphic`的时候。回想了一下，发觉我的程序中路径点的来源有两个，一个是用户直接在地图上点的点，一个是通过查询得到的POI点，问题可能出在这里。再做了几次测试，分析出现错误的情形，发现当路径中的第一个点不是POI点，后面有POI点的情况下才会出错，反之正常。于是查了一下`FeatureSet`的API文档，发现`FeatureSet`是有一个Schema来存储`FeatureSet`中的`Graphic`包含哪些属性字段的，向`FeatureSet`中添加的`Graphic`的属性不能超出这些字段。如果没有定义这个Schema，`FeatureSet`就会根据第一个添加进来的`Graphic`的属性字段自动生成Schema。所以当第一个点为地图上点击的点时，没有属性字段，而后面添加POI点有属性字段，导致了添加失败。

### 解决

手动给`FeatureSet`定义属性字段的Schema。