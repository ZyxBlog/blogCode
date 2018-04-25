---
title: js制作Tooltip标签
date: 2016-12-01 12:31:18
tags:
- js
categories:
- 前端
---

制作Tooltip标签首先是鼠标移入,然后显示标签栏,移出后然后标签消失.

### 静态文件
#### html
```bash
<div id="topic">
    <h1>原生Javascript实现Tooltip效果</h1>  
    <p>Tooltip效果是非常常见的特效,它可以在用户将指针放置在控件上时为用户显示提示信息,比如简称文字显示一行文字全称时,例:
        <a class="tooltip" id="tool1">中国</a>,<a class="tooltip" id="tool2">NBA</a>.又比如显示一段文字,例:唐诗三百首中的    
        <a class="tooltip" id="tool3">春晓</a>.这就是Tooltip的提示.
    </p>  
    <p>Tooltip效果还可以用来显示图片,例:
        <a class="tooltip" id="tool4">;西湖美景</a>.  
    </p>  
    <p>甚至可以显示一整个网站:例
        <a class="tooltip" id="tool5">百度</a>  
    </p>  
    <p>这就是Tooltip效果.
</div>
```

#### css
我们要给需要释义的词统一好样式,设置类名为”tooltip”
```bash
<style type="text/css">  
html,body {    
    padding:0;    
    margin:0;  
}  
body {    
    background-color: rgb(157, 240, 152);  
}  
#topic {    
    width:500px;    
    height:350px;    
    padding:10px 20px;    
    margin:35px auto;    
    background-color:rgb(235, 232, 233);    
    border:10px solid rgb(249, 197, 160);    
    border-radius: 15px;    
    -moz-border-radius:15px;    
    -webkit-border-radius:15px;  
}  
h1 {    
    color:blue;  
}  
.tooltip {    
    color: rgb(224, 30, 24);    
    cursor:help;  
}  
.tip {    
    background-color: #fff;    
    display: block;    
    border:1px solid rgb(34, 242, 242);    
    color:#333;    
    line-height: 1.6;    
    padding: 20px;    
    font-size: 12px;    
    border-radius:5px;    
    -moz-border-radius:5px;    
    -webkit-border-radius:5px;    
    overflow:auto;  }
</style>
```

在里面我们需要注意如下几点:
* 一是css3中对圆角的设置border-radius,官方上解决兼容性是这样的-moz-border-radius和-webkit-border-radius
* 二是虽然现在还没有.tip,因为我们在后面会动态添加节点元素.

### 动态脚本
由于tooltip有多个标签,所以为了精简代码,我们主要思路是传递参数.
```bash
<script type="text/javascript">    
    var isIE = navigator.userAgent.indexOf("MSIE")>-1;    
    function tool(origin, id, html, width, height) {      
        if(document.getElementById(id) == null) {        
            var node;        
            ori = document.getElementById(origin);        
            node = document.createElement("div");        
            node.id = id;        
            node.className = "tip";        
            node.innerHTML = html;        
            node.style.width = width?width+"px":"auto";       //ie浏览器        
            node.style.height = height?height+"px":"auto";        
            if(!width &amp;&amp; isIE) {          
                node.style.width = node.offsetWidth;        
                node.style.position = "absolute";        
                node.style.display = "block";        
                node.style.left = ori.offsetLeft+"px";        
                node.style.top = ori.offsetTop+20+"px";        
                ori.appendChild(node);        
                ori.onmouseleave = function() {          
                    setTimeout(function() {            
                        document.getElementById(id).style.display = "none";          
                    }, 1000);        
                }     
            } else {        
                document.getElementById(id).style.display = "block";      
            }    
        }    
        /********中国********/    
        document.getElementById("tool1").onmouseenter = function() {      
            tool("tool1","to1","中华人民共和国",100,30);    
        }
    }
</script>
```            

该函数tool(),主要传递5个参数,第一个是触发源,第二个是创建节点的id,第三个是里面的html,这里可以是文字,可以是有格式的诗歌,可以是图片,也可以是网页.形式大致是这样的
```bash
<div class="tip" id="id">xxx</div>
```
其中需要注意的如下:
* auto这个不适用与IE的兼容性,因此在开头用navigator.userAgent.indexOf(“MISE”)>-1验证IE浏览器.
* 同时为了让标签摆在合适的位置,我设置了position为absolute,display为block.
* 如果不传递宽高参数,那设置为auto;
* offset后的Left或者Top,是相对于版面或者是父坐标的位置,在这里的很显然是相对于父元素的位置,然后赋值给出来标签的位置.

效果图
![show](http://oj171eydn.bkt.clouddn.com/show7.png)
