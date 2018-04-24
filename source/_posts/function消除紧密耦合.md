---
title: function消除紧密耦合
date: 2016-10-24 10:34:30
tags:
- js
categories:
- 前端
---

### callee()和caller()的用法
* obj.callee()是指向拥有obj这个对象的函数
* .caller()指向被调用的函数
在实现阶乘的时候我们有时会这样编码:
```bash
function cheng(num) {
    if (num <= 1) {
        return 1
    } else {
        return num*cheng(num-1);
}
```
这种函数名和函数执行耦合太紧密,为了避免这种问题,我们经常会这样:
```bash
function cheng(num) {
    if (num <= 1) {
        return 1;
    } else {
        return num*arguments.callee(num-1);
    }
}
成功解决耦合紧密的问题.
同样如下:
```bash
function out() {  
    inn();
}
function inn() {  
    alert(arguments.callee.caller)
}
out()      // caller指向out()
```
