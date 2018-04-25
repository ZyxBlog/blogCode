---
title: that的作用
date: 2016-12-27 12:47:08
tags:
- js
categories:
- 前端
---

在使用vue构建项目的时候,我们经常会使用
```bash
let that = this;
```
谈一下that的作用,在vue中this指的是vue生成的实例对象,但如果在模块的上下文里this的指代会发生变化,因此this的指代就会发生变化,所以我们有时需要先给vue实例对象的那个this,指代成that,以至于不发生矛盾.
当我们用模块化和js面向对象来写代码时,在闭包内,我们也需要用
```bash
var that = this;
```
同理也会因为实例化的对象指代的this,和内部函数的上下文指代this而容易引起编程错误,先把实例化的this赋值给that,让that等于实例化的对象,从而做好区分,方便编程.
