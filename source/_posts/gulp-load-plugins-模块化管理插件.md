---
title: 'gulp-load-plugins[模块化管理插件]'
date: 2017-02-16 16:03:05
tags: [gulp]
---


一般情况下，gulpfile.js中的模块需要一个个加载。

	var gulp = require('gulp'),
	    jshint = require('gulp-jshint'),
	    uglify = require('gulp-uglify'),
	    concat = require('gulp-concat');
	
	gulp.task('js', function () {
	   return gulp.src('js/*.js')
	      .pipe(jshint())
	      .pipe(jshint.reporter('default'))
	      .pipe(uglify())
	      .pipe(concat('app.js'))
	      .pipe(gulp.dest('build'));
	});

上面代码中，除了gulp模块以外，还加载另外三个模块。

这种一一加载的写法，比较麻烦。使用gulp-load-plugins模块，可以加载package.json文件中所有的gulp模块。上面的代码用gulp-load-plugins模块改写，就是下面这样。

假设package.json文件包含以下内容。

	{
	
	   "devDependencies": {
	      "gulp-concat": "~2.2.0",
	      "gulp-uglify": "~0.2.1",
	      "gulp-jshint": "~1.5.1",
	      "gulp": "~3.5.6"
	   }
	}

gulpfile.js中写法

	var gulp = require('gulp'),
	    gulpLoadPlugins = require('gulp-load-plugins'),
	    plugins = gulpLoadPlugins();
	
	gulp.task('js', function () {
	   return gulp.src('js/*.js')
	      .pipe(plugins.jshint())
	      .pipe(plugins.jshint.reporter('default'))
	      .pipe(plugins.uglify())
	      .pipe(plugins.concat('app.js'))
	      .pipe(gulp.dest('build'));
	});


## 来源： ##

- [gulp-load-plugins[模块化管理插件]](http://www.qianduancun.com/nodejs/33.html)
