---
title: gitlab
date: 2016-09-02 20:42:05
tags: [git]
---

# [Generating a new SSH key](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/) #

## Open Git Bash. ##

## Paste the text below, substituting in your GitHub email address. ##

    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
>  Creates a new ssh key, using the provided email as a label
> Generating public/private rsa key pair.
## When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location. ##


> Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]
## At the prompt, type a secure passphrase. For more information, see "Working with SSH key passphrases". ##

> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]



进入目录cd 仓库名，执行命令

    git config --global user.name "王常键"
    git config --global user.email "changjianwang@cyou-inc.com"

设置你的个人信息。

## Create a new repository ##

    git clone ssh://git@ued.local.17173.com:10022/changjianwang/test.git   //从现有仓库克隆
    cd test
    touch README.md   //新建文件README.md
    git add README.md   //当前文件"README.md"添加到暂存区
    git commit -m "add README"   //git commit -m "注释"，把暂存区内容提交到本地仓库 
    git push -u origin master   //把本地仓库的提交推送到远程仓库


##  Existing folder or Git repository ##

    cd existing_folder
    git init
    git remote add origin ssh://git@ued.local.17173.com:10022/changjianwang/test.git
    git add .   //当前目录所有文件添加到暂存区
    git commit
    git push -u origin master


## Git本地分支管理  分支的创建、合并、删除  ##
    git branch //显示所有分支 
    git branch b1 //从当前分支创建一个叫b1的分支 
    git checkout b1 //切换到b1分支 
    git checkout -b b1 //相当于以上两条命令的组合 
    git checkout master  //切换到master主分支 
    git merge b1  //把b1分支的代码合并到master上 
    git branch -d b1   //删除b1分支，不能在被删除分支上执行

## Git Tag标签管理  标签的创建、删除  ##
    git tag t1，从当前分支创建一个名为t1的标签 
    git tag -d t1，删除名为t1的标签
    git tag -a v1.4 -m 'version 1.4'  //新建一个v1.4的tag,并提把内容提交到本地仓库
    git push --tags  //提交推送到远程仓库

## Git本地仓库操作命令  ##
    git status，查看当前状态，发现有未跟踪文件 
    git diff，比较当前工作区和暂存区有何不同 
    git status，查看当前状态，发现有文件未提交 
    git log，查看提交日志
	git rebase i HEAD~1 //修改最近的第一条日志记录
    git commit --amend //修改最近的一条日志记录
    gitinit/git clone 【初始化库】 
    git status 【查看状态】 
    git add【添加文件】
    git diff【对比文件】
    git commit【提交更新】
    git rm【移除文件】
    git mv【移动文件】
    git log 【查看提交历史】
	git log --pretty=oneline //  查看当行日志 
    git reset 【撤销操作】
    git branch 【创建分支】
    git merge  【分支合并】
    git conflict 【解决冲突】
    git tag 【创建标签】


## 特性分支 ##
从develop分支创建，用于特性开发，完成后要合并回develop分支。
 
**操作过程：** 

    git checkout -b newfeature develop //从develop分支创建newfeature特性分支 
    git checkout develop //开发完成后，需要合并回develop分支，先切换到develop分支 
    git merge --no-ff newfeature //合并回develop分支，必须加--no-ff参数 
    git branch -d newfeature  //删除特性分支 
    git push origin develop //把合并后的develop分支推送到远程仓库 
    

## 帮助文档 ##
- [Gitlab使用手册](http://wenku.baidu.com/link?url=dYKBMJAi3EQSWilvVSkLXlD95HM28SHNnAg6CXNBM8KuDkIEOduFI-rXYAFKFlvcfIneNphcV_FtCBHhKkGTiChzL1Nkb_L3fsVeSgw_ohC)
- [Git & GitLab 使用及规范](http://www.myexception.cn/software/1891171.html)