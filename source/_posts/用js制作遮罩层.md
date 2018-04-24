---
title: 用js制作遮罩层
date: 2016-11-17 16:43:17
tags:
- js
categories:
- 前端
---

之前也看过别人写遮罩层,有的是在js里面写html然后用append插入html,考虑到性能问题,我选择了一种简单的单纯控制显示与隐藏已经存在的元素.

### 静态配置

先将静态html和css配好，由于遮罩层先写入了html所以不是太简洁明了

#### html
![code](http://oj171eydn.bkt.clouddn.com/whole.png)

#### css
```bash
<style type="text/css">  
    html,body {     
        padding: 0;
        margin: 0;
    }
    #whole {
        z-index:10;
    }
    #header {  
        width:100%;   
        height:50px;
        background-color:rgb(57, 57, 57);
    }
    #login {
        color: #FFFFFF;
        margin-left: 94%;   
        padding-top: 11px;   
        cursor: pointer;
    }
    img {  
        width:100%;   
        float: left;
    }
    #ceng {   
        width:100%;   
        height:100%;   
        position:fixed;   
        top:0;   
        left:0;   
        z-index: 20;   
        background-color: rgb(97, 99, 97);   
        opacity: 0.75;   
        filter:alpha(opacity:75);   
        display:none;
    }
    #kuang {  
        width: 350px;   
        height: 380px;   
        background-color: white;   
        position:fixed;   
        top:0;   
        left:0;   
        opacity: 1;   
        filter:alpha(opacity:100);   
        z-index:130;   
        display:none;
    }
    #kuang img {  
        width:100%;   
        height:100%;
    }
</style>
```

在这里我们需要注意：
* 层级问题,层级z-index首先只作用于兄弟节点,如果是父子节点,默认子节点的层级高于父节点,而遮罩层层级高于背景图,因此z-index要大一些
* 透明度的问题,由于ie和火狐浏览器对透明度的兼容性不同,因此我们需要这样写
```bash
opacity: 0.75;       // Firefox, Safari(WebKit), Opera
filter:alpha(opacity:75);     // IE
```
* 对中间登陆框的定位,我们用js计算后定位

### js code
js代码主要实现计算和控制动态定位
![code](http://oj171eydn.bkt.clouddn.com/show5.png)
![code](http://oj171eydn.bkt.clouddn.com/show6.png)
