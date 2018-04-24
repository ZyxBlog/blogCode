---
title: js铺满全屏
date: 2016-09-15 12:44:09
tags:
- css
- js
categories:
- 前端
---

### css实现
设置padding-margin为0, 然后设置body, html长宽为100%
```bash
body,html {  
    padding: 0;
    margin: 0;
    width: 100%;
    height: 100%;
    background-color: pink;
}
```

### js实现
当body里面有个div,在不操作body的情况下,设置div宽高,使它铺满屏幕,
* 首先css
```bash
body,html {  
    padding: 0;
    margin: 0;
}

#whole {
    background-color: blue;
}
```

首先在这里设置div宽高百分百是没有用的,因为父元素body没有宽度,所以设置百分百最后是不能实现的.
我们可以这样用js实现:
```bash
<script type="text/javascript">
    var whole = document.getElementById('whole');
    var h = document.documentElement.clientHeight;
    var w = document.documentElement.clientWidth;
    whole.style.height = h + 'px';
    whole.style.width = w + 'px';
    window.onresize = function() {
        h = document.documentElement.clientHeight;    
        w = document.documentElement.clientWidth;
        whole.style.height = h + 'px';
        whole.style.width = w + 'px';
    };
</script>

clientHeight和clientWidth是可视区的高和宽,但是如果屏幕缩放会出现留白或者滚动条,因此当window.onresize时触发事件,重新赋值铺满,这样就可以了
