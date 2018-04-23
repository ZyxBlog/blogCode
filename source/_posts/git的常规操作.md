---
title: git的常规操作
date: 2016-07-31 09:22:05
tags:
- git
categories:
- git
---

## git命令
git clone ‘地址’是从地址克隆到本地。
git add file/. 是将文件或者所有文件添加到暂存区,也可以用git commit -a file/。
git commit -m “message”是将所有文件修改过的提交上去。
git pull是更新本地代码。
git push是推到远程库里面,git push origin dev推送远程其他分支。
git status是查看更改信息和状态,例如当rm file删除文件时,用该命令就知道file被删了。
git checkout -file丢弃工作区的修改。
如果是修改还未放入暂存区,撤销修改后就和版本库一样;如果是已经放入暂存区了,就回到暂存区的状态。
git reset HEAD file是将暂存区的修改撤销,重新放回工作区。
git remote add origin git@server-name:path/repo-name.git关联一个远程库。
git push -u origin master(第一次推送)。
git push origin master(后来推送)。
git checkout -b dev创建dev分支并切换到dev分支,git branch查看当前分支。
get branch dev是创建分支,get checkout dev是切换分支。
git remote查看远程库  git remote -v更详细的信息。
git branch -d dev删除dev分支。
git reset -hard <以前的版本> git撤销已经push到远端的commit
git push prigin <分支> -force 强制推送
