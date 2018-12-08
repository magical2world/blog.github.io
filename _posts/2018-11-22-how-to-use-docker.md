---
layout: post
title: docker的使用
date: 2018-11-22 19:03:32.000000000 +09:00
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
<http://www.ruanyifeng.com/blog/2018/02/docker-tutorial.html>

### 三、docker的基本操作

#### 1、使用docker hub

[docker hub](https://hub.docker.com/)是一个类似github的东西，用户将自己的镜像上传到上面，也可以在上面从上面下载别人的镜像来使用，十分方便开发者对镜像的使用及管理。

##### （1）、下载镜像

这里以TensorFlow的镜像为例，我们在docker hub中搜索TensorFlow就能找到TensorFlow的镜像

<figure>
    <a><img src="{{site.url}}/my_pics/docker/docker_search_tf.jpg"></a>
</figure>

按照上面的提示在终端中下面的语句，下载镜像

```
sudo docker pull tensorflow/tensorflow
```

这时查看镜像

```
sudo docker image ls
```

可以看出已经多出了tensorflow/tensorflow这一项

<figure>
    <a><img src="{{site.url}}/my_pics/docker/after_tf.jpg"></a>
</figure>

##### （2）、上传镜像

想要上传自己的镜像，首先到官网注册一个docker hub账号。然后你需要更改一下你的镜像的tag

```
sudo docker tag tensorflow/tensorflow 你的账号名/tensorflow
```

这时本地就会出现一个“你的账号名/tensorflow”的镜像。

在上传镜像的时候需要先在本地登录你的账号

```
sudo docker login
```

然后输入账号及密码。

这时在终端输入：

```
sudo docker push 你的账号名/tensorflow
```

就能将镜像上传。

#### 2、创建自己的镜像

在使用docker时，有时我们需要构建自己的镜像。创建自己的镜像需要先建立一个空文件件，然后在文件夹中新建一个Dockerfile文件，文件中的内容是你为镜像配置的一些必要的东西，例如：

```
# This is a comment

FROM python:2.7-slim
```

是配置了默认的python，具体Dockerfile的编辑可以参考<>

然后在当前目录先输入：

```
sudo docker build -t 你的镜像名 .
```

来生成镜像。

#### 3、在容器中安装必要的库

##### （1）、运行容器

```
sudo docker run -t -i tensorflow/tensorflow /bin/bash
```

这是我们就会进入一个临时终端：

<figure>
    <a><img src="{{site.url}}/my_pics/docker/docker_terminal.jpg"></a>
</figure>

##### （2）、在容器中安装软件

一般情况下，我们都需要根据自己的要求对pull下的容器使其满足自己的工作要求。其中最基本的就是在上面安装一些必要的包或者python库。这点在运行镜像并进入终端后就可以像在实体机上进行操作的方式来进行配置。只是这里不再需要sudo权限。

#### 4、使用容器运行本地程序

这一步是使用docker的关键，通过利用docker上的配置环境来运行本机的程序可以避免在其他机器上运行程序时来重新配置环境。使用容器运行本地程序的具体操作是：

```
sudo docker run -t -i -v /home/amax/test.py:/run/test.py -v /home/amax/test:/run/test tensorflow/tensorflow python /run/test.py
```

在运行主机的程序时需要先将主机的文件挂载到容器中，具体操作就是在“-v”后面加入“主机文件的绝对路径:你要挂载的路径”。需要注意的是，所要挂载的路径的名必须是以“/”开头的，此外你的程序所涉及到的文件都要挂载到容器上，并且要确保文件系统保持一致。然后我们就能利用容器运行本地程序。

#### 5、删除镜像

##### （1）、删除镜像

```
sudo docker images
```

然后会出现镜像的ID，根据镜像的ID来对进行进行删除

<figure>
    <a><img src="{{site.url}}/my_pics/docker/image_id.jpg"></a>
</figure>

例如删除第一个镜像

```
sudo docker rmi 2054925f3b43 
```

当然也可以直接使用镜像的名称来对镜像进行删除

```
sudo docker rmi 镜像名
```

##### （2）、删除容器

当有相应的容器时就无法对该镜像进行删除，这个时候需要先删除或者停止容器

首先查看容器

```
sudo docker ps -a
```

然后就可以像删除镜像一样直接删除容器

```
sudo docker rm 容器的ID
```

当然还可以使用下面的语句直接删除所有的容器

```
sudo docker rm $(sudo docker ps -aq)
```

删除容器后就可以实现对镜像的删除

停止容器的操作基本一致

```
sudo docker stop 容器的ID
sudo docker stop $(sudo docker ps -aq)
```



