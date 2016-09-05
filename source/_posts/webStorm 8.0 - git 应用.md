---
title: webStorm 8.0 - git 应用
date: 2016-09-02 20:42:05
tags: [webStorm,git]
---
# webStorm 8.0 - git 应用 #


## 在Windows上安装Git ##

Windows下要使用很多Linux/Unix的工具时，需要Cygwin这样的模拟环境，Git也一样。Cygwin的安装和配置都比较复杂，就不建议你折腾了。不过，有高人已经把模拟环境和Git都打包好了，名叫msysgit，只需要下载一个单独的exe安装程序，其他什么也不用装，绝对好用。

`msysgit` 是Windows版的Git，从[http://msysgit.github.io/](http://msysgit.github.io/)下载，然后按默认选项安装即可。

安装完成后，在开始菜单里找到“Git”->“Git Bash”，蹦出一个类似命令行窗口的东西，就说明Git安装成功！

## 配置Git ##

在File菜单，选择 settings 进入设置界面。 

选择 `Version Control` 选项

- 进入 Github 设置 host、login、password等信息。
- 进入 Git 设置 path to git executable , 使其指向git安装目录。 如： `C:\Program Files (x86)\Git\bin\git.exe`；

之后ok就可以了。



## 启用Git源码管理 ##

Vcs菜单，`Enable version control integration`，激活源码管理集成。我们选择 `Git`。 此时webStorm就可以正常使用git管理代码了。


## 参考资料 ##

- [Git教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
- [git for windows](http://msysgit.github.io/)

