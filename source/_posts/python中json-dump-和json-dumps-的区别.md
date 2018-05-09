---
title: python中json.dump()和json.dumps()的区别
date: 2017-12-05 13:47:33
tags:
- python
categories:
- 后台
---
首先问题的起因是一个学习python时的demo，开始学习json.jump()的用法，开始由于在pycharm中创建了一个文件名叫json.py导致代码么，没有通过编译。
重命名，ok。
但是在解决上一个问题百度时发现有json.jumps()的存在。同时发现对应json.load(),还有一个json.loads()的存在。
jump和jumps的区别在于jump主要是针对于文件的，jump的特点是后面接受两个参数，jumps后面只有一个参数，两个第一个参数一样都是要操作的数据data，jump有第二个参数，第二个参数是文件名，主要是用来操作文件，但是jumps()不具备这个功能。loads和load同理。
同时dumps是将dict转化成str格式，loads是将str转化成dict格式。
