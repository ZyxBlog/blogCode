---
title: 关于margin的问题
date: 2017-02-04 10:50:27
tags:
- css
categories:
- 前端
---

今天遇到一个小问题，之前看到过的，但是后来忘了，今天又遇到有点的模棱两可。
是这样的:两个div，上面那个margin大一点，下面的div的margin小一点，问实际两个div相隔多远？
答案是：两者取大的那个margin，margin会重合。
那如果是嵌套的div，实际相隔多远？
答案是：两者距离取里面的div的margin。
