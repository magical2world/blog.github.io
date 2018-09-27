---
layout: post
title: 使用wordpress来搭建网站
date: 2018-09-27 21:41:32.000000000 +09:00
---

最近要帮实验室做一个网站，来方便新入学的师弟师妹们了解实验室项目，所以就学习了一下如何使用wordpress以本地计算机为服务器搭建一个网站。下面就简单说一下小编入坑的经历。

### 一、搭建必要的环境

使用wordpress需要依赖于Apache、MySQL及php。分别安装这些太麻烦了，这里小编使用的是[xampp](https://www.apachefriends.org/index.html)，它是一个集成了这三个的环境。

下载之后直接按照步骤安装，之后打开xampp，其界面如下：

<figure>
    <a><img src="{{site.url}}/my_pics/xampp1.png"></a>
</figure>

点击start，开启Apache及MySQL

如果无法开启这两项服务则可能是端口被占用，这时修改一下配置文件中的端口号就行，这里小编遇到三种错误，分别是开启Apache时httpd.conf的80端口被占用，小编通过点击进入这个文件，将所有80改为8081问题就解决了。同样，小编还改变了httpd-ssl.conf文件中的443为4431，my.ini中的3306为3316。最终才成功同时开启了Apache及MySQL。

<figure>
    <a><img src="{{site.url}}/my_pics/xampp2.png"></a>
</figure>

### 二、建立数据库

### 三、安装wordpress

### 四、个性化设计你的网站