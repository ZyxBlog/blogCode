---
title: 关于js的小问题
date: 2016-12-20 07:46:11
tags:
- js
categories:
- 前端
---

今天遇到这样一道js题目,是这样的:
```bash
<script type=text/javascript>  
    var a = 1;  
    (function() {    
        console.log(a);    
        var a = 2;    
        console.log(a);
    })();
</script>
```
问两次输出是什么?
一开始我以为这道题是考察局部变量和全局变量,分别输出1,2
但事实上并不是,最后输出为undefined和2,在网上百度之后才发现并不是这样,因为其实上式等同于
```bash
var a = 1;
(function() {  
    var a;  
    console.log(a);  
    var a = 2;  
    console.log(a);
})();
```
在函数里面a在等于1之后又赋值给2,但是在a=2之前,函数是处于声明了未赋值的状态,因此为undefined.
函数声明和变量声明会引擎式的提升到当前作用域的顶部,但是只提升名称不会提升赋值.
