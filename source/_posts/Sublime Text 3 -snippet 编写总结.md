---
title: Sublime Text 3 -snippet 编写总结
date: 2017-04-1 13:42:05
tags: [Sublime Text]
---

## 自定义- Snippet ##
### 简介 ###

Snippet 让Code更加高效，类似组件，通过快捷键调用

### Snippet 类型 ###

#### 1.安装第三方代码段如： ####

- 	Emmet Css Snippets 
- 	SASS Snippets
- 	jQuery  Snippets

#### 2. 创建自己代码段 ####

- 	创建：tools>developer>new snippet
- 	存储：必须以.sublime-snippet后缀

### 完整的结构和说明 ###
	
	<snippet>
	    <content><![CDATA[ 你需要插入的代码片段Hello, ${1:this} is a ${2:snippet}.]]></content>
	    <!-- 可选：快捷键，利用Tab自动补全代码的功能 -->
	    <tabTrigger>hello</tabTrigger>
	    <!-- 可选：使用范围，不填写代表对所有文件有效。附：source.css和test.html分别对应不同文件。 -->
	    <scope>source.python</scope>
	</snippet>

- ${1:this}表示代码插入后，光标所停留的位置，可同时插入多个。其中:name为自定义参数（可选）。
- ${2:snippet}表示代码插入后，按Tab键，光标会根据顺序跳转到相应位置（以此类推）。
- $ 符号的话 需要将它转义成 /$

## <scope>官方定义内容 ##


	ActionScript: source.actionscript.2
	AppleScript: source.applescript
	ASP: source.asp
	Batch FIle: source.dosbatch
	C#: source.cs
	C++: source.c++
	Clojure: source.clojure
	CoffeeScript: source.coffee
	CSS: source.css
	D: source.d
	Diff: source.diff
	Erlang: source.erlang
	Go: source.go
	GraphViz: source.dot
	Groovy: source.groovy
	Haskell: source.haskell
	HTML: text.html(.basic)
	JSP: text.html.jsp
	Java: source.java
	Java Properties: source.java-props
	Java Doc: text.html.javadoc
	JSON: source.json
	JavaScript: source.js
	BibTex: source.bibtex
	Latex Log: text.log.latex
	Latex Memoir: text.tex.latex.memoir
	Latex: text.tex.latex
	LESS: source.css.less
	TeX: text.tex
	Lisp: source.lisp
	Lua: source.lua
	MakeFile: source.makefile
	Markdown: text.html.markdown
	Multi Markdown: text.html.markdown.multimarkdown
	Matlab: source.matlab
	Objective-C: source.objc
	Objective-C++: source.objc++
	OCaml campl4: source.camlp4.ocaml
	OCaml: source.ocaml
	OCamllex: source.ocamllex
	Perl: source.perl
	PHP: source.php
	Regular Expression(python): source.regexp.python
	Python: source.python
	R Console: source.r-console
	R: source.r
	Ruby on Rails: source.ruby.rails
	Ruby HAML: text.haml
	SQL(Ruby): source.sql.ruby
	Regular Expression: source.regexp
	RestructuredText: text.restructuredtext
	Ruby: source.ruby
	SASS: source.sass
	Scala: source.scala
	Shell Script: source.shell
	SQL: source.sql
	Stylus: source.stylus
	TCL: source.tcl
	HTML(TCL): text.html.tcl
	Plain text: text.plain
	Textile: text.html.textile
	XML: text.xml
	XSL: text.xml.xsl
	YAML: source.yaml

## 参考资料 ##

- [SublimeText3 snippet 编写总结](http://blog.csdn.net/chenhongwu666/article/details/50952295)