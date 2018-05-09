---
title: 关于hack
date: 2017-02-13 18:52:28
tags:
- css
categories:
- 前端
---

hack技巧作为兼容样式例如IE6等低版本的浏览器。
* 里面最常用的一种技巧！important在IE6下有些情况不显示，{color：red！important;color:blue;}此时会出现IE6颜色仍然为蓝色，但是其他浏览器还是会出现颜色为红色。{color:red!important}{color:blue}此时浏览器显示字为红色。
* \9，+，-的区别：\9用于属性后面，识别于IE6,7,8；+用于属性前面，识别于6，7；-也用于属性前面，识别于IE6
* 关于IE和其他浏览器的区别：在于IE浏览器对伪类支持不广泛。
  具体方法如下：@-moz-document url-prefix(){} 这是通过内核的方法判断，仅对于火狐使用。
  +html 后面接css仅对于IE7识别。.类名，x:-moz-any-link,x:default{} IE7和火狐3.5以下。
* 关于IE6,7,8和其他浏览器区别@media all and(min-width:0px){.类名{}}
* google浏览器和其他的区别，主要靠谷歌浏览器的内核webkit判断：@media screen and(-webkit-min-device-pixel-ratio:0){.类名{}}
