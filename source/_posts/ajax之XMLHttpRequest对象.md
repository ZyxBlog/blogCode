---
title: ajax之XMLHttpRequest对象
date: 2017-02-20 11:01:40
tags:
- js
categories:
- 前端
---

平时写项目用jquery里面$.ajax()和$.post()和$.get()用的比较多，因此用原生写ajax比较少。

首先创建XMLHttpRequest对象
```bash
var xmlhttp;
if (window.XMLHttpRequest) {  
    xmlhttp = new XMLHttpRequest();
} else if(window.ActiveXObject) {  
    xmlhttp = new ActiveXObject("Microsoft.XMLHTTP");
}
if (xmlhttp != null) {  
    xmlhttp.onreadystatechange = statechange;  
    xmlhttp.open('POST/GET', url, true);  
    xmlhttp.send(null);
} else {  
    alert('error');
}
function statechange() {  
    if(xmlhttp.readyState == 4) {    
        if (xmlhttp.status == 200) {      
            alert("通讯success");    
        } else {      
            alert("fail");    
        }  
    }
}
```
