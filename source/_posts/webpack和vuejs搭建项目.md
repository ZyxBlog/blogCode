---
title: webpack和vuejs搭建项目
date: 2016-10-14 10:33:06
tags:
- vuejs
- webpack
categories:
- 前端
---

### 安装vue-cli
在确认nodejs,npm,cnpm,git安装后,首先创建一个文件夹vueProj

接着进入该文件夹后开始用npm安装vue-cli
```bash
npm install -g vue-cli
```
我们选取其中比较简单的模板webpack-simple#1.0,在确认y后会进行模板下载
![安装后截图](http://oj171eydn.bkt.clouddn.com/picture.jpg)

根据个人情况进行填写,至此基本框架就搭建好了.

### 安装依赖
下面我们开始安装依赖，将package.json里面的依赖安装好,不用npm install, 用换了淘宝源的cnpm
```bash
cnpm install
```

### run server
等待一会，下载完后，最后我们就把框架打好，可以开始写项目了，跑一下看看
![初始效果图](http://oj171eydn.bkt.clouddn.com/show.jpg)
