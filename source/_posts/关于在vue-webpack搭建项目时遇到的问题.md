---
title: 关于在vue-webpack搭建项目时遇到的问题
date: 2016-11-07 10:12:17
tags:
- vuejs
- webpack
categories:
- 前端
---
### 总结一些建立项目过程中的坑
由于我构建的是多界面的项目-这里vue-router路由配件就必不可少，首先我们要知道devDependencies和dependencies里面的区别
* devDependencies  里面的插件只用于开发环境，不用于生产环境
* dependencies  是需要发布到生产环境的
然后我们安装vue-router的依赖进devDependencies里面
```bash
npm install vue-router -D
```

在这里遇到问题,所有之后的配置弄好后main.js里面
![code](http://oj171eydn.bkt.clouddn.com/chengxutu.jpg)

发现页面渲染不出来,控制台报错,意思是.map不符合语法规范,百度后找到了问题所在,原来刚才安装vue-router的依赖版本是”vue-router”:”^2.1.1”,而这个是vuejs2.0的依赖,在2.0里面已经不用.map了,于是重新安装依赖用vuejs1.0的”vue-router”:”^0.7.13”,我们将这句话写入package.json,然后
```bash
npm install
```

成功!

### vue-router如何渲染进页面
我们除了在main.js配置路由,还需要在index.html中app.vue里面添加
```bash
<template><router-view></router-view></template>
这样就渲染出页面了!
```

### 端口占用
当8080端口正在启用时，显然是改端口,在哪里改,可以在webpack.config.js里面的
![code](http://oj171eydn.bkt.clouddn.com/chengxutu2.jpg)"
添加一行
```bash
port: '8090'
```
