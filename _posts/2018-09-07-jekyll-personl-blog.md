---
layout: post
title: 使用Jekyll建立你的个人博客
date: 2018-09-07 14:58:32.000000000 +09:00
---

以前总是使用简书、csdn这类网站的博客，有一天突然发现可以自己建立自己的博客，而它那种精美的 布局立马吸引到了我，更是能使自己的DIY兴趣得到充分的发展。下面小编就讲一下小编的入坑经历。下面的所有步骤均是基于Windows系统的。

### 一、使用github page

#### 1、创建新的repository

打开github，新建一个repository，repository的命名方式为example.github.io。

<figure>
    <a><img src="{{site.url}}/my_pics/1536327733(1).png"></a>
</figure>


#### 2、下载github desktop

去[官网](https://desktop.github.com/)下载github desktop，并将你创建的repository clone到本地。这里要多说一句的是github简直是神器，能够记录你对代码的修改内容，从此妈妈再也不用担心我的代码会丢失了。

### 二、配置Jekyll

#### 1、安装ruby

Jekyll是基于ruby的，因此需要安装ruby。Windows下安装ruby非常简单，在[官网](<https://www.ruby-lang.org/en/downloads/>)RubyInstaller文件后双击运行即可。

#### 2、安装Jekyll

打开终端在终端中输入：

```
gem install jekyll
```

### 三、在别人的主题上设计自己的博客

#### 1、选择自己喜欢的主题进行下载

对于初学者来说自己设计主题实在是太难了，但是在别人的设计的主题上进行修改就简单的多了，这里小编是通过在<https://github.com/onevcat/vno-jekyll>上进行修改得到的，该主题目录下的文件分布如下图所示：

<figure>
    <a><img src="{{site.url}}/my_pics/1536412853(1).png"></a>
</figure>


#### 2、对下载的主题进行修改

##### （1）、安装必要的插件

在终端中执行下面的语句，已安装该主题所必要的插件

```
bundle install
```

##### （2）、修改主题

在整个文件系统中，文件夹assets/images下存放的分别是主题的背景图像及头像图像，将这两幅图换成自己的图像就行。

此外我们还可以通过修改_config.yml文件来修改我们博客所要显示的内容。

```
title: 你的博客的标题
subtitle: 子标题
welcome_message: 欢迎词
description: 关于你的个人博客的描述

cover_color: 背景配色

blog_button: 你所要添加的按钮

social: 你的各种的社交账号
```

修改好之后在终端中输入```bundle exec jekyll server```从新开启Jekyll。复制地址```http://127.0.0.1:4000/```到你的浏览器就可以看到修改后的结果。、

##### （3）、写文章

个人博客中的文章都放在_posts文件夹中，是Markdown文件。这里推荐一个非常好用的Windows版的编写Markdown文件的工具[Typora](https://typora.io/#windows)，有关Typora的使用可以参考<https://www.jianshu.com/p/5e199c5c7a33>。

此外，我们也可以通过安装插件jekyll-admin来方便我们编辑博客。

首先，在Gemfile中添加

```
gem 'jekyll-admin',group: :jekyll_plugins
```

执行

```
bundle install
bundle exec jekyll server 
```

在浏览器中输入```http://127.0.0.1:4000/admin```，在posts中添加new posts就会出现下面的界面：

<figure>
    <a><img src="{{site.url}}/my_pics/1536414562(1).png"></a>
</figure>

这个就很像是简书、csdn这些博客的编写方式了。

### 四、绑定自己的域名

#### 1、在[万网](https://wanwang.aliyun.com/)购买域名

##### （1）、选择一个你自己喜欢的域名并购买

##### （2）、进入==管理控制台->云解析 DNS->解析设置==进行添加A记录及CNAME记录

<figure>
    <a><img src="{{site.url}}/my_pics/1536373305(1).png"></a>
</figure>


其中CNAME的记录值是你的github的名称，A的记录值是IP地址，IP地址需是下面4个IP地址中的至少一个。（注意：万网购买的域名需要实名认证后才能使用）

- 185.199.108.153
- 185.199.109.153
- 185.199.110.153
- 185.199.111.153

#### 2、添加CNAME文件

在github的settings中找到github pages，在custom domain中输入你购买的域名，github就会自动生成CNAME文件。选中Enforce HTTPS，当红线部分变成绿色，则绑定成功。然后我们就可以通过自己的域名来登录自己的blog了。

<figure>
    <a><img src="{{site.url}}/my_pics/1536374026(1).png"></a>
</figure>


#### 参考：

<http://louisly.com/2016/04/used-jekyll-to-create-my-github-blog/>

<https://www.youtube.com/watch?v=Zt_QzSbyDcw&t=764s>