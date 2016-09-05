---
title: jshint配置说明
date: 2016-09-02 20:42:05
tags: [jshint]
---
# jshint配置说明 #
	
	{
	    "jquery": true,//检查预定义的全局变量，防止出现$未定义，该项根据实际代码修改
	    "bitwise": false,//不检查位运算
	    "browser": true,//通过浏览器内置的全局变量检测
	    "devel":true,//允许对调试用的alert和console.log的调用
	    "camelcase": false,//不强制验证驼峰式命名
	    "curly": true,//强制使用花括号
	    "eqeqeq": false,//不强制使用===比较运算符
	    "es3":true,//兼容es3规范，针对旧版浏览器编写的代码
	    "esnext": false, //不使用最新的es6规范
	    "expr": true,//允许未赋值的函数名表达式，例如console && console.log(1)
	    "forin":false,//不强制过滤遍历对象继承的属性    
	    "freeze":false,//不限制对内置对象的扩展
	    "immed": true,//禁止未用括号包含立即执行函数
	    "indent": false,//不强制缩进
	    "latedef": true,//禁止先调用后定义
	    "maxdepth":false,//不限制代码块嵌套层数
	    "maxparams":false,//不限制函数参数个数
	    "newcap": false,//不对首字母大写的函数强制使用new
	    "noarg": false,//不禁止对arguments.caller和arguments.callee的调用
	    "noempty":false,//不禁止空代码块
	    "nonew":false,//允许直接new实例化而不赋值给变量
	    "plusplus":false,//允许++和--运算符使用
	    "quotmark": "single",//字符串使用单引号
	    "scripturl": true,//允许javascript伪协议的url
	    "smarttabs": true,//允许混合tab和空格缩进
	    "strict": false,//不强制使用es5严格模式
	    "sub": true,//允许用[]形式访问对象属性
	    "undef": true,//禁止明确未定义的变量调用，如果你的变量（myvar）是在其他文件中定义的，可以使用/*global myvar */绕过检测
	    "unused": false,//允许定义没用的变量，在某些函数回调中，经常出现多个参数，但不一定会用
	    "multistr": false,//禁止多行字符串，改用加号连接
	    "globals": {
	      "jQuery": true
	    }
	}