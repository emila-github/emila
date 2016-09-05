---
title: ubuntu - 乌邦图终端学习笔记
date: 2016-09-02 20:42:05
tags: [ubuntu]
---
# ubuntu - 乌邦图终端学习笔记 #



## Ctrl+Shift+t 快速打开新的模拟终端 ##

起始目录， 家目录

- 普通用户：/home/username
- root: /root


## 下如何以root用户登录 ##

1、先解除root锁定，为root用户设置密码

打开终端输入：`sudo passwd`

	Password: <--- 输入你当前用户的密码
	
	Enter new UNIX password: <--- 新的Root用户密码
	
	Retype new UNIX password: <--- 重复新的Root用户密码
	
	passwd：已成功更新密码

## su:切换用户 ##

- su [-] login 切换用户  例如： `su - root`
- sudo passwd 不用切换用户以另外一个用户身份执行命令

> su 在不加任何参数，默认为切换到root用户，但没有转到root用户家目录下，也就是说这时虽然是切换为root用户了，但并没有改变root登录环境；su 加参数 - ，表示默认切换到root用户，并且改变到root用户的环境；



## 文件管理 ##

- 文件管理 # ls ls -a 列出当前目录下的所有文件，包括以.头的隐含文件   
- 文件管理 # ls ls -l或ll 列出当前目录下文件的详细信息  
- 文件管理 # pwd pwd 查看当前所在目录的绝对路经  
- 文件管理 # cd `cd ..` 回当前目录的上一级目录  
- 文件管理 # cd `cd -` 回上一次所在的目录  
- 文件管理 # cd `cd ~` 或 cd 回当前用户的宿主目录  
- 文件管理 # cd `cd ~用户名` 回指定用户的宿主目录 

## 安装vim ##
    sudo apt-get install vim
- sudo 表示以管理员身份运行后面的命令
- apt-get 是ubuntu下的包管理工具
- install 是安装的意思
- vim 是一个编辑器软件
- 
## 文件操作 ##
vi 打开一个不存在的文件a时，在没有输入保存命令时，a文件是不会存储到机器磁盘上的。

**vi打开一个文件时，进入的是阅读模式，只有输入相关命令才会进入编辑模式：**

- i :在当前位置插入
- a:在当前位置后追加
- o:在当前位置的后面插入一行
- I :在行头插入
- A:在行尾追加
- O:在当前位置的前面插入一行
- 'ESC'键从编辑模式转换到阅读模式

**阅读模式（或叫命令模式）下：**

- :w 保存文件
- :w filename 保存成filename文件
- :q 退出
- :q! 强行退出
- :w! 强行写
- :wq 保存退出
- :x 同wq