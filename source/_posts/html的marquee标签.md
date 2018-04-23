---
title: html的marquee标签
date: 2016-08-12 18:54:40
tags:
- html
categories:
- 前端
---

### 特点
marquee让我好奇的地方在于：虽然它是html标签，但却能实现像js或者css3一样的字幕滚动的动态效果，实在很有趣。
marquee标签有很多可用的属性，除了宽高,对齐方式,背景颜色这些常规属性,还有一些特有属性。

### 属性
behaviour是设定滚动的方式,可用alternate表示在两端来回滚动;slide从一端到另一端,不重复;scroll从一端到另一端,重复
direction是设置滚动的方向,可用up,down,left,right上下左右滚动
loop是设置滚动的次数,默认loop=”-1”,表示一直滚动
vspace和hspace是设定活动字幕里所在的位置距离父容器垂直/水平边框的距离
scrollamount是设置滚动速度,单位为pixels
scrolldelay设定活动字幕滚动两次之间的延迟时间，单位millisecond（毫秒）
