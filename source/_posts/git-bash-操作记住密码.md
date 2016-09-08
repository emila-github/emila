---
title: git bash 操作记住密码
date: 2016-09-08 21:34:14
tags: [git]
---



> git for windows 如何记住用户名和密码 

## 创建存储用户名密码的文件  ##
在home文件夹，一般是 C:\Documents and Settings\Administrator 下建立文件 .git-credentials （windows下不允许直接创建以.开头的文件，所以有一个小技巧：先创建一个文件名叫 ）git-credentials 然后进入 git bash 使用命令： 


	mv git-credentials .git-credentials 

用记事本打开这文件输入，如果用户名中有@，那么使用%代替： 

	https://{username}:{password}@github.com 
	#比如： 
	#https://zhangsan:123456@github.com 

保存 ，添加config项 ，在任意文件夹下右键进入 git bash ，然后输入： 
	git config --global credential.helper store 

执行完后去查看 C:\Documents and Settings\Administrator\.gitconfig 这个文件，发现多了一项： 

	[credential] 
	helper = store 

就成功了。 

然后要重开 git bash 窗口，再提交就不用输入用户名密码 