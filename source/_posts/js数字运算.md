---
title: js数字运算
date: 2016-08-29 17:23:42
tags:
- js
categories:
- 前端
---

一般来说,在js的数字运算里,我们需要注意以下几点:
* 对于普通的整数运算,我们不需要纠结太多但是小数运算需要格外注意,例:0.05+0.25和-0.15+0.15都等于实际运算值,但是0.1+0.2输出则不为0.3而是0.300000000004,这是由于二进制转化的缘故.
* 当出现非数字时,例如:4-false是为4,因为false转化成了0;4-null也为4,因为null转化成了0;4-''也为4,因为''也转化成了0.
* 关于加减,例4-'2'输出2,因为'2'转化成了2,我们用typeof可以发现结果是数字类型,但是如果我们用加号的话,结果则为字符串类型,而乘除结果则都是数字类型.
