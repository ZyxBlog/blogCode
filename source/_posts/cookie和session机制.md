---
title: cookie和session机制
date: 2017-02-16 19:07:53
tags:
- html5
categories:
- 前端
---

首先cookie和session是干什么的？cookie和session是会话跟踪的技术。Cookie通过在客户端记录信息确定用户身份，Session通过在服务器端记录信息确定用户身份。
而javascript是运行在客户端的脚本，因此一般只能够设置cookie，而不能设置session
### 设置Cookie
```bash
function setCookie(name,value) {  
    var Days = 30;  
    var exp = new Date();  
    exp.setTime(exp.getTime() + Days*24*60*60*1000);  
    document.cookie = name + '=' + escape(value) + ';expires=' + exp.toGMTString();
}
```

### 读取Cookie
```bash
function getCookie(name) {  
    var arr;  
    var reg = new RegExp('(^|)'+name+'=([^;]*)(;|$)'); //正则匹配  //^|匹配开头，；$|匹配$加结尾，中间是name加上非;的0-多个字符  
    if (arr = document.cookie.match(reg)) {    
        return unescape(arr[2]);  
    } else {    
        return null;  
    }
}
```

### 删除cookie
function delCookie(name) {  
    var exp = new Date();  
    exp.setTime(exp.getTime()-1);  
    var del = getCookie(name);  
    if(del != null) {    
        document.cookie = name+'='+del+'expires='+exp.toGMTString();  
    }
}
