---
title: js筛选奇数和偶数
date: 2016-11-25 16:44:34
tags:
- js
categories:
- 前端
---

创建两个空数组,利用循环挨个判断.
```bash
<script type="text/javascript">  
    var a = [2,4,9,12,44,5,13,19];
    var b = [];
    var c = [];
    for (var i = 0; i < a.length; i++) {    
        (a[i] % 2 == 0) ? b.push(a[i]) : c.push(a[i]);
    }
    console.log("偶数是:" + b);
    console.log("奇数是:" + c);
</script>
```
输入为:
![output](http://oj171eydn.bkt.clouddn.com/jisuan.png)
