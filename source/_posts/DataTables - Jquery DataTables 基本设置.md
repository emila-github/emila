---
title: npm package.json中的dependencies和devDependencies的区别
date: 2016-09-02 20:42:05
tags: [npm,package]
---

一个node package有两种依赖，一种是dependencies一种是devDependencies，其中前者依赖的项该是正常运行该包时所需要的依赖项，而后者则是开发的时候需要的依赖项，像一些进行单元测试之类的包。

如果你将包下载下来在包的根目录里运行

	npm install

默认会安装两种依赖，如果你只是单纯的使用这个包而不需要进行一些改动测试之类的，可以使用

	npm install --production

只安装dependencies而不安装devDependencies。

如果你是通过以下命令进行安装

	npm install packagename

那么只会安装dependencies，如果想要安装devDependencies，需要输入

	npm install packagename --dev  

## 参考文献： ##


- [npm package.json中的dependencies和devDependencies的区别](http://www.luckyonecn.com/blog/difference_between_dependencies_and_devdependencies_in_npm/)

npm官方文档：

- [package.json](https://www.npmjs.org/doc/json.html)
- [npm-install](https://www.npmjs.org/doc/cli/npm-install.html)