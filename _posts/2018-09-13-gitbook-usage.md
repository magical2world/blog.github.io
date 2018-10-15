---
layout: post
title: GitBook使用指南
date: 2018-09-13 18:51:32.000000000 +09:00
---

### 一、搭建GitBook环境

#### 1、搭建Nodejs环境

前往[Node.js官网](https://nodejs.org/en/)下载Nodejs并安装

安装成功后可在终端输入node -v查看是否安装成功

#### 2、安装GitBook可视化编写工具

下载并安装[GitBook Editor](https://legacy.gitbook.com/editor)，其中GitBook Editor可以帮助我们更方便的编辑文章。

#### 3、安装gitbook

在终端输入下面的指令，安装gitbook

```
npm install gitbook-cli -g
```

#### 4、使用MathJax渲染数学公式

如果要在书中使用公式，需要外部数学公式插件库。这里使用Mathjax。在你的书的目录下添加book.json文件，并在文件中添加下面内容

```
{
    "plugins":["mathjax"]
}
```

如果想在本地渲染，则需在终端输入

```
gitbook install ./
```

### 二、开始编辑文章

#### 1、初始化书籍目录

打开终端，在你所建的书的目录下输入

```
gitbook init
```

初始化后有两个必要文件，README.md及SUMMARY.md，其中README.md是对书籍的介绍，SUMMARY.md是书籍的目录。

#### 2、编辑书籍

用GitBook Editor打开你初始化的书籍，进入编辑你的书就可以了。GitBook是基于Markdown语法的。

当编辑好你的书籍后，在终端中输入下面的语句即可编译你的文章。

```
gitbook serve
```

然后在新的窗口中输入http://127.0.0.1:4000就可以查看书籍。

### 三、将你的文章上传到github上

新建一个repository，并将其clone到本地，将编辑好的书移动到clone后的文件夹中，在将文件夹中更新后的内容push到github上。

