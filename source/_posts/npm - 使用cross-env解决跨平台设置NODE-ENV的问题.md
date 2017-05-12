---
title: npm - 使用cross-env解决跨平台设置NODE-ENV的问题
date: 2017-05-12 10:09:16
tags: ['npm']
---

在package.json的scripts标签下配置一系列命令，如下所示：

	"scripts": {
	    "start": "npm run clear&& NODE_ENV=development webpack-dev-server --host 0.0.0.0 --devtool eval --progress --color --profile",
	    "deploy": "npm run pre&& npm run clear&& NODE_ENV=production webpack -p --progress"
	  },

windows下运行npm start的时候会报错，'NODE_ENV' 不是内部或外部命令，也不是可运行的程序


## 解决方式 ##
安装across-env: `npm install cross-env --save-dev`

这个迷你的包能够提供一个设置环境变量的scripts，让你能够以unix方式设置环境变量，然后在windows上也能兼容运行。

在NODE_ENV=xxxxxxx前面添加cross-env就可以了。

	  "scripts": {
	    "build:sit-preview": "cross-env npm_config_report=true node build/build.js"
	  },