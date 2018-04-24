---
title: html5fordata上传文件
date: 2016-11-20 08:13:43
tags:
- html5
categories:
- 前端
---

### 标签
今天在构建项目时遇到一个问题,关于图片的交互,我们一般在引入图片的时候一般会用这样一个标签
```bash
<img src="#" />
```
然而我们上传图片的时候很明显不能只用一个url地址来与后台进行交互,毕竟本地的地址与后台服务器提供的地址是不一样的,而且地址的作用是用来帮我们找到这个图片,因此,经过查找我发现可以用html5的新属性formdata或者插件来实现这个功能,在这里主要是用formdata来进行上传的.

首先要有一个form表单,id值为upload,其中表单内容省略
``bash
<form id="upload"></form>
```

### 实例化formadata
```bash
var upload = document.getElementById"upload");
var data = new FormData(upload);
```

然后把内容插入进去就行了
```bash
data.append("username", "zhouyx");
```

图片的插入大致如此,那我们在本地如何判断图片上传是否成功呢
我们可以在network里查看
![code](http://oj171eydn.bkt.clouddn.com/pic.jpg)我们可以看到filename为pic.6这幅图已经上传成功.
