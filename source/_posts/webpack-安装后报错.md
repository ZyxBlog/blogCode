---
title: webpack 安装后报错
date: 2017-04-26 12:01:40
tags:
- webpack
categories:
- 前端
---
### 安装步骤
在脱离vue-cli里面现成的webpack配置后，为了更深层的理解webpack，自己鼓捣了一下webpack。
按常规套路：
```bash
npm init
npm install webpack --save-dev
```
一路enter下来，本应该无事的，却报错Refusing to install webpack as a dependency of itself;
研究了官方文档和搜索了网上一些不靠谱的解答。
回到代码，考虑到命令没有错误，只有可能是enter一路字段有误，经验证默认package.json里面的name值为webpack。
找到问题所在。
so， 改变name，只要不为webpack即可。
