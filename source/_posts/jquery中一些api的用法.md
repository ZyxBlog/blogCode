---
title: jquery中一些api的用法
date: 2016-10-08 10:32:26
tags:
- jquery
- js
categories:
- 前端
---

### find和children
关于$.find()和$.children()的区别，在遍历DOM节点时,我们经常需要寻找子节点,那在jquery中比较常用的两种遍历方法$.find()和$.children().
通过children获取的是该元素的下级元素，而通过find获取的是该元素的下级所有元素.这时回到上面，我们可以得出，$("#tb>tbody").children() 获取的是两个tr元素（不包括它们子元素td)
而children里面的选择器则是在获取的两个tr元素里再根据条件进行筛选，所以上面那种写法获取不到值。

### index
关于查找索引值index的用法———$.index()
```bash
<ul>
    <li id="num1">num1</li>
    <li id="num2">num2</li>
    <li id="num3">num3</li>
</ul>

$('li').index(document.getElementById('num2')); // 传递一个DOM对象，返回这个对象在原先集合中的索引位置
$('li').index($('#num2'));   // 传递一个jQuery对象
$('li').index($('li:gt(0)'));  // 传递一组jQuery对象，返回这个对象中第一个元素在原先集合中的索引位置
$('#num2').index('li');  // 传递一个选择器，返回#num2在所有li中的做引位置
$('#num2').index(); //不传递参数，返回这个元素在同辈中的索引位置。  
```
