---
layout: post
title: "用ArcGIS Server发布WFS时坐标顺序设置"
category: study
tags: [ArcGIS, Web Service, GIS, WFS]
---

### 问题

指导新生学习OGC空间信息服务规范，用到ArcGIS Server来发布WFS，并用Openlayers做网页客户端进行显示。做的过程中遇到了要素无法显示的问题。

### 排错

开始以为是服务器端的问题，但是通过监控网络请求，发现与服务器的通信是成功的。又怀疑是调用Openlayer的代码有问题。但是检查了一遍，发现调用其他例子里的WFS是可以显示出结果的。然后对比了两个WFS服务器返回的数据，发现里面的坐标对有些问题。ArcGIS Server的WFS返回的坐标点是纬度在前，经度在后。而在Openlayers里面，坐标对是经度在前，纬度在后的。经纬度对调了个。位置肯定就变了，显示到地图范围以外了，当然就看不到结果了。

### 解决

可以通过修改ArcGIS Server的配置文件来设置坐标中经纬度值的排列顺序。

具体步骤：

1.  如果ArcGIS Server已经开启，先关闭它；
2.  找到ArcGIS Server配置文件所在的文件夹：`[ArcGIS Server的安装路径]\server\user\cfg`； 
3.  用文本编辑器打开对应服务的配置文件，例如`sample.MapServer.cfg`；
4.  找到WFSServer配置的部分，在`<Properties>`节点中插入`<AxisOrderWFS11>longlat</AxisOrderWFS11>`，如下面代码片段所示；
5.  重新启动ArcGIS Server。

{% highlight xml %}
    <Extension>
      <TypeName>WFSServer</TypeName>
      <Enabled>true</Enabled>
      <Properties>
        <CustomGetCapabilities>false</CustomGetCapabilities>
        <EnableTransactions>false</EnableTransactions>
        <Name>sample</Name>
        <OnlineResource>http://sample.com/arcgis/services/sample/MapServer/WFSServer</OnlineResource>
        <AppSchemaURI>http://sample.com/arcgis/services/sample/MapServer/WFSServer</AppSchemaURI>
        <AppSchemaPrefix>sample</AppSchemaPrefix>
        <AxisOrderWFS11>longlat</AxisOrderWFS11>
      </Properties>
      <Info>
        <WebEnabled>true</WebEnabled>
      </Info>
    </Extension>
{% endhighlight %}