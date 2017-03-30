---
title: Vue2.0学习笔记
date: 2017-03-23 15:42:05
tags: [Vue]
---

## 路由 ##

### 简单的路由 ###

如果只需要非常简单的路由而不需要引入整个路由库，可以动态渲染一个页面级的组件像这样： [实例应用](https://github.com/chrisvfritz/vue-2.0-simple-routing-example)

	const NotFound = { template: '<p>Page not found</p>' }
	const Home = { template: '<p>home page</p>' }
	const About = { template: '<p>about page</p>' }
	const routes = {
	  '/': Home,
	  '/about': About
	}
	new Vue({
	  el: '#app',
	  data: {
	    currentRoute: window.location.pathname
	  },
	  computed: {
	    ViewComponent () {
	      return routes[this.currentRoute] || NotFound
	    }
	  },
	  render (h) { return h(this.ViewComponent) }
	})


## 学习资料 ##
- [Vue 2.0 Simple Routing Example](https://github.com/chrisvfritz/vue-2.0-simple-routing-example)
- [webstorm下vuejs开发配置](http://blog.csdn.net/caixiajia/article/details/53874267)
- [什么是 Vuex?](https://github.com/vuejs/vuex/issues/176)