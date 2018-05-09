---
title: canvas中getImageData跨域问题
date: 2017-10-27 13:33:12
tags:
- html5
categories:
- 前端
---

在本地使用canvas中的getImageData()这个方法时发现控制台报如下错：22 Uncaught DOMException: Failed to execute ‘getImageData’ on ‘CanvasRenderingContext2D’: The canvas has been tainted by cross-origin data.at HTMLImageElement.image.onload
由此可知这里有一个跨域的问题。
原因是图片存在本地是没有域名的，而使用该方法时，浏览器会判定为跨域而报错。
我的解决方法是用node配置本地服务器，使用express框架和http模块，将把图片上传本机服务器中，通过客户端返回给服务器。
