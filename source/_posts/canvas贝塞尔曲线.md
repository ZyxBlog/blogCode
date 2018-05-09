---
title: canvas贝塞尔曲线
date: 2017-10-02 13:32:07
tags:
- html5
categories:
- 前端
---

### 实现用贝塞尔曲线画一个气泡

#### html部分
```bash
<canvas id="canvas" width="300" height="300" width="300" style="border: 1px dashed #808080"></canvas>
```
#### js部分
```bash
function $$ (id) {  
    return document.getElementById(id)
}
window.onload = function () {  
    var can = $$('canvas')  
    var cxt = can.getContext('2d')  
    cxt.moveTo(75, 25)  
    cxt.quadraticCurveTo(25, 25, 25, 62)  
    cxt.quadraticCurveTo(25, 100, 50, 100)  
    cxt.quadraticCurveTo(50, 120, 30, 125)  
    cxt.quadraticCurveTo(60, 120, 65, 100)  
    cxt.quadraticCurveTo(125, 100, 125, 62)  
    cxt.quadraticCurveTo(125, 25, 75, 25)  
    cxt.strokeStyle = 'blue'  
    cxt.stroke()
}
```
气泡就这么画出来了
![show](http://oj171eydn.bkt.clouddn.com/qipao.png)
