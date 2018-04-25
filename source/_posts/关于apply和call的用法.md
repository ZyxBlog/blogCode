---
title: 关于apply和call的用法
date: 2017-01-04 12:13:08
tags:
- js
categories:
- 前端
---

对于自己的理解apply和call,在用途方面,一方面是传递参数,另一方面是扩充函数作用域
### 传递函数:
```bash
function sum(num1, num2) {
    return num1 + num2;
}
function sum1(num1, num2) {  
    return sum.apply(this,[num1,num2]);
}
function sum2(num1,num2){  
    return sum.apply(this,arguments);
}
function sum3(num1,num2){  
    return sum.call(this,num1,num2);
}
alert(sum1(1,1));    //2  
alert(sum2(1,1));    //2
alert(sum3(1,1));    //2
```
两者区别在于接受参数的方式不同,apply不像call除第一个this外,后面的参数要逐个列举出来.

### 扩充函数作用域
```bash
window.name = "Tom";
var a = {  
    name:'Jerry'
}
function na(){  
    alert(this.name);
}
na();
na.call(this);      
Tomna.call(window);    
Tomna.call(a);    //Jerry
