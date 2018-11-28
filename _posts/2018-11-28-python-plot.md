---
layout: post
title: python画图
date: 2018-11-28 22:14:32.000000000 +09:00
---

#### 一、折线图

#### 二、柱状图

绘制柱状图的命令是

```python
import matplotlib.pyplot as plt
import matplotlib as mpl

custom_font=mpl.font_manager.FontProperties(fname='C:\Windows\Fonts\simfang.ttf',size=40)#设置字体格式1
custom_font1=mpl.font_manager.FontProperties(fname='C:\Windows\Fonts\simfang.ttf',size=18)#设置字体格式2

def autolabel(rects):#为柱状图添加数值
    for rect in rects:
        height=rect.get_height()
        plt.text(rect.get_x()+rect.get_width()/2-0.1,1.03*height,'%s'%float(height))

name_list=['1','2','3','4','5','6']

num_list1=[0.862,0.835,0.865,0.882,0.871,0.883]
num_list2=[0.885,0.926,0.908,0.913,0.926,0.924]
num_list3=[0.904,0.873,0.892,0.899,0.909,0.903]
num_list4=[0.922,0.963,0.929,0.941,0.943,0.963]

x=list(range(len(num_list1)))
total_width,n=0.8,4#total_width为总的宽度，4为需要画的数据的类别数

width=total_width/n
a=plt.bar(x,num_list1,width=width,label='CCA')
for i in range(len(x)):
    x[i]=x[i]+width
b=plt.bar(x,num_list2,width=width,label='KCCA')
for i in range(len(x)):
    x[i]=x[i]+width
c=plt.bar(x,num_list3,width=width,tick_label=name_list,label='MestCCA')#设置tick_label可以更改横坐标的名称
plt.tick_params(labelsize=30)#设置坐标轴刻度字体大小
for i in range(len(x)):
    x[i]=x[i]+width
d=plt.bar(x,num_list4,width=width,label='ConvCCA')
plt.xlabel(u'被试编号',fontproperties=custom_font)
plt.ylabel(u'准确率',fontproperties=custom_font)
plt.ylim(ymax=1.3)
autolabel(a)
autolabel(b)
autolabel(c)
autolabel(d)
plt.legend(prop=custom_font1)
plt.show()
```



