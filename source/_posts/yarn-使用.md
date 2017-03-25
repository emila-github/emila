---
title: yarn-使用
date: 2017-03-25 14:07:24
tags: [yarn]
---

## Windows ##

在 Windows 上安装 Yarn [下载安装程序](https://yarnpkg.com/latest.msi)

这将给你一个.msi 文件，当你运行它时带领你安装 Yarn 到 Windows 上。

如果你使用安装程序，你需要先安装 [Node.js。](https://nodejs.org/)




运行命令来测试 Yarn 是否安装：

	yarn --version


这里是一些你需要的最常用命令。

## 开始新项目 ##

	yarn init
## 添加依赖包 ##

	yarn add [package]
	yarn add [package]@[version]
	yarn add [package]@[tag]
## 升级依赖包 ##

	yarn upgrade [package]
	yarn upgrade [package]@[version]
	yarn upgrade [package]@[tag]
## 移除依赖包 ##

	yarn remove [package]
## 安装项目的全部依赖 ##

	yarn
或者

	yarn install

## 来源 ##
- [使用](https://yarnpkg.com/zh-Hans/docs/usage)
- [安装](https://yarnpkg.com/zh-Hans/docs/install)
