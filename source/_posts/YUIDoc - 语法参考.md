---
title: YUIDoc 语法参考
date: 2016-09-02 20:42:05
tags: [YUIDoc]
---

# YUIDoc 语法参考 #

## YUIDoc是什么? ##

YUIDoc会根据你写的代码注释生成API文档。

[YUIDoc](http://yui.github.com/yuidoc/) 是个NodeJS 应用能将你JS代码中的注释生成HTML格式的API文档。实事上，不仅是JS，任何支持块注释（指/* */）的语言都能用。 我想你也猜到了，YUIDoc是Yahoo出品的，跟鼎鼎大名的YUI一起的。
要安装YUIDoc，你要用npm先安装好NodeJS然后使用命令npm -g install yuidocjs 即可安装YUIDoc。通过命令yuidoc <path to js folder>来使用；详细内容下面接着讲。


## 主标签 ##

### @module ###

@module 标签描述一组关联的类（对，JS 没有类，YUIDoc只是把有构造方法也归为类罢了）。如果我们用YUIDoc生成 BackboneJS的文档，那 Backbone 对象就是个module，因为它同时管理Model, Collection, View, 和 other classes。标签后面跟着写module名称。


    /**
    @module Backbone
    */
    var Backbone = Backbone || {};


### @class ###
@class 标签专门描述类的。在YUI库中通常是个构造函数。每个有@class 标签的注释块都应该有一个@static 或者 @constructor的副标签。

	/**
	@class Model
	*/
	function Model () {}


如果你的类是module的一部分，那么不必在 @class 注释里指明与module的关系，只要文件的顶部有 @module的注释即可。

### @method ###

@method 描述类中的方法。你将会用到 @return 和 @params 副标签加以说明。


### @property ###

@property 标签说明类的属性值。 @type 和 @default副标签配合使用。

	/**
	@property templateString
	*/
	this.templateString = "div";


### @event ###

@event 描述你自定义的可触发事件。YUIDoc文档里指出:

> @event 注释快近似于 @method，但无需@return ， @param 则用于说明回调方法接收的参数


## 副标签 ##

注释块可以有多个副标签，通常同时有几个并且有些类型相同，下面介绍些常用的：

### @submodule ###

如果你的module分为多个(可能在同一个文件中，可能不在)， @submodule 就为此而生：

	/**
	@module Util
	@submodule array
	*/
	Util.array = {};


### @extends ###

@extends 描述类继承关系时非常有用，声明了当前类的超类是哪个：

	/**
	@class AppView
	@extends Backbone.View
	*/
	var AppView = Backbone.View.extend({});


### @constructor ###

如果一个类可被实例化，说明它得有个构造方法。如果你用的是原型链的方式，那类的构造也应该是构造方法。那么下面的注释就非常常见了：

	/**
	@class Recipe
	@constructor
	*/
	function Recipe () {}

这事实上是上面提到的 @class 标签中应该有一个@constructor 或@static 的副标签。


### @static ###

@static是描述那些不能实例化的静态类的。 一个最好的说明就是 Math 对象，你不必实例化才能调用其带的方法。是通过这个类本身来调用的：

	/**
	@class MathHelpers
	@static
	*/
	var MathHelpers = {};

方法也可以静态化：可以实例化的类中，可能有些类级别的方法，这些方法被设计成静态的（只能被类调用）。

	/**
	@class Person
	@constructor
	*/
	function Person () {}
	 
	/**
	@method all
	@static
	*/
	Person.all = function () {};

本示例中的Person 实例的all方法即是静态的。

### @final ###
本标签描述属性和常量：值不可变。由于JS并没有什么常量的概念，你编码的模式规范可能有这样的要求，那这个标签就有用了。

	/**
	@property DATE_FORMAT
	@final
	*/
	var DATE_FORMAT = "%B %d, %Y";

### @param ###
重要标签： @param 定义了 @method (包括@constructor) 或 @event的参数。@param 后写三个信息：name 参数名， type参数类型 (可选),，description参数描述。这三个的顺序可为name type descriptio或者 type name description；参数类型必须用{}包括起来。

	/**
	@method greet
	@param person {string} The name of the person to greet
	*/
	function greet (person) {}

参数有此可选项，放入[]中表示可选参数，后接着 =someVal 表明是默认参数 (显然，只有可靠参数才会有默认值)。用 * 表示多个参数(name* 表示1个或者多个参数，[name]* 表示0个或者多个参数)。

	/**
	@class Template
	@constructor
	@param template {String} The template string
	@param [data={}] {Object} The object whose properties will be rendered in the template
	*/
	function Template (template, data) {}

### @return ###
你的方法中通常有返回值，本标签就可以描述之，别忘记写上返回值类型和说明。

	/**
	@method toHTML
	@param [template=Recipe.defaultTemplate] {Template} A template object
	@return {String} The recipe contents formatted in HTML with the default or passed-in template.
	*/
	Recipe.prototype.toHTML = function (template) {
	    return "whatever";
	};

### @type ###
上面提到过主标签 @property 。你可能想过定义这些属性的类型， @type标签就是给你这么用的。之后跟着类型，如果多个用|分隔：

	/**
	@property URL
	@type String
	*/
	URL: "http://net.tutsplus.com",
	 
	/**
	@property person
	@type String|Person|Object
	*/
	this.person = new Person();


### @private / @protected ###

传统语言中都有private 属性或者方法：不能在实例之外访问。与常量一样，JS里只是练习用的，你可以通过声明@private 来标明。注意，YUIDoc不会在生成的文档中显示这些属性或者方法（合理），所以，你可以在代码中加入一些对私人有用的信息。

	/**
	@method _toString
	@private
	*/
	var _toString = Object.prototype.toString.call;

Protected 属性或者方法是介于public和 private之间的：它们只能被实例本身或者子类访问。如果你的代码作用是这样就用@protected标签标明。

### @requires ###
如果一个 module 依赖多个module，那就用 @requires 标明：

	/**
	@module MyFramework.localstorage
	@requires MyFramework
	*/

@requires 可用逗号分隔表明同时依赖多个。


### @default ###

声明一个@property时用 @default 定义它的默认值，须配合@type用。

	/**
	@property element
	@type String
	@default "div"
	*/
	element: "div",

### @uses ###
正如我们说过，JS没有类，不过模拟个类甚至子类是可办到的。最酷的是子类还能是个混血儿（mixes）：设置从另一个类中“借”其属性和方法。这说的不是继承，因为你可能嵌套多个类(是的，YUI 等其他类库都有这功能)。如果你做了这些可以用 @uses 标明，其后分别跟上嵌套的类名。

	/**
	@class ModalWindow
	@uses Window
	@uses DragDroppable
	*/
	var ModalWindow = new Class({
	    mixes: [Window, DragDroppable],
	    ...
	});

注意：以上的示例是我编的，不过我敢肯定我见过相似的代码。

### @example ###
想在代码中加入实例说明？那就用 @example 标签，后面缩进一级跟着写上实例。多少个实例无所谓。

	/**
	@method greet
	@example
	    person.greet("Jane");
	*/
	Person.prototype.greet = function (name) {};


### @chainable ###

你肯定很熟悉jQuery的链式风格。因为方法里面返回了当前对象所以你可以调完一个方法后再调另一个方法。用@chainable标明：

	/**
	@method addClass
	@chainable
	*/
	jQuery.prototype.addClass = function (class) {
	    // stuff;
	    return this;
	}


### @deprecated / @since / @beta ###

这三个标签说明代码的支持性质的(可以是任意代码: module, class, method, 或者其他)。用 @deprecated 标明代码不再可这么用 (弃用的功能可能在今后的版本更新中被移除)。 你也可以加上点明说为何要这么做。

	/**
	@method toJSON
	@deprecated Pass the object to `JSON.parse` instead
	*/
	Something.toJSON = function () {};

@since 标签告诉读者自哪个版起代码被加进来。 @beta 标明代码是beta： YUI 建议 @beta 代码“将来是不向下兼容的”。

	/**
	@class Tooltip
	@since 1.2.3
	@constructor
	*/
	function Tooltip () {}


### @extension / @extensionfor /extension_for ###

@extension 标签(和其别名) 跟 @uses相对。用它标明哪个类在其他类中能被嵌套，不是说此类总是被嵌套，只是说明它是可以的。

	/**
	@class Draggable
	@extensionfor ModalWindow
	*/


## Comments and Markdown ##

在我们做个完整实例之前，注释块还有两个要点我要先提一提。

首先，你会常常想增加些标签标说不明的信息。或许是想说明方法的目的，或者是想说明此类如何融入大局去。那么这些内容应该放在注释块的所有标签开始之前，YUIDoc会把它们包含进文档。

	/**
	The `Router` class is used for . . .
	@class Router
	@static
	*/
	var Router = {};

第二，你希望注释生成的文档能安意愿显示成有较好的可读性的HTML格式。当然可以，甚至你注释里的代码生成文档后会按语法高亮。


## 实例 ##

学过了标签之后，让我们来个实战实例。创建一个Store的module，关联两个类：Item 和 Cart。每个Item的实例都以Item类型保存入store 的列表里：将有属性 name， price，quantity。一个Cart 实例能添加入item并且计算价格总和（含税）。这个简单实例中功能齐全将运用到我们学到的很多标签。先来看store.js.

### 创建module： ###
	
	/**
	* This module contains classes for running a store.
	* @module Store
	*/
	 
	var Store = Store || {};

### 创建税率常量： ###

	/**
	* `TAX_RATE` is stored as a percentage. Value is 13.
	    * @property TAX_RATE
	    * @static
	    * @final
	    * @type Number
	*/
	 
	Store.TAX_RATE = 13;

这是一个包含了(@final) @property 和Number @type 的属性。注意我包含了 @static：这是由于种种原因，当我们生成文档时,YUIDoc会将此属性显示为类Item的属性：看起来YUIDoc 暂不支持 module有属性的。我猜测我可能通过创建一个静态类来托管这个常量（如果深入开发还会有更多常量的），但我我留下一个警示：用类似于YUIDoc的工具，如果使用其最大的潜在功能，可能会改变你的编码习惯，你不得不认真考虑是否愿意这么做。

### 现在来看Item类： ###

	/**
	 * @class Item
	 * @constructor
	 * @param name {String} Item name
	 * @param price {Number} Item price
	 * @param quantity {Number} Item quantity (the number available to buy)
	 */
	 
	Store.Item = function (name, price, quantity) {
	    /**
	     * @property name
	     * @type String
	     */
	    this.name = name;
	    /**
	     * @property price
	     * @type String
	     */
	    this.price = price * 100;
	    /**
	     * @property quantity
	     * @type Number
	     */
	    this.quantity = quantity;
	    /**
	     * @property id
	     * @type Number
	     */
	    this.id = Store.Item._id++;
	    Store.Item.list[this.id] = this;
	};

如上所见，本构造方法有三个参数，还有三个属性都作了注释。由于我们要每个Item的ID唯一，我们需要保存一个静态（类级别）的自增ID属性，还有另一个静态的属性专门能够通过它索引到ID对应的Item。

	/**
	 * `_id` is incremented when a new item is created, so every item has a unique ID
	 * @property id
	 * @type Number
	 * @static
	 * @private
	 */
	Store.Item._id = 1;
	 
	/**
	 * @property list
	 * @static
	 * @type Object
	 */
	Store.Item.list = {};

那类 Cart呢？

	/**
	 * @class Cart
	 * @constructor
	 * @param name {String} Customer name
	 */
	 
	Store.Cart = function (name) {
	    /**
	     * @property name
	     * @type String
	     */
	    this.name = name;
	    /**
	     * @property items
	     * @type Object
	     * @default {}
	     */
	    this.items = {};
	};

注意，我们声明默认的items 属性是个空对象。

下面是方法， addItem方法中的一个参数是可选的并且有默认值，还有就是此方法是支持链式的  @chainable。

	/**
	 * Adds 1 or more of a given item to the cart, if the chosen quantity
	 * is available. If not, none are added.
	 *
	 * @method addItem
	 * @param item {Object} An `Item` Object
	 * @param [quantity=1] {Number} The number of items to add to the cart
	 * @chainable
	 */
	 
	Store.Cart.prototype.addItem = function (item, quantity) {
	    quantity = quantity || 1;
	    if (item.quantity &gt;= quantity) {
	        this.items[item.id] = this.items[item.id] || 0;
	        this.items[item.id] += quantity;
	        item.quantity -= quantity;
	    }
	    return this;
	};

最后我们要返回价格总和，注意，我们通过数学公式将值转换为小数点为两位数的美元。

	/**
	 * @method total
	 * @return {Number} tax-included total value of cart contents
	 */
	 
	Store.Cart.prototype.total = function () {
	    var subtotal, id;
	    subtotal = 0;
	    for (id in this.items) {
	        if(this.items.hasOwnProperty(id)) {
	            subtotal += Store.Item.list[id].price * this.items[id];
	        }
	    }
	    return parseFloat(((subtotal * (1 + Store.TAX_RATE / 100)) / 100).toFixed(2));
	};


如果你想进行单元测试，下面是测试代码：

	var apple, pear, book, desk, assertEquals;
	 
	assertEquals = function (one, two, msg) {
	    console.log(((one === two) ? "PASS : " : "FAIL : ") + msg);
	};
	 
	apple = new Store.Item('Granny Smith Apple', 1.00, 5);
	pear  = new Store.Item('Barlett Pear', 2.00, 3);
	book  = new Store.Item('On Writing Well', 15.99, 2);
	desk  = new Store.Item('IKEA Gallant', 123.45, 1);
	cart  = new Store.Cart('Andrew');
	 
	cart.addItem(apple, 1).addItem(book, 3).addItem(desk, 1);
	 
	assertEquals(apple.quantity, 4, "adding 1 apple removes 1 from the item quantity");
	assertEquals(book.quantity, 2, "trying to add more books than there are means none are added");
	assertEquals(cart.total(), 140.63, "total price for 1 apple and 1 desk is 140.63");


## 生成文档 ##

代码和注释都编写好后我们开始生成文档。

如果你是通过npm安装成全局的，那你就运行 yuidoc {path to js}。我这里只用运行

	yuidoc .

之后，你会在当前目前生成一个out文件夹；打开 out/index.html就看到生成的文档内容：

## 配置输出 ##

这些[配置选项](http://yui.github.com/yuidoc/args/index.html#yuidocjson-fields) 可以在运行 YUIDoc 时设置。你可以在命令行里使用，不过我喜欢做成JSON放入一个JSON 文件里使用。 在你的项目目录建立一个 yuidoc.json文件。首先设置项目信息，这些信息不会影响输出结果，不过加上总是好的：

	{
	    "name": "Documenting JavaScript with YUIDoc",
	    "description": "A tutorial about YUIDoc, for Nettuts+",
	    "version": "1.0.0",
	    "url": "http://net.tutsplus.com"
	}

然后，有些有意义的选项你可以设置，以下是对照表：

- linkNatives: 设置为 “true” 则类似String 或者 Number 类型的将连接到[MDN docs](https://developer.mozilla.org/En).
- outdir: 输出的路径
- paths: YUIDoc 将扫描的JS路径
- exclude: YUIDoc会忽略生成的路径

设置了 paths选项，运行 `yuidoc -c yuidoc.json` 即可，就算没有设置paths 只运行 yuidoc .，YUIDoc会自动找到配置文件并运用的。

以下是我这个项目的配置文件：

	{
	    "name": "Documenting JavaScript with YUIDoc",
	    "description": "A tutorial about YUIDoc, for Nettuts+",
	    "version": "1.0.0",
	    "url": "http://net.tutsplus.com",
	    "options": {
	        "linkNatives": "true",
	        "outdir": "./docs",
	        "paths": "."
	    }
	}

## 更多 ##

- [YUIDoc 0.3.0 Release Blog Post](http://www.yuiblog.com/blog/2012/05/09/yuidoc-0-3-0-is-official/)
- [YUIDoc Home Page](http://yui.github.com/yuidoc/)
- [Using YUIDoc](http://yui.github.com/yuidoc/args/index.html)
- [YUIDoc Syntax Reference](http://yui.github.com/yuidoc/syntax/index.html)
- [YUIDoc Themes](http://yui.github.com/yuidoc/themes/index.html)
- [[译]用YUIDoc文档化JavaScript代码](http://www.iunbug.com/archives/2012/06/07/296.html)