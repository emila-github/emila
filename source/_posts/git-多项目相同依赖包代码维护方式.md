---
title: git-多项目相同依赖包代码维护方式
date: 2017-03-28 09:34:43
tags: [git]
---

> 在广告开发中，由于依赖包都相同，为了减少依赖包的重复安装，这里用分支作为项目的主干，以下是相关操作的方法


拉取广告公用模板作为master,新广告可以用他做分支，任何环境的变化都要合并到该主干上

	// git clone 远端源地址
	git clone ssh://git@ued.local.17173.com:10022/changjianwang/ad2017.git  

添加远端源

	// git remote add 本地源名称 远端源地址
	git remote add AdVrIndexTopBackground ssh://git@ued.local.17173.com:10022/changjianwang/AdVrIndexTopBackground.git

拉取远端源的master到本地源的AdVrIndexTopBackground分支上

	// git fetch origin 远程分支名x:本地分支名x
	git fetch AdVrIndexTopBackground master:AdVrIndexTopBackground


提交某个分支到远端源的主干上
	// git push origin 本地分支名x:远程分支名x
	git push AdVrIndexTopBackground AdVrIndexTopBackground:master




