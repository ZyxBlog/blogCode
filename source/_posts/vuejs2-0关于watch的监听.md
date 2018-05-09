---
title: vuejs2.0关于watch的监听
date: 2017-06-14 19:46:33
tags:
- vuejs
categories:
- 前端
---
要求实现一个子组件与父组件之间传递一个提示框的基本信息,在使用v-model和props实现双向绑定时,用watch监听接受的对象,然而console也没有报错,说明语法逻辑是没有问题,对此我觉得应该是对vm.$watch的理解出现偏差,重新查看了文档,发现只能监听expression和function.于是我选择监听对象其中一个值,由于两个值是同时改变的,我将监听的值放在后一个,然后$emit出去(但其实这样是有问题的,因为对象里面有两个参数,监听一个,如果写法上,监听的值放在前面,那么是错误的).但是就在上面的情况,$emit时候还是报错,console显示$emit未定义.这就说明this没有$emit这个属性.
说明this有问题,console后,this是undefined,再次查看在watch的用法一栏,我注意到底下有一条关于arrow的小字:
Note that you should not use an arrow function to define a watcher (e.g. searchQuery: newValue => this.updateAutocomplete(newValue)). The reason is arrow functions bind the parent context, so this will not be the Vue instance as you expect and this.updateAutocomplete will be undefined.
上面指明了监听不应该用到箭头函数,因为箭头函数绑定了父文本,从而改变了this的指向,而此时的this不是vue实例,然后把箭头函数换回了function的写法.
这次没问题.
然后重新思考对对象的处理,用深度监听去监听遍历forEach或者for in循环后面的值,这样就能监听每个值的变化,唯一的就是属性名,需要暂存去找,比较耗时.
最后google了一下,发现尤大推荐做一个row组件,每一个row组件监听自己的对象,
```bash
let that = this;
this.rows.forEach(function(row, i) {    
    that.$watch('rows[' + i + ']',
    function () {},
    { deep: true })
})
```
感觉总体思路差不多,作者的方法对自己的想法做了封装.缺点在于不能获取属性名,只能获取变化值
