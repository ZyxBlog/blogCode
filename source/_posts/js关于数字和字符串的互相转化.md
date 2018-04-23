---
title: js关于数字和字符串的互相转化
date: 2016-08-03 15:11:07
tags:
- js
categories:
- 前端
---

### 将字符串转化成数字的方法
parseInt(),例:parseInt("1234")输出1234。
parseInt("010", 10);  //return 10
parseInt("010", 8);  //return 8
parseFloat(),是将字符串转化成浮点型的数字
Number(value)强制转化成数字

### 将数字串转化字符串的方法
String(value)将给定值强制转成字符串
.toString()将给定值转化成字符串

```bash
var a = 10;
var b = a.toString();console.log(typeof b);       //将输出b的类型string
```
当数字和字符串相加时,最后结果是字符串类型
