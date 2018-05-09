---
title: CMD和AMD
date: 2017-02-27 14:46:39
tags:
- js
categories:
- 前端
---

关于模块化规范，CMD规范和AMD规范，两者的区别是什么。
* CMD是（Common Module Definition）为通用模块定义。
* AMD是（Asynchronous Module Definition）为异步模块定义。
### CMD
```bash
define(function(require,exports,module) {  
    var $ = require("jquery.js");     //引入依赖  
    module.exports = {    //code  }
});
```

### AMD
```bash
define(['dependency'], fucntion(){   //引入依赖    
    //code                 
});
```
从编程方式来看CMD主要是在需要依赖的时候引入依赖，而AMD是在一开始就把所有的依赖关系引完。
因此区别在于对依赖模块的的执行时机处理不同。
