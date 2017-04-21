---
title: http-proxy-middleware
date: 2017-04-21 13:08:05
tags: [npm, proxy]
---

## Install ##

	npm install http-proxy-middleware --save-dev

## Core concept ##


- context 匹配对应请求的的URL地址, 匹配的请求将被代理到目标主机
- options.target 目标主机地址

## Example ##

	var express = require('sxpress');
	var proxy = require('http-proxy-middleware');
	
	var context = '/object/api';//context 可以使一个数组['/object/api','/object2/api',...] 
	var options = {
	    target: 'http://www.target.org',//目标服务器地址
	    changeOrigin: true,             //虚拟主机网站需要
	    headers: {                      //添加token,用于开发
	        'Authorization': 'Bearer ' + token,
	        'x-api-version': 1
	    }
	}
	
	var apiProxy =  proxy(context, options);
	var app = express();
	    app.use(apiProxy);
	    app.listen(3000);


## 资料 ##
- [http-proxy-middleware](https://www.npmjs.com/package/http-proxy-middleware)
- [npm模块之http-proxy-middleware使用教程（译）](http://blog.csdn.net/xmloveth/article/details/56847456)
- [http-proxy-middleware示例](http://blog.csdn.net/crasslandWolf/article/details/51276785)

