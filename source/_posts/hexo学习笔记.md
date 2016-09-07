---
title: hexo学习笔记
date: 2016-09-02 20:42:05
tags: hexo
---

## Hexo简介 ##

Hexo 是一个轻量的静态博客框架。通过Hexo可以快速生成一个静态博客框架,仅需要几条命令就可以完成,相当方便。
Hexo的官方网站 [http://hexo.io](http://hexo.io) 就是托管于github的pages服务上

<!--more-->

## Hexo安装方法 ##
通过npm安装Hexo-Cli

	npm install hexo-cli -g

## Hexo配置方法 ##

新建一个需要当做博客目录的文件夹

	mkdir blog
进去之后加入hexo主程序和安装npm

	hexo init
	npm install

**文件夹大致结构如下**

- scaffolds 工具模板 scripts hexo的功能js
> scaffolds ：模板文件夹，新建文章时，Hexo 会根据 scaffold 来建立文件。Hexo 有三种默认布局： post 、 page 和 draft ，它们分别对应不同的路径。新建文件的默认布局是 post ，可以在配置文件中更改布局。用 draft 布局生成的文件会被保存到 source/_drafts 文件夹。
> 
> 假如执行 hexo new photo "My Gallery" ，Hexo会尝试在scaffolds目录中去寻找photo.md的模版文件，然后基于它创建标题为My Gallery的文章。

- source 博客资源文件夹
- source/_drafts 草稿文件夹

> Hexo提供草稿功能，在 _drafts 目录下的文章不会发表到网站上，你可以通过命令 hexo publish [layout] <title发布你的草稿，改命令会将文章移到 _posts 目录下。但是也可以设置 _config.yml 配置文件的 render_drafts 字段，使草稿默认发布到站点中。

- source/_posts 文章文件夹
> source/_post ：文件箱。（低版本的hexo还会存在一个 _draft ，这是草稿箱）除 _posts 文件夹之外，开头命名为 _ (下划线)的文件/ 文件夹和隐藏的文件将会被忽略。Markdown 和 HTML 文件会被解析并放到 public 文件夹，而其他文件会被拷贝过去

- themes 存放皮肤的文件夹
- themes/landscape 默认皮肤文件夹
- _config.yml 全局配置文件，每次更改要重启服务。
- db.json json格式的静态常量数据库
- _posts 目录：Hexo存放博客文章的文件夹
- themes 目录：存放皮肤的文件夹，默认使用官方的主题 你也可以从 hexo主题页面 下载你喜欢的主题

## 配置Hexo ##
**Hexo全局配置**

用文本编辑器修改_config.yml这个文件 大致如下 只需要自行修改几个 其他保持默认即可

通常需要修改站点名称 /URL格式 /归档设置 /disqus评论用户名 /部署配置 这几项就可以了 注意冒号后面都要添加一个半角空格 之后才是设置参数

自定义域名设置 在 source 我文件夹下面新建 CNAME 文件 里面写入你的自定义域名 并设置您的dns配置cname方式到服务提供商的给的地址即可

**网站**

参数 描述

title 网站标题

subtitle 网站副标题

description 网站描述

author 您的名字

language 网站使用的语言

timezone 网站时区。Hexo 预设使用您电脑的时区。时区列表

**网址**

参数 描述 默认值

url 网址

root 网站根目录

permalink 文章的 永久链接 格式 :year/:month/:day/:title/

permalink_default 永久链接中各部分的默认值

网站存放在子目录

如果您的网站存放在子目录中，例如 http://yoursite.com/blog，则请将您的 url 设为 http://yoursite.com/blog 并把 root 设为 /blog/。

**目录**

参数 描述 默认值

source_dir 资源文件夹，这个文件夹用来存放内容。 source

public_dir 公共文件夹，这个文件夹用于存放生成的站点文件。 public

tag_dir 标签文件夹 tags

archive_dir 归档文件夹 archives

category_dir 分类文件夹 categories

code_dir Include code 文件夹 downloads/code

i18n_dir 国际化（i18n）文件夹 :lang

skip_render 跳过指定文件的渲染，您可使用 glob 来配置路径。

**文章**

参数 描述 默认值

new_post_name 新文章的文件名称 :title.md

default_layout 预设布局 post

auto_spacing 在中文和英文之间加入空格 false

titlecase 把标题转换为 title case false

external_link 在新标签中打开链接 true

filename_case 把文件名称转换为 (1) 小写或 (2) 大写 0

render_drafts 显示草稿 false

post_asset_folder 启动 Asset 文件夹 false

relative_link 把链接改为与根目录的相对位址 false

future 显示未来的文章 true

highlight 代码块的设置

**分类 & 标签**

参数 描述 默认值

default_category 默认分类 uncategorized

category_map 分类别名

tag_map 标签别名

日期 / 时间格式

Hexo 使用 Moment.js 来解析和显示时间。

参数 描述 默认值

date_format 日期格式 MMM D YYYY

time_format 时间格式 H:mm:ss

分页

参数 描述 默认值

per_page 每页显示的文章量 (0 = 关闭分页功能) 10

pagination_dir 分页目录 page

**扩展**

参数 描述

theme 当前主题名称

deploy 部署


## 基本使用 ##

Hexo使用markdown语法的纯文本存放文章 后缀为 .md 你可以在 _post 文件夹里面新建这个后缀的 .md 文件 使用的全是UTF-8编码

也可以输入命令以生成


	//$ hexo new [layout] <title>
	//hexo n
	hexo new post <title>

如果是新建一个页面

	hexo new page <title>

看一下刚才生成的

title: title #文章标题

date: 2015-02-05 12:47:44 #文章生成时间

categories: #文章分类目录 可以省略

tags: #文章标签 可以省略

description: #你对本页的描述 可以省略

这里开始使用markdown格式输入你的正文。

多标签注意语法格式 如下:

	tags: [标签1,标签2,标签3]


想在首页文章预览添加图片可以添加photo参数 这个fancybox可以省略 如下:
	
	photos:
	    - http://xxx.com/photo.jpg

正文中可以使用 <!--more--> 设置文章摘要 如下:

以上是文章摘要
<!--more-->
以下是余下全文

more以上内容即是文章摘要，在主页显示，more以下内容点击『> Read More』链接打开全文才显示。

##Hexo部署方法 ##
写完文章之后 就可以启动本地服务器**测试**了

	hexo server  // hexo s

这个时候hexo启动localhost的4000端口 静态的网站架设完成

我们能过浏览器打开地址， [http://localhost:4000/](http://localhost:4000/) 

推荐部署在 Github 或者 Gitcafe 的pages服务上

修改后就可以部署上去了

	hexo clean #清除缓存 网页正常情况下可以忽略此条命令
	hexo g #生成静态网页
	hexo d #开始部署


`hexo g` 在本地目录下，会生成一个public的目录，里面包括了所有静态化的文件。

生成静态文件之后，如果要发布到github，还需要配置 deploy 指令。在全局的配置文件中找到 deploy ： 

	# Deployment
	## Docs: http://hexo.io/docs/deployment.html
	deploy:
	type: git
	repo: https://github.com/dwqs/dwqs.github.io.git
	branch: master   

这需要安装 hexo-deployer-git ：

	npm install hexo-deployer-git --save-dev

最后利用hexo指令发布到github：

	hexo d
	//same as
	hexo deploy


## Hexo常用插件安装与配置 ##

安装首页文章数量 存档 分类 的插件

安装本地服务器代理插件

安装发布器插件

安装更新插件 rss site-map之类的

	npm install hexo-generator-index --save
	npm install hexo-generator-archive --save
	npm install hexo-generator-category --save
	npm install hexo-generator-tag --save
	npm install hexo-server --save
	npm install hexo-deployer-git --save
	npm install hexo-deployer-heroku --save
	npm install hexo-deployer-rsync --save
	npm install hexo-deployer-openshift --save
	npm install hexo-renderer-marked@0.2 --save
	npm install hexo-renderer-stylus@0.2 --save
	npm install hexo-generator-feed@1 --save
	npm install hexo-generator-sitemap@1 --save

装完之后去全局配置文件 _config.yml 修改参数

	index_generator:
	  per_page: 10 ##首页默认10篇文章标题 如果值为0不分页
	archive_generator:
	  per_page: 10 ##归档页面默认10篇文章标题
	  yearly: true  ##生成年视图
	  monthly: true ##生成月视图
	tag_generator:
	  per_page: 10 ##标签分类页面默认10篇文章
	category_generator: 
	  per_page: 10 ###分类页面默认10篇文章
	feed:
	  type: atom ##feed类型 atom或者rss2
	  path: atom.xml ##feed路径
	  limit: 20  ##feed文章最小数量
	deploy:
	  type: git ##部署类型 其他类型自行google之
	  repo: <repository url> ##git仓库地址
	  branch: [branch] ##git 页面分支
	  message: [message] ##git message建议默认字段update 可以自定义
	  -多部署
	      deploy:
	          type: git
	          message: update  ##git message建议默认字段update 可以自定义
	          repo: 
	          github: <repository url>,[branch] ##github 仓库地址和分支
	          gitcafe: <repository url>,[branch] ##gitcafe 仓库地址和分支

更多插件可以去Hexo插件wiki找到 [https://github.com/hexojs/hexo/wiki/Plugins](https://github.com/hexojs/hexo/wiki/Plugins)


## Hexo主题设置 ##
同样编辑主题文件夹的 _config.yml

	# Header
	menu:	#导航栏连接
	Home: /
	Archives: /archives #归档页面URL
	自定义页面标题: /自定义页面URL
	rss: /atom.xml  #rss地址  默认即可
	# Content
	excerpt_link: Read More #阅读更多的文字显示
	fancybox: true #开启fancybox效果
	# Sidebar  #侧边栏设置
	sidebar: right
	widgets:
	  - category
	  - tag
	  - tagcloud
	  - archive
	  - recent_posts
	# Miscellaneous #社交网络和统计连接地址
	google_analytics: #google analytics ID
	favicon: /favicon.png #网站的favicon
	twitter:
	google_plus:
	fb_admins:
	fb_app_id:

## Hexo主题安装 ##

Execute the following command, and modify theme in _config.yml to theme-name

	$ git clone <repository> themes/<theme-name>
	//ex1: 
	$ git clone https://github.com/henryhuang/oishi.git themes/oishi
    //ex2:
 	$ git clone https://github.com/emila-github/pacman.git themes/pacman


## 参考资料 ##
- [Hexo 3.0 静态博客使用指南](http://www.tuicool.com/articles/Jva2iaA)
- [简洁轻便的博客平台: Hexo详解](http://www.tuicool.com/articles/ueI7naV)
- [使用的主题](https://github.com/dwqs/nx)
- [皮肤](https://github.com/hexojs/hexo/wiki/Themes)
- [Hexo Docs](http://www.ituring.com.cn/article/199295)