---
title: python中%s和%r的区别
date: 2017-01-18 14:15:27
tags:
- python
categories:
- python
---
%r用repr()方法处理对象,而%s用str()方法处理对象，这里的repr()和str()都是python将值转化成字符串，只是repr()是供解释器读取，而str()是供人阅读。
两者的区别有点像前端jquery中的.html()和.text(),.html()有将html标签转化的能力，而.text()是直接显示，不转化。
```bash
$.html('<a>链接</a>')     //链接
$.text('<a>链接</a>')     //<a>链接</a>   .text()会保留标签
```
同理，
```bash
content = 'hello world!'
print 'hello %s ' % content      //hello hello world!
print 'hello %r ' % content      //hello 'hello world!'  %r会保留单引号
```
