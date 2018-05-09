---
title: js打乱数组
date: 2017-02-07 10:51:44
tags:
- js
categories:
- 前端
---

这里主要是考察对js数组的排序，第一想法是需要用到.sort()这个属性，已知，当.sort()用于比较时:

* 若 a 小于 b，在排序后的数组中 a 应该出现在 b 之前，则返回一个小于 0 的值。
* 若 a 等于 b，则返回 0。
* 若 a 大于 b，则返回一个大于 0 的值。

因此，思路是先生成一个数组，然后基于打乱，肯定要用到Math.random()这个方法。
```bash
<script type="text/javascript">  
    window.onload = function() {    
        var arr = [];    
        for (var i = 0; i < 10; i++) {      
            arr[i] = i;   
        }    
        console.log(arr)    
        arr.sort(function() {      
            return 0.5 - Math.random();    
        });    var str = arr.join();    
        console.log(str)  
    }
</script>
```
这样便较为快速的实现了。
