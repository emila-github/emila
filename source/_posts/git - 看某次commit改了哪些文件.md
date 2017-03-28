---
title: git 看某次commit改了哪些文件
date: 2017-03-24 8:42:05
tags: [git]
---

- git log 查看commit的历史
- git show <commit-hash-id>查看某次commit的修改内容
- git log -p <filename>查看某个文件的修改历史
- git log -p -2查看最近2次的更新内容
- git log --name-status 每次修改的文件列表, 显示状态
- git log --name-only 每次修改的文件列表
- git log --stat 每次修改的文件列表, 及文件修改的统计
- git whatchanged 每次修改的文件列表
- git whatchanged --stat 每次修改的文件列表, 及文件修改的统计
- git show 显示最后一次的文件改变的具体内容

