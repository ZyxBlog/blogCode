---
title: localStorage和sessionStorage
date: 2016-12-04 18:15:20
tags:
- html5
categories:
- 前端
---

众所周知,存储数据一直都是cookie来实现的,但是cookie不适合存储大量的数据,由于它是对于每个服务器来传递的,因此执行速度慢,而且效率低。
在html5属性里localStorage和sessionStorage则无须服务器就可以存储大大提高了效率,但他们只能存储字符串类型的对象,下面分析一下两者区别:
localStorage.username=”zyx”,生命周期是永久,除非在浏览器UI上手动删除,不然将会永远存在.同时它是全局变量,我是在ajax里面添加的.
对于有登陆页面的网站,在登陆页面的ajax,例:
```bash
$.ajax({  
    dataType: 'json',  
    type: '',  
    data: {},  
    success: function(data) {    
        if(data.status == '200') {                //登陆成功,则实现存储      
            localStorage.username='';               
            localStorage.password='';    
        }
    }
})
```

* sessionStorage生命周期为当前窗口或标签页，一旦窗口或标签页被永久关闭了，那么所有通过sessionStorage存储的数据也就被清空了。
* 不同浏览器无法共享localStorage或sessionStorage中的信息。相同浏览器的不同页面间可以共享相同的localStorage（页面属于相同域名和端口），但是不同页面或标签页间无法共享sessionStorage的信息。一个标签页包含多个iframe标签且他们属于同源页面，那么他们之间是可以共享sessionStorage的。
* 如果是清除的话,则用localStorage.removeItem('a')删除名称为'a'的信息;localStorage.clear()为清除所有信息。
