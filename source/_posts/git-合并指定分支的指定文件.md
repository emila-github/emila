---
title: git  合并指定分支的指定文件
date: 2017-03-17 11:10:28
tags: [git]
---

分支A_bracn和B_branch，只想将A_branch分支的某个文件f.txt合并到B_branch分支上。

	git checkout A_branch     // 切换到A分支；
	git checkout --patch B_branch f.txt  // 合并B分支上f文件到A分支上，将B分支上 f 文件追加补丁到A分支上 f文件。你可以接受或者拒绝补丁内容。

