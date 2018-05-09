---
title: canvas学习实践
date: 2017-09-23 13:07:34
tags:
- html5
categories:
- 前端
---
最近在学习canvas，同样图形技术，canvas和svg却是完全不同的，首先canvas是建立在js上的动态绘图，而svg是静态的xml描述的。
同canvas是基于位图的，适用于像素处理和动态渲染。图片放大会失真，但是svg是矢量图每次修改时，canvas需要重绘，但是svg不需要。
今天主要是在学习了canvas后，自己是实践了两个功能，一个是绘制一个正多边形，一个是画一个调色板。
首先是正多边形：

### html部分
```bash
<canvas id="canvas" width="500" height="500" style="border: 1px dashed #808080"></canvas>
```

### js部分
```bash
function $$ (id) {
    return document.getElementById(id);
}  // n为多边形的边数，dx，dy表示中心坐标，size表示大小}}
function createX (cxt， n, dx, dy, size) {  // 封装的方法    
    cxt.beginPath();
    var degree = (2 * Math.PI) / n;
    for (var i = 0; i < n; i++) {
       var x = Math.cos(i * degree);        
       var y = Math.sin(i * degree);       
       cxt.lineTo(x * size + dx, y * size + dy);
       cxt.closePath();
    }
}
window.onload = function () {
    var cnt = $$("canvas");
    var cxt = cnt.getContext("2d");
    createX(cxt, 7, 100, 75, 50);
    cxt.fillStyle = "red";
    cxt.fill();
}
```
正多边形的绘制主要是根据多边形的长度和角度俩计算出每个点的坐标。
下面是实现了一个调色板的图：
```bash
function $$(id) {
    return document.getElementById(id);
}
var cnt = $$("canvas");
var cxt = cnt.getContext("2d");
for (let i = 0; i < 6; i++) {
    for (let j = 0; j < 6; j++) {        
        cxt.fillStyle = "rgb(" + Math.floor(255 - 42.5 * i) + "," + Math.floor(255 - 42.5 * j) + ",0)";        cxt.fillRect(j * 25, i * 25, 25, 25);
    }
}
```
效果图如下：
![show](http://oj171eydn.bkt.clouddn.com/color1.png)
将调色板做成像插件一样的colorPicker形式
js代码:
```bash
var nap = $$("canvas1");
var npt = nap.getContext("2d");
var r = 255, g = 0, b = 0;
for (let i = 0; i < 150; i++) {
    if (i < 25) {
        g += 10;
    } else if (i > 25 && i < 50) {
        r -= 10;
    } else if (i > 50 && i < 75) {       
        g -= 10;
        b += 10;
    } else if (i >= 75 && i < 100) {
        r += 10;
    } else {
        b -= 10;
    }    
}    
npt.fillStyle = "rgb(" + r + "," + g + "," + b + ")";
npt.fillRect(3 * i, 0, 3, nap.height);
```
效果图如下：
![show](http://oj171eydn.bkt.clouddn.com/color2.png)
