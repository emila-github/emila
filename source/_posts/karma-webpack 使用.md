---
title: karma-webpack 使用
date: 2016-09-18 17:13:00
tags: [karma,mocha,webpack]
---


## karma-webpack 使用 ##

### Install ###

	$ npm i -D karma-webpack

## Usage ##

### 生成` karma.conf.js`  配置 ###

	$ karma init

karma.conf.js 文件内容如下：

	// karma.conf.js	
	// Karma configuration
	// Generated on Sun Sep 18 2016 16:38:58 GMT+0800 (中国标准时间)
	
	module.exports = function(config) {
	  config.set({
	
	    // base path that will be used to resolve all patterns (eg. files, exclude)
	    basePath: '',
	
	
	    // frameworks to use
	    // available frameworks: https://npmjs.org/browse/keyword/karma-adapter
	    frameworks: ['mocha'],
	
	
	    // list of files / patterns to load in the browser
	    files: [
	    ],
	
	
	    // list of files to exclude
	    exclude: [
	    ],
	
	
	    // preprocess matching files before serving them to the browser
	    // available preprocessors: https://npmjs.org/browse/keyword/karma-preprocessor
	    preprocessors: {
	    },
	
	
	    // test results reporter to use
	    // possible values: 'dots', 'progress'
	    // available reporters: https://npmjs.org/browse/keyword/karma-reporter
	    reporters: ['progress'],
	
	
	    // web server port
	    port: 9876,
	
	
	    // enable / disable colors in the output (reporters and logs)
	    colors: true,
	
	
	    // level of logging
	    // possible values: config.LOG_DISABLE || config.LOG_ERROR || config.LOG_WARN || config.LOG_INFO || config.LOG_DEBUG
	    logLevel: config.LOG_INFO,
	
	
	    // enable / disable watching file and executing tests whenever any file changes
	    autoWatch: true,
	
	
	    // start these browsers
	    // available browser launchers: https://npmjs.org/browse/keyword/karma-launcher
	    browsers: ['Chrome'],
	
	
	    // Continuous Integration mode
	    // if true, Karma captures browsers, runs the tests and exits
	    singleRun: false,
	
	    // Concurrency level
	    // how many browser should be started simultaneous
	    concurrency: Infinity
	  })
	}



### 修改 Karma 配置 ###

	// karma.conf.js
	// Karma configuration
	module.exports = function(config) {
	  config.set({
	    // ... normal karma configuration
	    files: [
	      // all files ending in "_test"
	      {pattern: 'test/*.test.js', watched: false},
	      {pattern: 'test/**/*.test.js', watched: false}
	      // each file acts as entry point for the webpack configuration
	    ],
	
	    preprocessors: {
	      // add webpack as preprocessor
	      'test/*.test.js': ['webpack'],
	      'test/**/*.test.js': ['webpack']
	    },
	
	    webpack: {
	      // karma watches the test entry points
	      // (you don't need to specify the entry option)
	      // webpack watches dependencies
	
	      // webpack configuration
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
	    },
	
	    webpackMiddleware: {
	      // webpack-dev-middleware configuration
	      // i. e.
	      stats: 'errors-only'
	    }
	  });
	};

### 也可以用以下方法统一配置 Karma ###

	// karma.conf.js

	files: [
	  // only specify one entry point
	  // and require all tests in there
	  'test/test_index.js'
	],
	
	preprocessors: {
	  // add webpack as preprocessor
	  'test/test_index.js': ['webpack']
	},



	// test/test_index.js
	
	// require all modules ending in ".test" from the
	// current directory and all subdirectories
	var testsContext = require.context(".", true, /.test$/);
	testsContext.keys().forEach(testsContext);


### Source Maps ###

	$ npm install --save-dev karma-sourcemap-loader

修改 Karma 的 preprocessors 配置

	    preprocessors: {
	      // add webpack as preprocessor
	      'test/*.test.js': ['webpack', 'sourcemap'],
	      'test/**/*.test.js': ['webpack', 'sourcemap']
	    },

并把生成的 sourcemap 告诉 webpack

	webpack: {
	  // ...
	  devtool: 'inline-source-map'
	}


## 运行测试用例 ##

	$ karma start


## 资料 ##
- [karma-webpack](https://github.com/webpack/karma-webpack)