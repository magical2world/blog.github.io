---
layout: post
title: 如何配置服务器及使用远程桌面系统
data: 2018-09-06 15:34:24.000000000 +09:00
---

### 一、服务器配置

#### 1、安装Ubuntu操作系统

这部分网上有很多教程，这里不做介绍

#### 2、安装显卡驱动

##### （1）、到NVIDIA官网<https://www.nvidia.cn/Download/index.aspx?lang=cn>下载驱动

##### （2）、安装NVIDIA驱动

卸载原有驱动

```
sudo apt-get remove -purge nvidia*
```

禁用nouveau

打开编辑配置文件：

```
/etc/modprobe.d/blacklist.conf
```

在最后一行添加

```
blacklist nouveau
禁用nouveau第三方驱动，之后也不需要改回来
```

执行：

```
sudo update-initramfs -u
```

重启后执行

```
lsmod | grep nouveau
```

安装驱动

```
sudo 你所下载的驱动文件 -no-opengl-files    #不安装OpenGL
```

#### 3、安装CUDA

根据你所要安装的深度学习框架到CUDA官网<https://developer.nvidia.com/cuda-downloads>下载相应的文件。

<figure>
    <a><img src="{{site.url}}/my_pics/1536229944(1).png"></a>
</figure>

安装官网提示安装CUDA。切记在安装过程中第一步选项输入n，因为第一步是安装显卡驱动，而我们已经在上一步中安装了显卡驱动，之后就一直输入y或者enter键即可安装CUDA。

#### 4、安装cuDNN

根据你所选择的框架选择你所需要的cuDNN版本到官网<https://developer.nvidia.com/cudnn>下载cuDNN并解压。然后在终端输入下面的内容，将解压后得到的include/和lib64/复制到CUDA的安装目录下的include/和lib64里面

```
cd 解压后的路径
sudo cp -P include/cudnn.h /usr/local/cuda-9.0/include
sudo cp -P lib64/libcudnn* /usr/local/cuda-9.0/lib64
sudo chmod a+r /usr/local/cuda-9.0/lib64/libcudnn*
```

### 二、配置远程桌面登录系统

#### 1、使用管理员账号添加新用户

#### 2、安装Ubuntu的mate桌面环境

打开终端，在终端中输入：

```
sudo apt-get update
sudo apt-get install ubuntu-mate-core
sudo apt-get install ubuntu-mate
```

然后注销或重启Ubuntu即可

3、通过ssh远程登录服务器

##### （1）、Windows端远程ssh登录

下载并安装putty，然后打开putty，在红线部分输入服务器的IP地址，然后点击open输入自己的用户名及密码就能通过终端远程访问服务器了。

<figure>
    <a><img src="{{site.url}}/my_pics/1536230953(1).png"></a>
</figure>

##### （2）、Ubuntu端远程ssh登录

在终端中输入下面指令就可以实现通过终端远程访问服务器了。

```
ssh 用户名@服务器IP
```

#### 4、配置vnc

进入服务器终端后，在终端中输入vncserver，这是系统会自动在home路径下生成一个.vnc文件夹。

然后在终端中输入以下命令：

```
cd .vnc
vi xstartup
```

修改xstartup文件的最后一行为mate-session &

<figure>
    <a><img src="{{site.url}}/my_pics/1536230117(1).png"></a>
</figure>

然后在终端中输入下面的指令来杀死你刚才开辟的端口号：

```
vncserver -kill :你刚才开启的端口号
```

从新使用vncserver打卡一个新的端口号。

#### 5、使用远程桌面系统

##### （1）、Windows下使用远程桌面系统

下载vncviewer<https://www.realvnc.com/en/connect/download/viewer/>，并打开。在红线部分输入<u>IP地址:你所开启的端口号</u>即可进入远程左面 系统

<figure>
    <a><img src="{{site.url}}/my_pics/1536230178(1).png"></a>
</figure>

##### （2）、Ubuntu下使用远程桌面系统

安装vncviewer

```
sudo apt-get install xvnc4viewer
```

在终端中输入vncviewer，然后输入<u>IP地址:你所开启的端口号</u>即可进入远程桌面系统

