---
title: github 更新 fork 出来的项目使其和源仓库同步
date: 2016-09-02 20:42:05
tags: [git]
---
# github 更新 fork 出来的项目使其和源仓库同步 #

github上的一个开源项目（这里称：A_REPOSITORY_URL），进过我们 `fork` 到我们的仓库中（这里称：B_REPOSITORY_URL）。

以下是fork后 项目A更新后，仓库B拉取A更新的过程。

## 先把B clone到本地 ##

    git clone B_REPOSITORY_URL

## 再cd到本地B的目录，把A作为一个remote加到本地的B中（一般命名为upstream） ##

    git remote add upstream A_REPOSITORY_URL

## pull另一个A的remote（upstream）的相应分支（比如master）就可以 ##

    git pull upstream master

## 最后push回github的B_REPOSITORY ##

    git commit -a -m '同步A的拉取'
    git push origin master