---
layout: post
title: 如何使用Git及Github
date: 2018-10-19 11:35:32.000000000 +09:00
---

#### 1、在你的github上新建一个repository

<figure>
    <a><img src="{{site.url}}/my_pics/new_repository.jpg"></a>
</figure>

然后将这个repository clone到本地。

#### 2、同步你的代码到github

##### （1）、初始化Git

```
git init
```

##### （2）、添加更新的文件

```
git add 更新的文件
```

##### （3）、设置commit

```
git commit -m "内容"
```

##### （4）、添加远程仓库

```
git remote add origin 你的repository的链接
```

如果在这一步出现错误：fatal: remote origin already exists.

则需要先 删除远程Git仓库

```
git remote rm origin
```

##### （5）、提交分支

```
git push -u origin master
```

提交的时候需要输入你的账号和密码。完成提交后刷新你的网页就能看到更新了。



注意：如果在执行上述操作时看到要求输入你的姓名及邮箱的提示，按要求输入相应代码即可。当然姓名和邮箱可以都是不真实的，这个无关紧要。