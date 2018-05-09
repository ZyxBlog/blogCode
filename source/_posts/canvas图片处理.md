---
title: canvas图片处理
date: 2017-10-24 13:32:54
tags:
- html5
categories:
- 前端
---
像素操作：通过getImageData().data获取

* 反转效果：data[i + 0] = 255 - data[i]
* 黑白效果：data[i + 0] = data[i + 1] = data[i + 2] = average
* 亮度效果：同时加一个正值一个负值(变亮或者是变暗)
* 复古效果：取三个数的某种加权平均值
r = data[i + 0]
g = data[i + 1]
b = data[i + 2]
data[i + 0] = r * 0.39 + g * 0.76 + b * 0.18;
data[i + 1] = r * 0.35 + g * 0.68 + b * 0.16;
data[i + 2] = r * 0.27 + g * 0.53 + b * 0.13;
* 透明处理：data[i + 3] *= n
