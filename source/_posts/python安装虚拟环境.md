---
title: python安装虚拟环境
date: 2017-12-29 13:47:48
tags:
- python
categories:
- 后台
---

一、步骤：
sudo apt install python-pip
2.1）升级pip
sudo pip install –upgrade pip
2.2）使用pip安装虚拟环境完成后，有可能使用指令无法启动虚拟环境，为了避免套件被安装在系统环境中，需要在~/.bashrc文件中加上代码：
export PIP_REQUIRE_VIRTUALENV=true
或者在执行pip的时候让系统自动开启虚拟环境<br>export PIP_RESPECT_VIRTUALENV=true
3）安装virtualenv
sudo pip install virtualenv
由于有virtualenvwrapper虚拟环境管理包，能够直接使用简单指令操作虚拟环境，所以就不使用virtualenv自带的指令来操作虚拟环境。
4）安装virtualenvwrapper
sudo pip install virtualenvwrapper
5）配置virtualenvwrapper
默认的virtualenvwrapper安装在/usr/loacl/bin 目录下，需要运行virtualenvwrapper.sh文件。按照文件中的安装步骤设置环境：
创建目录存放虚拟环境
mkdir $HOME/.virtualenvs
在~/.bashrc中添加行：
export WORKON_HOME=$HOME/.virtualenvs
source /usr/local/bin/virtualenvwrapper.sh
运行：source ~/.bashrc
此时virtualenvwrapper就配置好了，接下来可以使用命令运行虚拟环境。
6）使用指令操作虚拟环境
列出虚拟环境列表
lsvirtualenv
创建新虚拟环境mkvirtualenv [name]启动/
切换虚拟环境workon [name]
删除虚拟环境rmvirtualenv [name]
离开虚拟环境deactivate
二、在搭建虚拟环境的时候，遇到报错OSError: Command /home/zyx/font-d/learning/lenv/bin/python2 - setuptools pkg_resources pip wheel failed with error code 2
遇到python2中依次执行
$ pip -V　
$ sudo pip install –upgrade pip
然后建立虚拟环境时virtualenv 文件夹名
同时HTTPError: 404 Client Error: Not Found for url: http://pypi.doubanio.com/simple/pkg-resources/
解决方法：换源
