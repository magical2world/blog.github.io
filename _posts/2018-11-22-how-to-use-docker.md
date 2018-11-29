---
layout: post
title: docker的安装及使用
date： 2018-11-22 19:03:32.000000000 +09:00
---

### 一、为什么选择docker

### 二、安装docker

#### 1、卸载老版本的docker

在安装docker之前需要先卸载老版本的docker

```
sudo apt-get remove docker docker-engine docker.io
```

#### 2、安装Docker CE 

安装docker的方法有很多，这里仅仅介绍使用库安装，其它安装方式可以到 https://docs.docker.com/install/linux/docker-ce/ubuntu/#extra-steps-for-aufs查看

##### （1）、更新一下源

```
sudo apt-get update
```

##### （2）、安装一些必要的包

```
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
```

##### （3）、添加docker的官方GPG值

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
```

##### （4）、选择合适的库

我的电脑是x86_64的，所以使用下面的语句

```
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```

##### （5）、安装Docker CE

```
sudo apt-get install docker-ce
```

##### （6）、检查是否安装成功

首先将hello-world的文件pull到本地

```
sudo docker image pull library/hello-world
```

成功之后就可以查看这个image文件了

```
sudo docker image ls
```

然后运行这个文件

```
sudo docker run hello-world
```

如果出现下面的信息，则说明安装成功

<figure>
    <a><img src="{{site.url}}/my_pics/docker/hello_world.jpg"></a>
</figure>

