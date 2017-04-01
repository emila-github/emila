---
title: Sublime Text 3 -实用的sublime插件集合
date: 2017-04-1 10:42:05
tags: [Sublime Text]
---

## 插件介绍 ##

### Package Control ###

- 功能：安装包管理
- 简介：sublime插件控制台，提供添加、删除、禁用、查找插件等功能
- 使用：https://sublime.wbond.net/installation

**安装方法：**

`CTRL+`` ，出现控制台
粘贴以下代码至控制台

ST3：

	import urllib.request,os,hashlib; h = 'df21e130d211cfc94d9b0905775a7c0f' + '1e3d39e33b79698005270310898eea76'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)

> 其他方法：
> 如果以上方法不能安装，请使用下面的方法
> 选择菜单：Preferences Browse Packages
> 打开sublime插件安装包文件夹
> 下载文件并复制到打开的文件夹
> 重启sublime



## Emmet ##

- 功能：编码快捷键，前端必备
- 简介：Emmet作为zen coding的升级版，对于前端来说，可是必备插件，如果你对它还不太熟悉，可以在其官网（http://docs.emmet.io/）上看下具体的演示视频。
- 使用：教程-[http://docs.emmet.io/cheat-sheet/](http://docs.emmet.io/cheat-sheet/)、[http://peters-playground.com/Emmet-Css-Snippets-for-Sublime-Text-2](http://peters-playground.com/Emmet-Css-Snippets-for-Sublime-Text-2)/

![](http://cdn.xuanfengge.com/wp-content/uploads/2013/12/emmet.gif)


## JSFormat ##

- 功能：Javascript的代码格式化插件
- 简介：很多网站的JS代码都进行了压缩，一行式的甚至混淆压缩，这让我们看起来很吃力。而这个插件能帮我们把原始代码进行格式的整理，包括换行和缩进等等，是代码一目了然，更快读懂~
- 使用：在已压缩的JS文件中，右键选择jsFormat或者使用默认快捷键（Ctrl+Alt+F）

![](http://cdn.xuanfengge.com/wp-content/uploads/2013/12/jsFormat.gif)


## LESS ##

- 功能：LESS高亮插件
- 简介：用LESS的同学都知道，sublime没有支持less的语法高亮，所以这个插件可以帮上我们
- 使用：打开.less文件或者设置为less格式

![](http://cdn.xuanfengge.com/wp-content/uploads/2013/12/less.gif)


## jQuery ##

- 功能：jQ函数提示
- 简介：快捷输入jQ函数，是偷懒的好方法

![](http://cdn.xuanfengge.com/wp-content/uploads/2013/12/jquery.gif)


## Doc​Blockr ##

功能：生成优美注释
简介：标准的注释，包括函数名、参数、返回值等，并以多行显示，手动写比较麻烦
使用：输入/*、/**然后回车，还有很多用法，请参照
https://sublime.wbond.net/packages/DocBlockr

![](http://cdn.xuanfengge.com/wp-content/uploads/2013/12/basic.gif)
![](http://cdn.xuanfengge.com/wp-content/uploads/2013/12/function-template.gif)

## AutoFileName ##

- 功能：快捷输入文件名
- 简介：自动完成文件名的输入，如图片选取
- 使用：输入”/”即可看到相对于本项目文件夹的其他文件

![](http://cdn.xuanfengge.com/wp-content/uploads/2013/12/autofilename.gif)

## Nodejs ##

- 功能：node代码提示
- 教程：https://sublime.wbond.net/packages/Nodejs

![](http://cdn.xuanfengge.com/wp-content/uploads/2013/12/ZCFcC.png)


## Enhancements ##

- 功能：是一款很实用的右键菜单增强插件；在安装该插件前，在Sublime Text左侧FOLDERS栏中点击右键，只有寥寥几个简单的功能；安装了就相当于给其丰了大胸一般。

## HTML-CSS-JS Prettify ##

- 功能：一款集成了格式化（美化）html、css、js三种文件类型的插件


## Bracket Highlighter ##

- 功能：高亮各种括号的起始和结尾
- 
## AdvancedNewFile ##

- 功能：
	快速创建文件，快捷键 `ctrl+alt+n`

	默认情况下文件会存储在当前目录，如果当前没有目录，会存储在用户的根目录

## LiveStyle ##

- 功能：
	- 开启一种实时编辑体验的开发插件
	- 	支持Chrome浏览器，还支持Safari浏览器
	- 	实时进行CSS调试插件工具
	- 	当你在文本编辑器中打字的时候，(LiveStyle)即时同步更新网页，不用等到文件- - 	保存或者页面预加载。并且LiveStyle是第一个能够将在浏览器开发工具栏的变化以正确的方式同步更新到源代码中

	




## 参考资料 ##

- [实用的sublime插件集合 – sublime推荐必备插件](http://www.xuanfengge.com/practical-collection-of-sublime-plug-in.html)
- [packagecontrol](https://packagecontrol.io/installation)
- [Emmet Documentation](https://docs.emmet.io/cheat-sheet/)