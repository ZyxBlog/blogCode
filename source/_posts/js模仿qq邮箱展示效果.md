---
title: js模仿qq邮箱展示效果
date: 2016-11-03 16:41:49
tags:
- js
categories:
- 前端
---

其实效果类似于展开与收起效果。

一开始我们还是写好静态文件，并且在两个a标签上添加两个事件

### html模板
```bash
<div id="whole">
    <div id="acticle0">    
        <p class="title">[GitHub] Your password has changed</p>    
        <p class="time">时间:2016年9月23日(星期五) 凌晨3:00 (UTC-07:00 休斯顿、底特律时间)</p>    
        <p>摘要:Hello zyx19960415, We wanted to let you know that your GitHub password was changed.       
        If you did not perform this action, you can recover access by entering 609629767@qq.com into the form at https://github.com/password_reset.To see this and other security events for your account, visit https://github.com/settings/security...<a href="#" onclick="show(this)">展开全文</a></p>  
        <div class="content"> 正文:Hello zyx19960415, We wanted to let you know that your GitHub password was changed. If you did not perform this action, you can recover access by entering 609629767@qq.com into the form at https://github.com/password_reset. To see this and other security events for your account, visit https://github.com/settings/security. If you run into problems, please contact support by visiting https://github.com/contact or replying to this email. Please do not reply to this email with your password. We will never ask for your password, and we strongly discourage you from sharing it with anyone.    
        <div class="shouqi">         
            <a href="#" class="btn" onclick="hide(this)">收起全文</a>
        </div>       
    </div>
</div>
```
### 布置样式
```bash
<style type="text/css">  
    body {
        margin:0;
        padding:0;
        font-size: 9pt;
        line-height: 180%;
    }
    #whole {
        width:750px;
        height:auto;
        background-color: #f8f8f8;
        margin:0 auto;
        padding:5px;
    }
    .title {
        font-weight: bold;
        color:blue;
        font-size: 11px;
    }
    .time {
        color:#ccc;
    }
    .content {
        border: 1px solid #ccc;
        display: none;
        padding: 5px;
    }
    .shouqi {
        text-align: right;
        height:30px;
    }
    .btn {
        width:80px;
        height:20px;
        text-align: center;
        text-decoration: none;
        padding:5px 3px 5px 3px;
        background-color: #f0f0f0;
        border: 1px solid #ccc;
    }
</style>
```
此时效果：
![效果](http://oj171eydn.bkt.clouddn.com/show8.png)

### 动态js脚本
```bash
<script type="text/javascript">    
    function show(num) {
        var a = num.parentNode;
        var b = a.nextSibling;
        if (b.nodeType !=  1) {
            b = b.nextSibling;
        }
        a.style.display = "none";       
        b.style.display = "block";    
    }
    function hide(num) {
        var a = num.parentNode.parentNode;       
        var b = a.previousSibling;
        if (b.nodeType !=  1) {
            b = b.previousSibling;
        }
        a.style.display = "none";       
        b.style.display = "block";    
    }
</script>

### 效果
![show](http://oj171eydn.bkt.clouddn.com/show9.png)


### attention
这个效果还是比较简单的,如果用jquery来写用$.parent(),$.children(),$.siblings()来写会更快一点,<br>但是还是有几点需要注意:
* 首先是传参,将this传入,这里的this表示触发click事件的那个节点元素.
* 操作dom节点有parentNode,previousSibling和nextSibling寻找节点.
* 最关键的是previousSibling和nextSibling的兼容性问题,在某些浏览器下他们找的是空结点,因此我们需要判断一下,是否是元素节点,如果不是则往下面一个节点找,在上面的nodeType!=1就是这样判断的.
