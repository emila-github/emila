---
title: sublime-jsdocs 的使用
date: 2016-09-02 20:42:05
tags: [Sublime Text,jsdocs]
---
## sublime-jsdocs 的使用 ##

DocBlockr(v2.11.6) 是 sublime的插件包，目前支持 Sublime Text 2 & 3。 DocBlockr 支持 Javascript, PHP, ActionScript, CoffeeScript, Java, Groovy, Objective C, C and C++.的注释的快速生成。

## 安装 ##
 安装控件需要安装 [Package Control](http://wbond.net/sublime_packages/package_control)。如果你已经具备了以上条件，在sublime中按下` Ctrl + Shift + p `选择 `Package Control: Install Package` 后， 搜索 `DocBlockr` 并选中，这就开始安装了。

## 使用 ##

在新的一行中输入 `/**` 后按下 `enter` 或者 `tab`


![](/images/sublime-jsdoc-01.gif)

一个星号的注释使用方法

![](/images/sublime-jsdoc-02.gif)


为一个函数添加注释,函数的名称和参数，在函数前输入 `/**` 后回车，他会自动解析并自动添加注释。

![](/images/sublime-jsdoc-03.gif)

在生成注释后， 按 `tab` 快速切换需要修改的地方

![](/images/sublime-jsdoc-04.gif)

他还提供了对其他语言的支持

![](/images/sublime-jsdoc-05.gif)

DocBlockr 会尝试的去猜测 function 的返回值
- 如果方法名中以 "set" 或 "add" 开头，它将不会为注释插入 `@return`. 如： `function setName() {...}`
- 如果方法名中以 "is" 或 "has" 开头，它将为注释 `@return` 设置为 `Boolean`. 如： `@return {Boolean}`
- 在Javascript中,如果函数以一个大写字母开始,并假定函数定义为一个类，此时不添加@return标记。


## 变量的文档 ##

如果在新的一行声明一个变量，在 `/**` 后 按下 `shift+enter` , DocBlocker 将试着猜测变量的数据类型，并插入响应类型注释。

![](/images/sublime-jsdoc-06.gif)


DocBlocker 除了视图判断以 is 或 has 这些开头命名的参数为 booleans 类型为，还将 callback, cb, done, fn, 和 next 判断成 Function 类型。例子如下：


	/**
	 * [isMe description]
	 *
	 * @method isMe
	 *
	 * @param  {Boolean}  isA      [description]
	 * @param  {[type]}   isb      [description]
	 * @param  {Function} callback [description]
	 * @param  {Function} cb       [description]
	 * @param  {Function} done     [description]
	 * @param  {Function} fn       [description]
	 * @param  {Function} next     [description]
	 *
	 * @return {Boolean}           [description]
	 */
	function isMe(isA, isb, callback, cb, done, fn, next){
		return a;
	}

用户还可以通过自定义规则完成预判断。比如下面的的例子中设定了 `b` 开头的参数是 `bool` 类型。这些设定可以通过修改 `Base File.sublime-settings` 文件中的 `jsdocs_notation_map`属性

	{
	    "jsdocs_notation_map": [
	        {
	            "prefix": "b", // a prefix, matches only if followed by an underscore or A-Z
	            "type": "bool" // translates to "Boolean" in javascript, "bool" in PHP
	        },
	        {
	            "regex": "tbl_?[Rr]ow", // any arbitrary regex to test against the variable name
	            "type": "TableRow"      // you can add your own types
	        }
	    ]
	}

下面我们来添加一个私有方法猜测的配置，这个配置意思是以 `_` 开头命名的方法都被预判为私有方法，在生成注释时会在注释文档中添加 `@private`

	{
	    "jsdocs_notation_map": [
			{
			    "prefix": "_",
			    "tags": ["@private"]
			}
	    ]
	}

## 注释其他说明 ##

在docblock文档流内按下回车，文档会自动加` *`

![](/images/sublime-jsdoc-07.gif)
![](/images/sublime-jsdoc-08.gif)

使用 `//` 后换行， docbolck 会在新的一行自动加上 `//`

![](/images/sublime-jsdoc-09.gif)

如果你想终止智能提速，你可以通过按下 `shift+enter` 去停止自动预测。

有时候我们的参数说明可能很长，我们可以在换行后按下 `tab` 实现快速缩进。

![](/images/sublime-jsdoc-10.gif)


## 修饰类注释 ##

有时候你会修以下类型的修饰类注释

	/////////////////
	// Foo bar baz //
	/////////////////

你可以通过输入 `// Foo bar baz` 后按下<<`Ctrl+Enter`>> 来快速实现。


## 添加额外的标签 ##

可以在docblock中输入 `@` 获得[JSDoc](http://code.google.com/p/jsdoc-toolkit/wiki/TagReference), [Google Closure Compiler](http://code.google.com/p/jsdoc-toolkit/wiki/TagReference), [YUIDoc](http://code.google.com/p/jsdoc-toolkit/wiki/TagReference) ， [PHPDoc](http://phpdoc.org/).的全部支持的列表。  

## 配置 ##
你可以通过 ` Preferences -> Package Settings -> DocBlockr -> settings default` 进入 `Base File.sublime-settings` 文件中修改相应配置。

具体的进入文件就可以看到举例


因为我用的是yuidoc来生成文档，这里需要把 `jsdocs_autoadd_method_tag` 设置成 `true`。




## 参考资料 ##
[sublime-jsdocs](https://github.com/spadgos/sublime-jsdocs)
