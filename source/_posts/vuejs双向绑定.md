---
title: vuejs双向绑定
date: 2017-05-14 12:19:51
tags:
- vuejs
categories:
- 前端
---
自vuejs从1.0到2.0完成迁移后，很多用法都被遗弃或者修改，之前傻乎乎的用vuejs2.0写动画，用到transition=”name”,后来发现被遗弃了，变成了<transtion name=""><transtion></transtion></transtion>
不过我觉得最坑的还是vuejs中对props的改变。之前vuejs1.0里面props是双向流，现在是单向流，官方解释————防止子组件无意修改了父组件的状态——这会让应用的数据流难以理解。
如今的props内的数据变成只可读不可写，然而我们还是需要从子组件向父组件进行数据传递。
首先可以用最原始的方法，在子组件内部$emit(“event”, value)将数据派发到父组件，然后父组件进行在子组件上绑定这个事件<child @event="methods"><child>,然后在methods里面添加这个方法，来实现子组件向父组件传递数据。</child></child>
但是当数据多的时候会发现很多没有营养的代码，例如：
```bash
...
methods: {    
    a: function(data) {      this.num1 = data;    },    
    b: function(data) {      this.num2 = data;    },    
    c: function(data) {      this.num3 = data;    }}
...
```
这样显而易见其实是不好的，当然也可以用其他方法，比如引入vuex库，将需要通信的数据全部变成全局变量。
但如果这种数据也不是特别多的时候，也没必要引入这么大一个库。
还有一种我觉得比较合适的，就是用v-model和props加data实现双向绑定。
首先可能有人会有疑问v-model大多数用于表单，例如input,select,textarea等等，但是通过外表看里面的代码，其实是这样的
v-model就是:value = "content";
@input = "content = $event.target.value"

因此v-model是v-bind和v-on的语法糖
所以可以在父组件上v-model一个封装后的content，然后用子组件去用props接受一个value值，考虑到props是可读不可写，因此我们需要用data，就把props里面的数据直接赋值给data里面的数据，因为data里面是可写的，因此监听data里面的数据，再把data里面的数据emit派发到父组件上，this.$emit(‘input’, content)，这样就实现了双向绑定，也避免了那段没有营养的代码。
