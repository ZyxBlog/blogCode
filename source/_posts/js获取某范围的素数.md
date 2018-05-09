---
title: js获取某范围的素数
date: 2017-03-02 11:31:42
tags:
- js
categories:
- 前端
---

js获取某范围之内的素数，思考过程：素数的性质，只能整除1和自己本身的数，自然数的范围内，0和1要去除。
然后一般筛选数据，由于不知道具体范围，我可以用传参的思想,最后返回一个筛选出来的数组。
```bash
var prime = function(leng) {  
    var arr = [];  
    var i,j;  
    for(i = 1; i < leng; i++) {    
        for(j = 2; j < i; j++) {       
            if(i % j === 0) {         
                break;       
            }
        }    
        if(i<=j && i!=1 ) {        //考虑到素数里面有2，没有1       
            arr.push(i);   
        }
    }
    return arr;
}
prime(100);     //会筛选出100以内的素数
```
