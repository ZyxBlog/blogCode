---
title: webpack引入zepto报错
date: 2017-05-01 12:19:03
tags:
- webpack
categories:
- 前端
---
这两天入webpack坑，发现还是对webpack不够理解，今天还是webpack的问题，在开发移动端项目的时候，先用了jquery库，主管觉得库太大，用的地方也不多，就直接在项目中删库，然而用ajax交互不得不说jquery比原生的ajax要节约很多代码。
考虑到用jquery库比较大，又是移动端，又需要精简代码，zepto.js成了首选。
然后当前项目建立在webpack+vue的基础上，考虑到和jquery差不多，就按jquery那种方式引了，在入口js里面import $ from “zepto”,在webpack.conf.js中new webpack.ProvidePlugin({$:”zepto”})。
结果报错：Uncaught TypeError: Cannot read property ‘createElement’ of undefined。
感觉是不科学的。
查了以后才发现确实，在webpack中要引入不支持模块化的库是有问题的。
zepto源码只使用了AMD规范的模块导出方法define，没有用common.js规范的module.exports来导出模块。但是貌似没有触及到问题的根源。
如果import $ from “zepto”，通过webpack之后转化的zepto，就是用module.export = factory(global)来获取factory方法返回的对象。
在模块加载的时侯，webpack导入模块module[module].call(module.exports)里面传递的参数来作为闭包的上下文，并运行模块闭包来将暴露的对象加入已加载的模块对象中。
因此对于zepto来说，它初始化的this其实就是module.exports,但是这个module.exports为this空对象。
则factory(global)中的global为空对象，zepto中的window也是空对象。而里面有var document = window.document(结果就是undefined)，所以报错。
解决方法，添加依赖，安装两个loader:exports-loader和script-loader。
```bash
npm install script-loader exports-loader --save-dev
```
script-loader是在import/require模块时，在全局上下文环境中运行一遍模块js文件，不管引入几次，模块只运行一次。
exports-loader是将我们指定的模块js转成纯字符串，并用eval.call()执行，这样执行的作用域就为全局作用域了。
