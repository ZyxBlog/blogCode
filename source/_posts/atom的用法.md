---
title: atom的用法
date: 2016-10-12 10:32:41
tags:
- Atom
categories:
- Atom
---

atom首先对于打开.vue文件既没有插件，也没有高亮，在此我们需要是Emmet插件适应.
### vim修改keymap
用vim打开vim ~/.atom/keymap.cson,其次编辑在文章末尾加上（里面大部分都是注释）
```bash
'atom-text-editor[data-grammar~="vue"]:not([mini])'
'emmet:expand-abbreviation-with-tab'
```

### 重启atom
重启atom，至此我们就能使atom的Emmet适应了vue

### 安装插件
接着需要安装一些插件，vue在Web前端的一些插件（可以在preferences里面的setting中安装）
* autoclose-html  =>  闭合html标签
* language-vue-component  =>  Atom编写Vue高亮
* vue-autocompile  =>  在atom上自动编译
* language-vue  =>  语法高亮显示
* atom-css-comb  =>  适合（css/less/sass）
