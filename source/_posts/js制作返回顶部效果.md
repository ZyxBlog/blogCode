---
title: js制作返回顶部效果
date: 2016-10-30 10:35:50
tags:
- js
categories:
- 前端
---

### html
首先返回顶部需要搭建好静态页面
![静态html](http://oj171eydn.bkt.clouddn.com/show2.png)

### css
```bash
<style type="text/css">  
    html,body {
        padding:0;
        margin: 0;
    }
    #back{   
        width:1000px;
        height: 3377px;
        margin:0 auto;
        background-color: #e0e0e0;
    }
    #back img{
        width:1000px;
        float:left;
    }
    #top{  
        width:50px;
        height: 50px;
        margin-left: 1010px;
        background: url(../img/back.png);
        background-size:cover;
        position:fixed;
        bottom: 20px;
        cursor:pointer;
        display:none;
    }
    #top img{
        width:50px;
    }
    </style>
```

在这里我们主要需要注意对返回顶部图标的定位,用fixed,固定于屏幕上的某处.

### main js
首先返回顶部有三个阶段,页面加载完成后的阶段,点击返回顶部返回的阶段,最后是在手动滚动阶段.

#### 所需变量
```bash
window.onload = function() {
    var top = document.getElementById("top");
    var showTop = document.documentElement.clientHeight;   //获取可视区的高度
    var timer = null;
    var control = true;   //设置布尔值,判断是否到达顶部
}
```

#### 触发事件
```bash
top.onclick = function() {
    timer = setInterval(function() {
        control = true;
        var h = document.documentElement.scrollTop||document.body.scrollTop;   document.documentElement.scrollTop = document.body.scrollTop = h + Math.floor(-h/10);
        if (h <= 0) {      
            clearInterval(timer);    
        }  
    }, 50);
}
```

设置定时器,每50ms执行一次,h则表示滚动卷离顶部的高度,在这里由于ie,Google浏览器的兼容问题.
我们需要用document.documentElement.scrollTop||document.body.scrollTop;
也或者用document.documentElement.scrollTop+document.body.scrollTop;都可以,下面主要就是实现返回顶部这个过程,我们一面避免兼容性的问题将每次的高度赋值给滚动卷离顶部的高度;为了实现由快到慢的过程我们将高度的固定值改为可变值h + Math.floor(-h/10),这里的Math.floor采用向下舍入.最后当滚动卷高度为0时清除定时器.

### 滚动事件
```bash
window.onscroll = function() {
    if(!control) {    
        clearInterval(timer);  
    }  
    control = false;  
    var heig = document.documentElement.scrollTop||document.body.scrollTop;   
    if(heig >= showTop) {    
        top.style.display = "block";  
    } else {    
        top.style.display = "none";  
    }
}
```
当离顶部距离补不为0时,手动滚动清除定时器,最后我们要实现返回顶部图标的实现与隐藏功能,我们已经在css中设置它为隐藏,当滚动卷高度大于可视区的高度,我们才让它出现.则是上面的第二个if语句的判断.

### js code
![code](http://oj171eydn.bkt.clouddn.com/show3.png)

### whole show
![show](http://oj171eydn.bkt.clouddn.com/show4.png)
