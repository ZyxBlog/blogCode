---
title: js关于number操作
date: 2016-12-24 12:46:52
tags:
- js
categories:
- 前端
---
今天在书上看到这样一个题目很有趣,题目是这样的:
```bash
console.log(0.1+0.2);            //0.30000000000000004
console.log(0.1+0.2==0.3);     //false
```

这样的原因是什么,如果计何得0.3，因为number类型是浮点型,计算的时候会先被转成二进制数,再计算,双精度浮点数的小数部分最多支持52位,最后转化成十进制的数,就变成最后的答案.
我的思考是设置小数位数,用.toFixed()这个方法.
```bash
function add(x,y) {  
    var t = x + y;
    var m = t.toFixed(1);  
    alert(m);
}
add(0.2, 0.1);
```
最后输出:
![output](http://oj171eydn.bkt.clouddn.com/math.png)
