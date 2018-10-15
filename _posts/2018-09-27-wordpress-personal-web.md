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

如果无法开启这两项服务则可能是端口被占用，这时修改一下配置文件中的端口号就行，这里小编遇到三种错误，分别是开启Apache时httpd.conf的80端口被占用，小编通过点击进入这个文件，将所有80改为8081问题就解决了。同样，小编还改变了httpd-ssl.conf文件中的443为4431，my.ini中的3306为3316。最终才成功同时开启了Apache及MySQL。当然如果没有报错就直接开启就无需修改端口好了。

<figure>
    <a><img src="{{site.url}}/my_pics/xampp2.png"></a>
</figure>

### 二、建立数据库

开启Apache及MySQL之后，在浏览器中输入http://localhost:8081/phpmyadmin/，这里因为我将httpd.conf的端口号进行了修改，所以要在localhost后面加上:8081，如果未进行修改可不加。在打开的界面中新建一个数据库：

<figure>
    <a><img src="{{site.url}}/my_pics/xampp3.png"></a>
</figure>

### 三、安装wordpress

下载[wordpress](https://wordpress.org/download/)，并将其解压到你所安装xampp路径的htdocs文件夹下。打开浏览器并输入http://localhost:8081/wordpress/后会出现下面的界面：

<figure>
    <a><img src="{{site.url}}/my_pics/select_langue.png"></a>
</figure>

在出现的界面中设置自己的语言。然后进入下面的界面，来对你的账号进行设置，切记用户名设置为"root"，密码暂时设置为空，数据库名设置为你刚才新建的数据库名。其他的不用改变。

<figure>
    <a><img src="{{site.url}}/my_pics/setting_name.png"></a>
</figure>

接下来就是要设置一些站点的基本信息，以及第一个站点用户的信息，如下图所示，按照提示填写完信息后点击"安装WordPress"，等待数秒后即可完成安装。

<figure>
    <a><img src="{{site.url}}/my_pics/get_information.png"></a>
</figure>



### 四、个性化设计你的网站

#### 1、添加多用户

点击用户来添加新用户，就可以使多人来登录你的网站了。此外你还可以在settings中设置新添加用户的权限。

<figure>
    <a><img src="{{site.url}}/my_pics/wordpress1.png"></a>
</figure>

#### 2、更改主题

在外观中点击主题，这里会有一些安装好的主题供你使用。你也可以自己根据自己的需求来下载一些主题来使用。当然你也可以对下载好的主题进行自定义来将将网站修改成你喜欢的界面

<figure>
    <a><img src="{{site.url}}/my_pics/wordpress2.png"></a>
</figure>

#### 3、新建文章及界面

点击文章或界面即可看到自己的文章或界面，通过编辑或新建就可以对文章或页面进行修改。需要注意的是，如果要在文章中添加图片或者是视频，需要先将他们添加到媒体库当中。

#### 4、更改地址

在settings中，wordpress地址及站点地址默认的是http://localhost:8081/wordpress，如果使用这个默认值，则在别的设备上登录网站时会出现网站混乱的情况。解决的方法是将localhost换成你的主机的IP地址，如127.0.0.1。

### 五、绑定自己的域名

#### 1、购买域名

在[万网](https://wanwang.aliyun.com/?utm_content=se_800089&gclid=EAIaIQobChMI3dThy9_c3QIVCGoqCh2G2w-rEAAYASAAEgK7b_D_BwE)或者是其他网站上购买自己的域名

<figure>
    <a><img src="{{site.url}}/my_pics/wordpress3.png"></a>
</figure>

#### 2、解析域名

进入控制台来添加解析A记录，如下图所示，其中红线里面填入你的计算机的IP地址.

<figure>
    <a><img src="{{site.url}}/my_pics/wordpress4.png"></a>
</figure>

添加完毕之后等待解析生效，可以在终端中输入：

```
ping 域名
```

来检验解析是否生效。域名生效后就可以通过使用<u>域名：8081/wodpress</u>来登录网站了。