---
title: node的安装
date: 2016-07-16 11:19:22
tags:
- nodejs
categories:
- 前端
---

## nodejs安装

### 本文采用nvm安装node

参考-nvm-的-README-，执行下面的命令，我用的是-ubuntu-系统应该这样的操作：
```bash
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash
```

这样 nvm 就安装好了，可能要重启一下 shell 才有 nvm 这个命令。

查看版本：
```bash
nvm ls-remote
```

可以看到当前最新版本是-v6-2-0-，运行下面的命令来安装：
```bash
nvm install v6.2.0
```
现在再来安装一个包，看看会被安装到什么位置
```bash
$ npm i -g gulp
```
```bash
/Users/zyx/.nvm/versions/node/v6.2.0/bin/gulp
```

可以看到-gulp-这个包安装到了-Users-zyx-之下。并且可执行文件也自动导出为系统命令了，可以通过运行下面的命令来确认：
```bash
$ which gulp
```
```bash
/Users/zyx/.nvm/versions/node/v6.2.0/bin/gulp
```

设置默认版本

每次启动新 shell ，Node 还是老版本。写成最新安装的 NVM 版本：
```bash
$ nvm alias default 6.2.0
```

让npm使用淘宝镜像换源,到 taobao 相关页面，找到下面的命令：
```bash
$ echo alias cnpm="npm --registry=https://registry.npm.taobao.org \
  --cache=$HOME/.npm/.cache/cnpm \  
  --disturl=https://npm.taobao.org/dist \
  --userconfig=$HOME/.cnpmrc
$ ~/.zshrc
$ source ~/.zshrc
```

因为我是ubuntu系统请把上面的 .zshrc 替换为 .bashrc 。

cnpm跟npm用起来没有任何区别，可以放心使用。但是由于是国内的源，在安装包的时候会下载的更快
