---
title: ubuntu显示器分辨率调整
date: 2017-07-18 12:56:24
tags:
- ubuntu
categories:
- linux
---

ubuntu外接显示器出现显示器分辨率的问题
解决方法如下:
```bash
cvt 1920 1080
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode VGA1 "1920x1080_60.00"xrandr --output VGA1 --mode "1920x1080_60.00"
```
这样就可以了,但不是永久的,当计算机关闭之后,又变成了原样,因此
```bash
sudo vim ~/.profile
```
用vim打开.profile文件后将上述命令写入,并保存.
