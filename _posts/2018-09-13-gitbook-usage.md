```
layout: post
title: GitBook使用指南
date: 2018-09-13 18:51:32.000000000 +09:00
```

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

