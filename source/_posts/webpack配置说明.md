---
title: webpack配置说明
date: 2016-09-02 20:42:05
tags: [webpack]
---

## webpack配置说明 ##

	module.exports = {
	  entry: "./src/main.js",
	  output: {
	    filename: "build/build.js"
	  },
	  module: {
	    loaders: [
	       //.css 文件使用 style-loader 和 css-loader 来处理
	      { test: /\.css$/, loader: "style!css" },
	      //.js 文件使用 jsx-loader 来编译处理
	      { test: /\.js$/,    loader: "jsx-loader" }
	    ]
	  },
	  resolve: {
	    extensions: ['', '.js', '.jsx']
        fallback: [path.join(__dirname, '../node_modules')],
        alias: {
            'src': path.resolve(__dirname, '../src'),
            'assets': path.resolve(__dirname, '../src/assets'),
            'components': path.resolve(__dirname, '../src/components')
        }
	  },
	  plugins: []
	};


entry 是页面中的入口文件，比如我这边的入口文件时main.js

output: 是指页面通过webpack打包后生成的目标文件放在什么地方去，我这边是在根目录下生成build文件夹，该文件夹内有一个build.js文件；

resolve: 定义了解析模块路径时的配置，常用的就是extensions; 可以用来指定模块的后缀，这样在引入模块时就不需要写后缀，会自动补全。

plugins: 定义了需要使用的插件，比如commonsPlugin在打包多个入口文件时会提取公用的部分，生成common.js;

module.loaders：是文件的加载器，比如我们之前react需要在页面中引入jsx的js源码到页面上来，然后使用该语法，但是通过webpack打包后就不需要再引入JSXTransformer.js；看到上面的加载器；比如jsx-loader加载器就是代表JSXTransformer.js的，还有style-loader和css-loader加载器；因此在使用之前我们需要通过命令把它引入到项目上来；因此需要如下命令生成下；

jsx-loader加载器 npm install jsx-loader --save-dev


module.loader: 其中test是正则表达式，对符合的文件名使用相应的加载器. 

/.css$/会匹配 xx.css文件，但是并不适用于xx.sass或者xx.css.zip文件.

url-loader 它会将样式中引用到的图片转为模块来处理; 配置信息的参数“?limit=8192”表示将所有小于8kb的图片都转为base64形式。

entry 模块的入口文件。依赖项数组中所有的文件会按顺序打包，每个文件进行依赖的递归查找，直到所有模块都被打成包；

output：模块的输出文件，其中有如下参数：

filename: 打包后的文件名

path: 打包文件存放的绝对路径。

publicPath: 网站运行时的访问路径。

relolve.extensions: 自动扩展文件的后缀名，比如我们在require模块的时候，可以不用写后缀名的。

relolve.fallback 当 webpack 在 root（默认当前文件夹，配置时要绝对路径） 和 modulesDirectories（默认当前文件夹，相对路径）配置下面找不到相关modules，去哪个文件夹下找 modules

relolve.alias: 模块别名定义，方便后续直接引用别名，无须多写长长的地址

plugins 是插件项;



## webpack的几个命令 ##

1. webpack         // 最基本的启动webpack的方法
1. webpack -w      // 提供watch方法；实时进行打包更新
1. webpack -p      // 对打包后的文件进行压缩
1. webpack -d      // 提供source map，方便调式代码
1. webpack --colors #输出结果带彩色，比如：会用红色显示耗时较长的步骤
1. webpack --profile #输出性能数据，可以看到每一步的耗时
1. webpack --display-modules #默认情况下 node_modules 下的模块会被隐藏，加上这个参数可以显示这些被隐藏的模块



## 设置运行环境 ##
在环境变量中定义 NODE_ENV 变量帮助 node 识别环境，例如：

	//Windows
	set NODE_ENV=test 
	//Linux or OSX
	export NODE_ENV=test


参考资料

[- 30分钟手把手教你学webpack实战](http://www.cnblogs.com/tugenhua0707/p/4793265.html)

