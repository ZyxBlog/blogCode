---
title: js捕捉事件和冒泡事件
date: 2016-11-15 08:43:00
tags:
- js
categories:
- 前端
---

js实现两种事件主要是用到了addEventListener()添加事件处理程序.
在addEventListener(“click”,function(){},boolean)里面第一个参数可以是触发的事件名click等,第二个参数是执行的函数,第三个是一个boolean值,默认是false.
当为false时,为冒泡事件;当为true时,为捕获事件.
* 冒泡事件过程:是子元素向父元素过渡,例如:button->div->body->document->window
* 捕获事件过程:是父元素向子元素过渡,例如:window->document->body->div->button
