---
title: js对数组排序
date: 2017-01-05 18:13:19
tags:
- js
categories:
- 前端
---
### 升序排列
```bash
var a  = [0,1,5,25,9,18];
function com(val1, val2) {  
    if(val1 < val2) {    
        return -1;  
    } else if(val1 == val2) {    
        return 0;  
    } else {    
        return 1;  
    }
}
var b = a.sort(com);
console.log(b);     // 输出为: 0,1,5,9,18,25
```

### 降序排序
```bash
var a  = [0,1,5,25,9,18];
function com(val1, val2) {  
    if(val1 < val2) {    
        return 1;  
    } else if(val1 == val2) {    
        return 0;  
    } else {    
        return -1;  
    }
}
var b = a.sort(com);
console.log(b);  // 输出为:25,18,9,5,1,0
在这里.sort()主要是实现重排序,但不会实现升序,只会将上述排成0,1,18,25,5,9,因此我们需要底下的com(),用的主要是冒泡方法,将其实现排序.
