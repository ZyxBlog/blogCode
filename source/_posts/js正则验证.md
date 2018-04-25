---
title: js正则验证
date: 2017-01-07 21:43:27
tags:
- js
categories:
- 前端
---
### 正则验证手机号码
由于现在大部分是13*,15*,18*开头的,我们采用如下验证:
```bash
<body>  
    <span>电话号码:</span>  
    <input type="text" id="tel" value=""/>  
    <button type="button" name="button" id="tijiao">提交</button>
</body>
<script type</span>="text/javascript">    
    var reg = /^(((13[0-9]{1}|(15)[0-9]{1}|(18)[0-9]))+\d{8})$/;    document.getElementById("tijiao".onclick = function() {      
        var tel = document.getElementById("tel").value;      
        if(reg.test(tel)) {       
            alert("格式正确");      
        } else {       
            alert("格式不正确");    
        }
    }  
</script>
```
![show](http://oj171eydn.bkt.clouddn.com/zhengze1.png)
![output](http://oj171eydn.bkt.clouddn.com/zhengze2.png)

### 验证邮箱地址
首先了解邮箱格式xxx@xx.xxx
```bash
<body>
    <span>邮箱:</span>
    <input type="text" id="mail" />
    <button type="button" name="button" id="tijiao">提交</button>  
</body>
<script type="text/javascript">   
    var reg = /^([a-zA-Z0-9_-])+@([a-zA-Z0-9_-])+((\.[a-zA-Z0-9_-]&{2,3}){1,2})$/;    document.getElementById("tijiao").onclick = function(){      
        var mail = document.getElementById("mail").value;      
        console.log(mail);      
        if(reg.test(mail)){        
            alert("格式正确");      
        } else {       
            alert("格式不正确");      
        }    
    }  
</script>
```
前面是字母或者数字,后面接@加字母或者数字,然后是.net,.com诸如此类但是点后面的字母设置长度为2-3个,最后这种.xx的形式可以一到两个,例如.com.cn
![show](http://oj171eydn.bkt.clouddn.com/zhengze3.png)
![show](http://oj171eydn.bkt.clouddn.com/zhengze4.png)
