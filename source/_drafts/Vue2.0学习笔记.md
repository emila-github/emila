---
title: Vue2.0学习笔记
date: 2017-03-23 15:42:05
tags: [Vue]
---

## vue快速开始 ##

github 地址: https://github.com/vuejs/vue-cli

	# 全局安装 vue-cli
	$ npm install --global vue-cli
	# 创建一个基于 webpack 模板的新项目
	$  vue init webpack my-project
	# 安装依赖，走你
	$ cd my-project
	$ npm install
	$ npm run dev

## 组件 ##
组件可以扩展 HTML 元素，封装可重用的代码。

### 使用组件 ###
#### 注册 ####

js:

	// 注册
	Vue.component('my-component', {
	  template: '<div>A custom component!</div>'
	})
	// 创建根实例
	new Vue({
	  el: '#example'
	})

html:

	<div id="example">
	  <my-component></my-component>
	</div>

渲染为：

	<div id="example">
	  <div>A custom component!</div>
	</div>

#### 局部注册 ####

	var Child = {
	  template: '<div>A custom component!</div>'
	}
	new Vue({
	  // ...
	  components: {
	    // <my-component> 将只在父模板可用
	    'my-component': Child
	  }
	})


### data-必须是函数 ###

html:

	<div id="example-2">
	  <simple-counter></simple-counter>
	  <simple-counter></simple-counter>
	  <simple-counter></simple-counter>
	</div>

js:

	Vue.component('simple-counter', {
	  template: '<button v-on:click="counter += 1">{{ counter }}</button>',
	  data: function () {
	    return {
	     counter: 0
	    }
	  }
	})
	new Vue({
	  el: '#example-2'
	})


父子组件的关系可以总结为 props down, events up 。父组件通过 props 向下传递数据给子组件，子组件通过 events 给父组件发送消息。

![](http://cn.vuejs.org/images/props-events.png)

### Prop ###
#### 使用-Prop-传递数据 ####

组件实例的作用域是孤立的。这意味着不能(也不应该)在子组件的模板内直接引用父组件的数据。要让子组件使用父组件的数据，我们需要通过子组件的props选项。

**子组件要显式地用 props** 选项声明它期待获得的数据：

js:

	Vue.component('child', {
	  // 声明 props
	  props: ['message'],
	  // 就像 data 一样，prop 可以用在模板内
	  // 同样也可以在 vm 实例中像 “this.message” 这样使用
	  template: '<span>{{ message }}</span>'
	})

然后我们可以这样向它传入一个普通字符串：

html:

	<child message="hello!"></child>



#### 动态-Prop ####

在模板中，要动态地绑定父组件的数据到子模板的props，与绑定到任何普通的HTML特性相类似，就是用 `v-bind`。每当父组件的数据变化时，该变化也会传导给子组件：

html:

	<div>
	  <input v-model="parentMsg">
	  <br>
	  <child v-bind:my-message="parentMsg"></child>
	</div>

使用 v-bind 的缩写语法通常更简单：

	<child :my-message="parentMsg"></child>



#### 使用-v-on-绑定自定义事件 ####

- 使用 $on(eventName) 监听事件
- 使用 $emit(eventName) 触发事件


		//单文件组件 l39_component_v-on_$emit.vue
		<script>
		  export default {
		    data () {
		      return {
		        total: 0
		      }
		    },
		    methods: {
		      incrementTotal: function () {
		        this.total += 1
		      }
		    },
		    components: {
		      'button-counter': {
		        template: '<button v-on:click="incr">{{ counter }}</button>',
		        data () {
		          return {
		            counter: 0
		          }
		        },
		        methods: {
		          incr: function () {
		            this.counter += 1
		            this.$emit('increment')
		          }
		        }
		      }
		    }
		  }
		</script>
		
		<template>
		  <div id="counter-event-example">
		    <p>{{ total }}</p>
		    <button-counter v-on:increment="incrementTotal"></button-counter>
		    <button-counter v-on:increment="incrementTotal"></button-counter>
		  </div>
		</template>



#### 使用自定义事件的表单输入组件 ####
自定义事件可以用来创建自定义的表单输入组件，使用 v-model 来进行数据双向绑定。

	<input v-model="something">

  ==

	<input v-bind:value="something" v-on:input="something = $event.target.value">


所以在组件中使用时，它相当于下面的简写：

	<custom-input v-bind:value="something" v-on:input="something = arguments[0]"></custom-input>

所以要让组件的 `v-model` 生效，它必须：

- 接受一个 `value` 属性
- 在有新的 value 时触发 `input` 事件

ex:

		// custom-input.vue
		// 定义通用input组件
		<template>
		  <div>
		    子msg:{{msg}} <br/>
		    <input ref="custom" :value="msg" @change="changeSubmsg($event.target.value)"><br/>
		    <input ref="custom" :value="getCurrentMsg" @change="changeSubmsg($event.target.value)">(computed通知值变化)<br/>
		  </div>
		</template>
		
		<script>
		  export default {
		    data () {
		      return {
		        // msg: this.$props.msg  // 有props msg时  该同名属性不能存在
		      }
		    },
		    props: ['msg'],
		    created () {
		      console.log('created->')
		      // this.$props.msg 优先级别高于 this.msg
		    },
		    computed: {
		      // 计算属性
		      getCurrentMsg: function () {
		        console.log('computed->')
		        return this.$props.msg
		      }
		    },
		    methods: {
		      changeSubmsg (value) {
		        // this.$refs.custom.value = value // 通过refs引用直接设置子组件值
		        this.$emit('panentEvent', value) // 触发父组件方法修改父组件子 再通过props 传入子组件
		      }
		    }
		  }
		</script>
		<style>
		
		</style>



父组件中使用 custom-input.vue

	// prop-emit.vue
	<template>
	  <div>
	    父msg:{{msg}}<br/>
	    <input v-model="msg"><br/> <br/> <br/>
	    <custom-input :msg = "msg" @panentEvent="changeMsg"></custom-input>
	  </div>
	</template>
	
	<script>
	  import customInput from './custom-input'
	  export default {
	    data () {
	      return {
	        msg: '父组件'
	      }
	    },
	    components: {
	      'custom-input': customInput
	    },
	    methods: {
	      changeMsg (msg) {
	        console.log('changeMsg')
	        this.msg = msg
	      }
	    }
	  }
	</script>
	<style>
	
	</style>



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

- [Vue 2.0教程](http://cn.vuejs.org/v2/guide/)
- [Vue 2.0 学习总结，精华全在这里了](https://mp.weixin.qq.com/s/IDZ0iNFsaimM3ZSAsL_qNg)
- [Vue 2.0 Simple Routing Example](https://github.com/chrisvfritz/vue-2.0-simple-routing-example)
- [vuejs-templates](https://github.com/vuejs-templates)
- [webstorm下vuejs开发配置](http://blog.csdn.net/caixiajia/article/details/53874267)
- [vue-router 2](http://router.vuejs.org/zh-cn/)
- [Vuex](http://vuex.vuejs.org/zh-cn/)
- [什么是 Vuex?](https://github.com/vuejs/vuex/issues/176)
- [vue-resource全攻略](http://www.doc00.com/doc/1001004eg)
- [Axios 中文说明](http://www.kancloud.cn/yunye/axios/234845)
- [Vue框架引入JS库的正确姿势](http://mp.weixin.qq.com/s/SJOzGQK9eaeVzyoG-m1tEw)
- [element](http://element.eleme.io/#/zh-CN)