---
title: jquery中点击事件的区别
date: 2016-09-25 08:44:50
tags:
- jquery
- js
categories:
- 前端
---

在jquery中关于点击事件click,我们除了用$(‘select’).click(function(){}),还可以用.on()或者.bind()或者.delegate()或者.live()来实现功能.

### bind
bind为绑定事件,但是对于尚未存在的DOM元素是无法绑定的,同时不适宜选择器匹配较多的元素.

### delegate
delegate为事件委托,后面传递的是三个参数,第一个是操作的元素,第二个的是触发click,第三个是执行的函数,同时它会向上冒泡,直到绑定的元素,不适宜dom树太深.

### live
live也是通过绑定事件,但是能弥补bind的缺陷,对于尚未存在的元素是可以绑定的.

### on
on是比较好的方法,相对来说功能比较全,如果用jquery的话,尽量推荐用on
