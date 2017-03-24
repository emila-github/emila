---
title: Jade-模板引擎学习笔记
date: 2017-03-24 11:42:05
tags: [Jade, 模板引擎]
---

jade 是 node 上一个常用的 html 模板语言，在咱项目里用来做 html 预处理语言，主要目的是减少代码量，同时让代码结构更清晰。
**jade 更名为 pug**

## 基础语法规则

1. 缩进代表嵌套
2. 每行**以第一个空格**为“分割符”之前的字符串（这部分暂称为 "tag-string"）编译为一个 html tag（以下简称 tag ），此空格之后的所有字符都**原封不动**的装进这个 tag 里
3. 使用css里的 `.class` 和 `#id` 的语法，直接用这两种语法开头的话可以省略 `div`
4. html attribute 可以写在括号"()"里跟在 tag-string 后面，此时括号内的空格不会被前述的第二条规则计算为“分割符”
5. `|` 处在行首，表示该行不做编译处理

### 例一

jade: 

    // e.g. I
    // 规则 1 + 规则 4
    div
      span
        input(type="text" required placeholder="Name")

html:

    <-- e.g. I -->
    <div>
      <span>
        <input type="text" required placeholder="Name"/>
      </span>
    </div>

### 例二

jade: 

    // e.g. II
    // 规则 2 + 规则 3 + 规则 5
    #greeting.bold-text <span class="blue">Hello</span>, <br>
      br
      span.red(id="additional-id")
        world!
        i Yeah, 
      |I'm good!

html:

    <-- e.g. II -->
    <div id="greeting" class="bold-text">
      <span class="blue">Hello</span>,
      <br>
      <br>
      <span class="red" id="additional-id">world!
        <i>Yeah,</i>
      </span>
      I'm good!
    </div>


## 模板功能简介

jade 使用这么几个关键词来承担模板功能：

1. include
2. extend
3. block

其后跟着的无论标记名还是 jade 文件的路径名都不必加引号 “” 且`.jade`后缀名可省略。

### include

`include` 就是在此插入另一个文件里写的 jade 代码段

include的例子：

	//- index.jade
	doctype html
	html
		include ./layout/header.jade
		body
		h1 include demo
		p content
		include ./layout/footer.jade

### extend & block

这两个关键词通常成对出现。

举例讲，你可以先写一个 `root/path/template/layout.jade`:

    doctype html
    html
	 head
	  block title
	   title默认内容
	 body
	  block content
      script(type="text/javascript" src="js/jquery.js")

之后写别的页面就可以通过 extend 将 `layout.jade` 作为“母板”，从而省去重复的部分，而通过 block 来提供变化的部分

例如新建页面 `root/path/index.html`:

    extend template/layout
	//- 进行替换
	block title
	 title新内容
	//- 进行替换
    block content
      h1 Hello, world!

这样等价于写：

    doctype html
    html
	 head
	  title新内容
	 body
	  h1 Hello, world!
      script(type="text/javascript" src="js/jquery.js")



## 参考资料 ##
- [Jade-简明教程](https://github.com/kelexx/devnotes/wiki/Jade-%E7%AE%80%E6%98%8E%E6%95%99%E7%A8%8B)
- [jade 官网](http://jade-lang.com/)
