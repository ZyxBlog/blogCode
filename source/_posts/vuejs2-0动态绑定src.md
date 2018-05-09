---
title: vuejs2.0动态绑定src
date: 2017-06-23 12:47:02
tags:
- vuejs
categories:
- 前端
---
在使用vuejs的情况下,满足图片的src会动态赋值,使图片能切换的需求,首先是将src变为:src,并在data中设置一个全局函数imgSrc,就像原本一样将img引用的相对路径’../../../path’这种形式,没想到图片没有显示出来.
问题出在哪里,我觉得很明显是路径的问题.但原因在于何处,我觉得首先webpack是没有编译路径的,还是保持相对路径的状态,因此出现错误.
解决方法:
```bash
data() {  
    return {       
        imgSrc: require('../../../path')
    }
}
```
就可以实现了.
