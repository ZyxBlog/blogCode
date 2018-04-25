---
title: js以YYYY-MM-DD形式显示日期
date: 2016-12-31 12:47:23
tags:
- js
categories:
- 前端
---

这是一个简单的操作字符串的例子,是这样解决的
```bash
<script type="text/javascript">    
    var date = new Date();    
    Y = date.getFullYear();    
    M = date.getMonth() + 1;    
    if (M < 10) {      
        M = '0'+M;    
    }   
    D = date.getDate();    
    if(D < 10) {      
        D = '0'+D;   
    }   
    console.log(Y+'-'+M+'-'+D);  
</script>
```
首先是获取今天的日期,然后分别获取年月日,注意点在于:
* 月份是从0开始的,需要加一;
* 月份和日期可能是个位数的,我们需要做个判断,如果是个位数,前位添加0;

输出结果:
![output](http://oj171eydn.bkt.clouddn.com/show13.png)
