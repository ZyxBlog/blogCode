---
title: python3更新
date: 2018-01-19 13:54:23
tags:
- python
categories:
- 后台
---

已知python3和python2由于变化比较大，是独立的。
最近由于python3的版本是3.5.2，是很久以前的，因此需要升级python3的版本。
1.首先从官网下载新版本的python
sudo apt-get install libssl-dev openssl wget https://www.python.org/ftp/python/3.6.5/Python-3.6.5.tgz
2.继而解压缩 tar xzvf Python-3.6.5.tgz
3.进入文件夹 cd Python-3.6.5
4.分别执行 ./configure
make          
sudo make install
在一次检查python3版本时
python3 -V 就输出Python 3.6.5
