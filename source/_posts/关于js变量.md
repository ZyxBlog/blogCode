---
title: 关于js变量
date: 2016-12-22 12:46:29
tags:
- js
categories:
- 前端
---

### js在闭包里面的局部变量和全局变量
```bash
(function() {  
    var a = b = 1;
})();
console.log(a);
console.log(b);
```
来看一下结果
![show](http://oj171eydn.bkt.clouddn.com/show14.png)

分析一下结果:在闭包域内由于var a里面的a为局部变量,因此无法暴露出来,a为a is not defined,但是b为什么有值?b有值说明此时b为全部变量,在函数中只是把1赋值给b,b再赋值给a,而只var了a,没有var b,所有b为全局变量.
