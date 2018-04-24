---
title: vue和webpack项目中外引插件
date: 2016-10-20 10:34:05
tags:
- vuejs
- webpack
categories:
- 前端
---

### 解决外部文件的引入
webpack+vue这种框架与普通html文件写入是不同的，它的语法是建立在ES6之上的，因此我们不能像平时一样用
```bash
<link rel="stylesheet" type ="text/css" href="a.css" />
<script type="text/javascript" src="a.js"></script>
首先我们需要在webpack.config.js中loaders里面配置好css或者less.<br>接着我们可以在该.vue文件里面的style模块中用ES6的语法import直接引入该文件.
对于初学者来说可能要配置和引入文件比较麻烦,那我们可以选一种更直接的方法,那就是在index.html中像普通css和js一样引入.
![程序图](http://oj171eydn.bkt.clouddn.com/chengxutu3.jpg)

### scoped
对于每个页面的style我们发现会出现样式干扰的情况,经查阅,我们可以发现
```bash
<style type="text/css" scoped>
```
使用scoped就能避免这个问题了
