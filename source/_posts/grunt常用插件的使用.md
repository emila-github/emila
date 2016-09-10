---
title: grunt常用插件的使用
date: 2013-10-17 15:04:52
tags: [grunt]
---

# grunt常用插件的使用 #

## [grunt-contrib-concat](https://npmjs.org/package/grunt-contrib-concat) ##
用于合并任意文件

安装插件： `npm install grunt-contrib-concat --save-dev`

注册插件： `grunt.loadNpmTasks('grunt-contrib-concat');`

（后面的插件演示就不再贴安装插件和注册插件的代码，大同小异。）

任务：合并src下的js文件到build目录，合并后文件名为built.js。
	
	grunt.initConfig({
	     concat: {
	         options: {
	             //文件内容的分隔符
	             separator: ';'
	         },
	         dist: {
	             src: ['src/*.js'],
	             dest: 'build/built.js'
	         }
	     }
	 });

向文件追加一些额外信息：

	grunt.initConfig({
	     pkg: grunt.file.readJSON('package.json'),
	     concat: {
	         options: {
	             //文件内容的分隔符
	             separator: ';',
	             stripBanners: true,
	             banner: '/*! <%= pkg.name %> - v<%= pkg.version %> - ' +
	                         '<%= grunt.template.today("yyyy-mm-dd") %> */'
	         },
	         dist: {
	         }
	     }
	 });

自定义进程函数，比如你需要在合并文件前，对文件名进行处理等。
	
	grunt.initConfig({
	     pkg: grunt.file.readJSON('package.json'),
	     concat: {
	         options: {
	              // Replace all 'use strict' statements in the code with a single one at the top
	             banner: "'use strict';\n",
	             process: function(src, filepath) {
	                     return '// Source: ' + filepath + '\n' +
	                              src.replace(/(^|\n)[ \t]*('use strict'|"use strict");?\s*/g, '$1');
	             }
	         },
	         dist: {
	         }
	     }
	 });



## [grunt-contrib-copy](https://npmjs.org/package/grunt-contrib-copy) ##

复制文件或目录的插件

	copy: {
	  main: {
	    files: [
	      {src: ['path/*'], dest: 'dest/', filter: 'isFile'}, // 复制path目录下的所有文件
	      {src: ['path/**'], dest: 'dest/'}, // 复制path目录下的所有目录和文件
	    ]
	  }
	}


## [grunt-contrib-clean](https://npmjs.org/package/grunt-contrib-clean) ##

删除文件或目录的插件

## [grunt-contrib-compress](https://npmjs.org/package/grunt-contrib-compress) ##

用于压缩文件和目录成为zip包，不是很常用。

	compress: {
	  main: {
	    options: {
	      archive: 'archive.zip'
	    },
	    files: [
	      {src: ['path/*'], dest: 'internal_folder/', filter: 'isFile'}, path下所有的js
	      {src: ['path/**'], dest: 'internal_folder2/'}, // path下的所有目录和文件
	    ]
	  }
	}


## [grunt-contrib-jshint](https://npmjs.org/package/grunt-contrib-jshint) ##
jshint用于javascript代码检查（并会给出建议），发布js代码前执行jshint任务，可以避免出现一些低级语法问题。

jshint拥有非常丰富的配置，可以自由控制检验的级别。


    jshint: {
        options: {
            //大括号包裹
            curly: true,
            //对于简单类型，使用===和!==，而不是==和!=
            eqeqeq: true,
            //对于首字母大写的函数（声明的类），强制使用new
            newcap: true,
            //禁用arguments.caller和arguments.callee
            noarg: true,
            //对于属性使用aaa.bbb而不是aaa['bbb']
            sub: true,
            //查找所有未定义变量
            undef: true,
            //查找类似与if(a = 0)这样的代码
            boss: true,
            //指定运行环境为node.js
            node: true
        },
        //具体任务配置
        files: {
            src: ['src/*.js']
        }
    }

错误摘抄：
> [L196:C6] W033: Missing semicolon. //语句结束缺少分号


jshint比较有意思的是还可以结合grunt-contrib-concat插件使用，在合并文件前（后）对js进行检查。

	grunt.initConfig({
	  concat: {
	    dist: {
	      src: ['src/foo.js', 'src/bar.js'],
	      dest: 'dist/output.js'
	    }
	  },
	  jshint: {
	    beforeconcat: ['src/foo.js', 'src/bar.js'],
	    afterconcat: ['dist/output.js']
	  }
	});

## [grunt-contrib-csslint](https://npmjs.org/package/grunt-contrib-csslint) ##

用于css代码检查，貌似css检查的需求有些鸡肋。

## [grunt-contrib-mincss](https://npmjs.org/package/grunt-contrib-mincss) ##

用于css压缩，用法相对于grunt-contrib-uglify简单很多。

	mincss: {
	  compress: {
	    files: {
	      "path/to/output.css": ["path/to/input_one.css", "path/to/input_two.css"]
	    }
	  }
	}


## [grunt-css-combo](https://npmjs.org/package/grunt-css-combo) ##

css合并的插件，用于css分模块书写时的合并（如果你不使用less、sass、stylus，建议使用这个插件）。

	css_combo: {
		files: {
		  'dest/index.combo.css': ['src/index.css'],
		},
	}

文件目录的demo请看[github](https://github.com/daxingplay/grunt-css-combo/tree/master/test/fixtures)。

src/index.css的代码如下：

	@import "./mods/mod1.css";
	@import "./mods/mod2.css";
	#content {}

通过`@import`来合并模块css文件。


## 参考资料 ##

[常用插件的使用—grunt入门指南](http://www.36ria.com/6226)
