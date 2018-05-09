---
title: 异步操作promise的回调
date: 2017-04-22 20:00:31
tags:
- ES6
categories:
- 前端
---
为实现一个发帖功能，里面需要上传网络视频，考虑到性能问题使用异步操作，决定ES6中的promise来实现，方式是用Promise.resolve().then()来实现。
resolve参数里面是函数返回的视频接口的一个对象，但是问题出在在状态变为resolve之后，.then这个方法并没有接受到返回的参数。因此测试一直不成功。
重新阅读ES6中的promise文档发现只要resolve中有返回值，then就能接受到。而且一般问题是出在.then().then()这种嵌套型的写法中。
在确认resolve最后return之前数据都是存在的，但是在then的时候接受不到，因此确定是返回值，没有获取到。
由于resolve中嵌套函数比较多，只好一一查看，在最外层和最内层函数都有return，就往里面查看，果然在调用一个api接口的函数时，没有return这个函数。
在添加return后，then里面的不再是undefined。
以后面对层层函数嵌套，而且promise不太熟的情况下，还是要多多注意。
