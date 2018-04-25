---
title: jquery制作简单的展开收起效果
date: 2016-12-08 09:38:56
tags:
- jquery
categories:
- 前端
---

这个展开与收起的效果还是挺简单的,首先配置静态文件
### 静态文件
```
<div id="pn">   
    <p>手机商品筛选</p>   
    <p>网络:移动4G 联通3G 电信3G</p>   
    <div id="hpn" style="display:none;">     
    <p>家回个500以上</p>     
    <p>特点防水  长待  10000000000</p>     
    <p>家回个500以上</p>     
    <p>特点防水  长待  10000000000</p>     
    <p>家回个500以上</p>     
    <p>特点防水  长待  10000000000</p>   
    <p class="slide">   
        <a href="#" id="strHref" class="btn-slide">更多选项</a>
    </p>
</div>
```

### css样式
```bash
<style type="text/css">
    body {  
        margin:0 auto;  
        padding:0px;
    }
    #pn {  
        background-color: #e8e8e8;  
        width: 600px;  
        display: block;  
        margin: 0 auto;  
        padding:5px;  
        font-size:9px;  
        height:auto;
    }
    .slide {  
        margin:0 auto;  
        padding:0px;  
        width:600px;  
        border-top:solid 4px gray;
    }
    .btn-slide {  
        background-color: gray;  
        height: 30px;  
        width: 120px;  
        text-align: center;  
        margin: 0 auto;  
        display: block;  
        color: #fff;  
        text-decoration:none;
}
</style>
```

### jquery实现功能
```bash
$(document).ready(function(){  
    $("#strHref").click(function() {   
        if($("#hpn")[0].style.display == "none") {     //$()选择器选择的是一个集合,而操作是元素      
            $(".btn-slide").html("收起");      
            $("#hpn").show(1000);    
        } else {      
            $(".btn-slide").html("更多选项");      
            $("#hpn").hide(1000);    
        }  
    });
});
```

### 效果图
![show](http://oj171eydn.bkt.clouddn.com/show11.png)
我们发现jquery中的show(1000)和hide(1000),我们能看出一些动画的效果,如果用js实现功能,那么一般是用display和setInterval合在一起,这时我们能发现效果显得很生涩,不流畅,因此如果要用原生js做的话.我们需要用到css3的新属性实现动画.
