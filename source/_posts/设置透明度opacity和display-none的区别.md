---
title: js设置透明度visible和display:none的区别
date: 2016-07-27 18:51:17
tags:
- css
- js
categories:
- 前端
---

js设置visible:hidden和display:none都是设置元素隐藏的方法,但是在近期使用过程中总结了几个不同之处:

### display:none
display:none 对于一个高度为h的块元素来说,在页面上彻底消失，它的高度变成了0,如果绑定了事件不会触发。

### visible:hidden
visible:hidden 对于一个高度为h的块元素来说,使对象在网页上不可见，但该对象在网页上所占的空间没有改变，他的高度还是h,如果绑定了事件依旧会触发。

### 使用
在动画设置的时候,用visible比较多,因为存在一个关键帧的设置,透明度会使动画效果更好。
写tab标签的时候,用display:none比较多。
