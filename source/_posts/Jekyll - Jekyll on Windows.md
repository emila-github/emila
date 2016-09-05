---
title: Jekyll - Jekyll on Windows
date: 2016-09-02 20:42:05
tags: [Jekyll]
---
# Jekyll - Jekyll on Windows #


> Jekyll 是一个简单的网站静态页面生成工具。由于是用Ruby语音编写的，所以在Windows系统上配置起来还是稍微有点繁琐的。具体过程如下：

## 安装 Ruby ##

进入 Ruby 的 [rubyinstaller.org](http://rubyinstaller.org/downloads/). 下载 [Ruby 2.0.0-p481 (x64)](http://dl.bintray.com/oneclick/rubyinstaller/rubyinstaller-2.0.0-p481-x64.exe?direct) 并安装（根据系统选择）。

查看安装是否成功  

	ruby --version

## 安装 Ruby 的 Devkit ##

进入 Ruby的官网 下载  [DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe](http://cdn.rubyinstaller.org/archives/devkits/DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe)

下载后解压到 `C:\rubydevkit\`,

进入目录

    cd "C:\rubydevkit\"

初始化配置,生成一个 config.yml 配置文件，该配置文件中包含了前面的Ruby安装目录 
	ruby dk.rb init

安装 DevKit
	ruby dk.rb install

配置 devkit的 config.yml
在文件中添加 Ruby 的路径  

	---
	- C:/ruby200-x64	
	- 
## 安装 Jekyll ##
	gem install jeyll

> 安装后的路径 C:\Ruby200-x64\lib\ruby\gems\2.0.0\gems\jekyll-2.3.0\bin

成功后将 jeyll 添加到环境变量的 path 中


## 安装 Python ##

进入 Python 的 [python.org](http://www.python.org/download/). 下载安装包 [Python 3.4.1 Windows X86-64 MSI Installer](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64.msi)


安装后配置环境变量的 path,  `C:\Python27`


成功后进入要生成静态页面的目录运行

	jekyll serve


浏览器中输入`http://localhost:4000/` 就可以直接运行你的 Jekyll 页面








