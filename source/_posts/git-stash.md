---
title: git stash
date: 2017-03-08 10:33:06
tags: [git]
---


git stash命令用于将本地变更挂起。

	// 暂存当前状态
	# git stash
	
	// 查看当前工作区和版本库区别
	# git diff HEAD
	==> 此时什么都没有输出，说明工作区被重置为HEAD指向内容了
	
	// 显示已暂存列表
	# git stash list
	stash@{0}: WIP on master: 440e976 init
	
	// 恢复暂存区和工作区进度
	# git stash pop --index stash@{0}
	
	// 查看工作区和版本库区别
	# git diff HEAD
	diff --git a/readme b/readme
	index ce01362..55d6c28 100644
	--- a/readme
	+++ b/readme
	@@ -1 +1,2 @@
	 hello
	+need to be stashed

命令详解

> 注：
> 
>  []方括号中内容为可选，[< stash >]里面的stash代表进度的编号形如：stash@{0}, <>尖括号内的必填
> git stash 对当前的暂存区和工作区状态进行保存。
> 
> git stash list 列出所有保存的进度列表。
> 
> git stash pop [--index] [< stash >] **恢复工作进度**


--index 参数：不仅恢复工作区，还恢复暂存区

<stash> 指定恢复某一个具体进度。如果没有这个参数，默认恢复最新进度

如：以下命令恢复编号为0的进度的工作区和暂存区

	`git stash pop --index stash@{0}`



git stash [save message] [-k|--no-keep-index] [--patch]


> 这是git stash保存进度的完整命令形式
> 使用save可以对进度添加备注
> # git stash save "这是保存的进度"
> 
> 现在执行list，会发现后面会出现自定义的备注
> # git stash list
> stash@{0}: On master: 这是保存的进度
> 
> -k和--no-keep-index指定保存进度后，是否重置暂存区
> --patch 会显示工作区和HEAD的差异,通过编辑差异文件，排除不需要保存的内容。和git add -p命令类似



git stash apply[--index] [< stash >] 不删除已恢复的进度，其他同 git stash pop

git stash drop[< stash >] 删除某一个进度，默认删除最新进度

git stash clear删除所有进度

git stash branch < branchname > < stash >基于进度创建分支

## 来源 ##
- [git stash 详解](http://www.tuicool.com/articles/rUBNBvI)