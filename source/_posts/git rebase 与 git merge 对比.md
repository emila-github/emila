---
title: git rebase 与 git merge 对比
date: 2016-09-10 14:44:10
tags: [git]
---

## 基础 ##

git rebase用于把一个分支的修改合并到当前分支。

假设你现在基于远程分支"origin"，创建一个叫"dev"的分支。

	$ git checkout -b dev origin

现在我们在这个dev分支做一些修改，然后生成两个提交(commit).

	$ vi d1.txt
	$ git commit -m 'add d1.txt 10:01'
	$ vi d2.txt
	$ git commit -m 'add d2.txt 11:02'

此时你在dev分支上查看日志

	$ git log --pretty=oneline
	
	a4636d76ab717ba13f30f998d586505d9d6587a2 add d2.txt 11:02
	46a24bfbab84bb95eb7b07d3fedc7df9525e2f3f add d1.txt 10:01


在你修改dev分支的同时，origin这个分支也发生了变化
他和dev分支一样也发生了两次提交，提交日志为：

	$ git log --pretty=oneline
	
	af0536eb96d4e7ef5f2858afc063f5a32cdcbdca add o2.txt 10:41
	f32a0a6e156c5c4a47cf2c78b76876c0e13d61bf add o1.txt 10:31


这时候在dev分支上 我们可以用 `git merge`  或 `git rebase` 来合并origin的更新到dev分支上

### git merge 合并的效果 ###
	#此时在dev分支上 使用以下命令
	$ git merge origin
	$ git log --pretty=oneline 
	
	1e46d0bb1e936cc3e9390bc9cc6b9add176f7cde Merge branch 'origin' into dev
	a4636d76ab717ba13f30f998d586505d9d6587a2 add d2.txt 11:02
	af0536eb96d4e7ef5f2858afc063f5a32cdcbdca add o2.txt 10:41
	f32a0a6e156c5c4a47cf2c78b76876c0e13d61bf add o1.txt 10:31
	46a24bfbab84bb95eb7b07d3fedc7df9525e2f3f add d1.txt 10:01

### git rebase 合并的效果 ###
	#此时在dev分支上 使用以下命令
	$ git rebase origin
	$ git log --pretty=oneline 
	
	a4636d76ab717ba13f30f998d586505d9d6587a2 add d2.txt 11:02
	46a24bfbab84bb95eb7b07d3fedc7df9525e2f3f add d1.txt 10:01
	af0536eb96d4e7ef5f2858afc063f5a32cdcbdca add o2.txt 10:41
	f32a0a6e156c5c4a47cf2c78b76876c0e13d61bf add o1.txt 10:31

### 效果对比 ###

**merge** 合并后有一个合并的日志，他的合并的日志是根据commit的时间先后顺序倒序排列，并且可以通过回退命令 `$ git reset --hard 1e46d0bb1e936cc3e9390bc9cc6b9add176f7cde` 来重置到合并前的状态

**rebase** 合并后没有合并记录，日志的排列是吧 origin 分支的 commit 日志直接插入到当前分支的 commit之前， 并且无法回退到 rebase前操作




## 资料 ##
- [git rebase简介(基本篇)](http://gitbook.liuhui998.com/4_2.html)
- [rebase](http://gitbook.liuhui998.com/4_2.html)