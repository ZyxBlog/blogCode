---
title: js数组去重
date: 2016-12-18 13:45:06
tags:
- js
categories:
- 前端
- 算法
---

最近在看前端笔试题的时候遇到这样一道题,用js去除数组中重复的元素,自己也思考了一下.
大致思路是这样的:一个数组a和一个空数组b,先将a[0]添加到b中,然后从a[1]到a[i]遍历,如果在b中能找到a[i]则跳过,如果不能则将a[i]添加进b.
具体代码如下：
```bash
<script type="text/javascript">  
    var a = [2,3,4,2,3,4,5,0,8,7,0,8];  
    var b = [];  b.push(a[0]);  
    for(var i = 1; i < a.length; i++) {    
        if(b.indexOf(a[i]) == -1) {      
            b.push(a[i]);   
        }
    }
    console.log(b);
</script>
```
我们打开浏览器的控制台我们可以看到:
![show](http://oj171eydn.bkt.clouddn.com/show12.png)
正确！
