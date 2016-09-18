---
title: mocha-webpack使用
date: 2016-09-18 15:22:00
tags: [mocha,webpack]
---

## 为什么需要这个模块 ##

正常情况下没有该模块的情况下使用 mocha 需要以下命令

	$ webpack test.js output.js && mocha output.js

这使得我们需要去做一些预编译


## 安装 mocha-webpack ##

	# install mocha, webpack & mocha-webpack as devDependencies
	$ npm install --save-dev mocha webpack mocha-webpack

安装成功后运行以下命令查看是否安装成功

	# display version of mocha-webpack
	$ node ./node_modules/mocha-webpack/bin/mocha-webpack --version
	 
	# display available commands & options of mocha-webpack
	$ node ./node_modules/mocha-webpack/bin/mocha-webpack --help


## 配置 mocha-webpack ##

在 package.json 配置以下内容


	...
	"scripts": {
	    "test": "mocha-webpack --webpack-config webpack.config-test.js \"src/**/*.test.js\"",
	  },
	...

这使你可以通过 `npm run test` 命令查看运行测试

## 新建 webpack.config-test.js ##
在根目录新建 webpack.config-test.js 并做如下配置


	var nodeExternals = require('webpack-node-externals');
	 
	module.exports = {
	  target: 'node', // in order to ignore built-in modules like path, fs, etc. 
	  externals: [nodeExternals()], // in order to ignore all modules in node_modules folder 
	};


也许你注意到在这个配置中入口，output.filename和output.path完全丢失。mocha-webpack将根据配置去重写它。

## 共享配置 ##

新建 `mocha-webpack.opts` 在文件中添加以下配置

	--colors
	--webpack-config webpack.config-test.js
	src/**/*.test.js


## Sourcemaps ##
	
	$ npm install --save-dev source-map-support

在 webpack.config-test.js 添加

	var nodeExternals = require('webpack-node-externals');
	 
	module.exports = {
	  output: {
	    // sourcemap support for IntelliJ/Webstorm 
	    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
	    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
	  }
	  target: 'node', // in order to ignore built-in modules like path, fs, etc. 
	  externals: [nodeExternals()], // in order to ignore all modules in node_modules folder 
	  devtool: "cheap-module-source-map" // faster than 'source-map' 
	};

在 mocha-webpack.opts 中添加

	--require source-map-support/register


## ES6支持 ##

mocha 中提供了 `mocha --compilers js:babel-core/register` 对es6进行预编译
，但 mocha-webpack 没有提供 --compilers，因为用到了webpack。

webpack提供了babel-loader 来处理es6 .([issues](https://github.com/zinserjan/mocha-webpack/issues/23))

在 webpack.config-test.js 添加

	module.exports = {
	 	#...
		module: {
		  loaders: [
		    {
		      test: /\.js$/,
		      exclude: /(node_modules|bower_components)/,
		      loader: 'babel', // 'babel-loader' is also a valid name to reference
		      query: {
		        presets: ['es2015']
		      }
		    }
		  ]
		}
		#...
	};


## 其他简单命令 ##

[sample-commands](https://www.npmjs.com/package/mocha-webpack#sample-commands)



## 来源 ##
- [npm mocha-webpack](https://www.npmjs.com/package/mocha-webpack)