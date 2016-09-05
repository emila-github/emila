---
title: node.js之path模块
date: 2016-09-02 20:42:05
tags: [node, path]
---
# node.js之path模块 #



## node之path模块 ##

    //引用该模块
    var path = require("path");

## 1、path.normalize(p) 路径解析，得到规范化的路径格式 ##

	//对window系统，目录分隔为'\', 对于UNIX系统，分隔符为'/'，针对'..'返回上一级；/与\\都被统一转换
	//path.normalize(p);
	
	var myPath = path.normalize(__dirname + '/test/a//b//../c/utilyou.mp3');
	console.log(myPath); //windows: E:\workspace\NodeJS\app\fs\test\a\c\utilyou.mp3

## 2、path.join([path1],[path2]..[pathn])路径结合、合并，路径最后不会带目录分隔符 ##

	//path.join([path1],[path2]..[pathn]);
	/**
	 * [path1] 路径或表示目录的字符，
	 */
	
	var path1 = 'path1',
	    path2 = 'path2//pp\\',
	    path3 = '../path3';
	
	var myPath = path.join(path1, path2, path3);
	console.log(myPath); //path1\path2\path3

## 3、path.resolve(path1, [path2]..[pathn]) 获取绝对路径 ##

	//path.resolve(path1, [path2]..[pathn]);
	
	//以应用程序为起点，根据参数字符串解析出一个绝对路径
	
	/**
	 * path 必须至少一个路径字符串值
	 * [pathn] 可选路径字符串
	 */
	
	var myPath = path.resolve('path1', 'path2', 'a/b\\c/');
	console.log(myPath);//E:\workspace\NodeJS\path1\path2\a\b\c


## 4、path.relative(from, to) 获取相对路径 ##

	//path.relative(from, to);
	//获取两路径之间的相对关系
	
	/**
	 * from 当前路径，并且方法返回值是基于from指定到to的相对路径
	 * to   到哪路径，
	 */
	
	var from = 'c:\\from\\a\\',
	    to = 'c:/test/b';
	
	var _path = path.relative(from, to);
	console.log(_path); //..\..\test\b; 表示从from到to的相对路径

## 5、path.dirname(p) ##

	// 获取路径中目录名

	var myPath = path.dirname(__dirname + '/test/util you.mp3');
	console.log(myPath);

## 6、path.basename(path, [ext]) ##

	// 获取路径中文件名,后缀是可选的，如果加，请使用'.ext'方式来匹配，则返回值中不包括后缀名；
	
	var myPath = path.basename(__dirname + '/test/util you.mp3', '.mp3');
	console.log(myPath);

## 7、path.extname(path) ##
	//获取路径中的扩展名，如果没有'.'，则返回空

## 8、path.sep属性 ##

	//返回操作系统中文件分隔符； window是'\\', Unix是'/'

## 9、path.delimiter属性 ##

	//返回操作系统中目录分隔符，如window是';', Unix中是':'

## path.parse(path) 把路径转换为对象## 

	linux
	path.parse('/home/user/dir/file.txt')
	// returns
	{
	    root : "/",
	    dir : "/home/user/dir",
	    base : "file.txt",
	    ext : ".txt",
	    name : "file"
	}
	windows
	path.parse('C:\\path\\dir\\index.html')
	// returns
	{
	    root : "C:\\",
	    dir : "C:\\path\\dir",
	    base : "index.html",
	    ext : ".html",
	    name : "index"
	}


## path.format(pathObject) 合并文件名 ##
与parse相逆

	path.format({
	    root : "/",
	    dir : "/home/user/dir",
	    base : "file.txt",
	    ext : ".txt",
	    name : "file"
	})
	// returns
	'/home/user/dir/file.txt'

## path.isAbsolute(path) 判断是否是绝对路径，如果长度为0，则返回false##
判断是否绝对路径
	linux
	path.isAbsolute('/foo/bar') // true
	path.isAbsolute('/baz/..')  // true
	path.isAbsolute('qux/')     // false
	path.isAbsolute('.')        // false
	
	windows
	path.isAbsolute('//server')  // true
	path.isAbsolute('C:/foo/..') // true
	path.isAbsolute('bar\\baz')  // false
	path.isAbsolute('.')         // false

## path.posix ##
提供上述 path路径访问，不过总是以 posix 兼容的方式交互。
## path.win32 ##
提供上述 path路径访问，不过总是以 win32 兼容的方式交互。


## 参考 ##
- [node.js之path模块](http://www.jianshu.com/p/fe41ee02efc8)
- [nodejs-path模块](http://www.jianshu.com/p/56bc803ecce2)

