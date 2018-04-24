---
title: html5实现拖拽功能
date: 2016-11-12 19:42:36
tags:
- js
categories:
- 前端
---

### 静态文件
```bash
<div id="drag" ondrop="drop(event)" ondragover="allowDrop(event)">
    <img src="../img/pic13.jpg" alt="图片" draggable="true" id="pic" ondragstart="drag(event)">
</div>
<div id="loc" ondrop="drop(event)" ondragover="allowDrop(event)"></div>
```

```bash
<style type="text/css">
#drag {
    width: 100px;
    height:100px;
    border:1px solid blue;
    float:left;
}
#loc{    
    margin-left: 120px;
    width:100px;
    height:100px;
    border:1px solid black;
}
img{
    width:100px;   
    height:100px;
}

</style>
```

* 1.设置图片为可拖拽,draggable=”true”
* 2.ondragstart=”drag(event)”,设置拖动的数据,event传递事件,setData()设置拖动值和类型
* 3.ondragover=”allowDrop(event)”放置的位置
* 4.ondrop=”drop(event)”进行放置

### js
```bash
<script type="text/javascript">
    function drag(e) {  
        e.dataTransfer.setData("text", e.target.id);       //设置类型为文本,值为e.target.id
    }
    function allowDrop(e) {
        e.preventDefault();         //取消事件默认动作
    }  
    function drop(e) {
        e.preventDefault();
        var dat = e.dataTransfer.getData("text");
        e.target.appendChild(document.getElementById(dat));  //将图片放进框里
    }
</script>
```

### 效果图
![show](http://oj171eydn.bkt.clouddn.com/show15.png)
![show](http://oj171eydn.bkt.clouddn.com/show16.png)
