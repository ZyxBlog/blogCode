---
title: 关于json的操作
date: 2016-08-25 22:03:45
tags:
- json
categories:
- 前端
---
json是一种轻量级的数据交换格式,目前前端后台交互主要是通过json格式的数据来进行交互,具体格式是{'name':'zyx'}.
对于前端来说,交互获取json数据我们需要进行处理,有时候要转化成js对象形式,JSON.parse(str)就可以将{'name':'zyx'}转化成{name:'zyx'}.
当我们给后台传送数据的时候,有时候需要将js对象转化成json形式,例如JSON.stringify({password:123})可以转化成json格式的,为{'password':123}.
JSON.parse()和JSON.stringify()是用于交互时数据关于json转化的方便的工具.
