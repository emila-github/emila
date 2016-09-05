---
title: webpack 插件： html-webpack-plugin
date: 2016-09-02 20:42:05
tags: [webpack,html-webpack-plugin]
---

<div class="post">
		<h2>
			<a id="cb_post_title_url" href="http://www.cnblogs.com/haogj/p/5160821.html">webpack 插件： html-webpack-plugin</a>
		</h2>
		<div id="cnblogs_post_body"><p>插件地址：<a href="https://www.npmjs.com/package/html-webpack-plugin" target="_blank">https://www.npmjs.com/package/html-webpack-plugin</a></p>
<p>这个插件用来简化创建服务于 webpack bundle 的 HTML 文件，尤其是对于在文件名中包含了 hash 值，而这个值在每次编译的时候都发生变化的情况。你既可以让这个插件来帮助你自动生成 HTML 文件，也可以使用 lodash 模板加载生成的 bundles，或者自己加载这些 bundles。</p>
<h1>Installation</h1>
<p>使用 npm 安装这个插件</p>
<div class="cnblogs_code">
<pre>$ npm <span style="color: #0000ff;">install</span> html-webpack-plugin@<span style="color: #800080;">2</span> --save-dev</pre>
</div>
<p>&nbsp;</p>
<h1>Basic Usage</h1>
<p>这个插件可以帮助生成 HTML 文件，在 body 元素中，使用 script 来包含所有你的 webpack bundles，只需要在你的 webpack 配置文件中如下配置：</p>

<pre><span style="color: #0000ff;">var</span> HtmlWebpackPlugin = require('html-webpack-plugin'<span style="color: #000000;">)
</span><span style="color: #0000ff;">var</span> webpackConfig =<span style="color: #000000;"> {
  entry: </span>'index.js'<span style="color: #000000;">,
  output: {
    path: </span>'dist'<span style="color: #000000;">,
    filename: </span>'index_bundle.js'<span style="color: #000000;">
  },
  plugins: [</span><span style="color: #0000ff;">new</span><span style="color: #000000;"> HtmlWebpackPlugin()]
}</span></pre>

<p>这将会自动在 dist 目录中生成一个名为 index.html 的文件，内容如下：</p>

<pre><span style="color: #0000ff;">&lt;!</span><span style="color: #ff00ff;">DOCTYPE html</span><span style="color: #0000ff;">&gt;</span>
<span style="color: #0000ff;">&lt;</span><span style="color: #800000;">html</span><span style="color: #0000ff;">&gt;</span>
  <span style="color: #0000ff;">&lt;</span><span style="color: #800000;">head</span><span style="color: #0000ff;">&gt;</span>
    <span style="color: #0000ff;">&lt;</span><span style="color: #800000;">meta </span><span style="color: #ff0000;">charset</span><span style="color: #0000ff;">="UTF-8"</span><span style="color: #0000ff;">&gt;</span>
    <span style="color: #0000ff;">&lt;</span><span style="color: #800000;">title</span><span style="color: #0000ff;">&gt;</span>Webpack App<span style="color: #0000ff;">&lt;/</span><span style="color: #800000;">title</span><span style="color: #0000ff;">&gt;</span>
  <span style="color: #0000ff;">&lt;/</span><span style="color: #800000;">head</span><span style="color: #0000ff;">&gt;</span>
  <span style="color: #0000ff;">&lt;</span><span style="color: #800000;">body</span><span style="color: #0000ff;">&gt;</span>
    <span style="color: #0000ff;">&lt;</span><span style="color: #800000;">script </span><span style="color: #ff0000;">src</span><span style="color: #0000ff;">="index_bundle.js"</span><span style="color: #0000ff;">&gt;&lt;/</span><span style="color: #800000;">script</span><span style="color: #0000ff;">&gt;</span> 
  <span style="color: #0000ff;">&lt;/</span><span style="color: #800000;">body</span><span style="color: #0000ff;">&gt;</span>
<span style="color: #0000ff;">&lt;/</span><span style="color: #800000;">html</span><span style="color: #0000ff;">&gt;</span></pre>

<p>如果你有多个 webpack 入口点，它们都会被包含在生成的 script 元素中。</p>
<p>如果有任何的 CSS 资源包含在 webpack 输出中（例如，使用 ExtractTextPlugin 提炼出的 css ），这些将会使用 link 包含在 HTML 页面的 head 元素中。</p>
<h1>Configuration</h1>
<p>&nbsp;可以进行一系列的配置，支持如下的配置信息</p>
<ul>
<li>title: 用来生成页面的 title 元素</li>
<li>filename: 输出的 HTML 文件名，默认是 index.html, 也可以直接配置带有子目录。</li>
<li>template: 模板文件路径，支持加载器，比如 html!./index.html</li>
<li>inject: true | 'head' | 'body' | false &nbsp;,注入所有的资源到特定的 template 或者 templateContent 中，如果设置为 true 或者 body，所有的 javascript 资源将被放置到 body 元素的底部，'head' 将放置到 head 元素中。</li>
<li>favicon: 添加特定的 favicon 路径到输出的 HTML 文件中。</li>
<li>minify: {} | false , 传递 html-minifier 选项给 minify 输出</li>
<li>hash: true | false, 如果为 true, 将添加一个唯一的 webpack 编译 hash 到所有包含的脚本和 CSS 文件，对于解除 cache 很有用。</li>
<li>cache: true | false，如果为 true, 这是默认值，仅仅在文件修改之后才会发布文件。</li>
<li>showErrors: true | false, 如果为 true, 这是默认值，错误信息会写入到 HTML 页面中</li>
<li>chunks: 允许只添加某些块 (比如，仅仅 unit test 块)</li>
<li>chunksSortMode: 允许控制块在添加到页面之前的排序方式，支持的值：'none' | 'default' | {function}-default:'auto'</li>
<li>excludeChunks: 允许跳过某些块，(比如，跳过单元测试的块)&nbsp;</li>
</ul>
<p>下面的示例演示了如何使用这些配置。</p>

<pre><span style="color: #000000;">{
  entry: </span>'index.js'<span style="color: #000000;">,
  output: {
    path: </span>'dist'<span style="color: #000000;">,
    filename: </span>'index_bundle.js'<span style="color: #000000;">,
    hash: </span><span style="color: #0000ff;">true</span><span style="color: #000000;">
  },
  plugins: [
    </span><span style="color: #0000ff;">new</span><span style="color: #000000;"> HtmlWebpackPlugin({
      title: </span>'My App'<span style="color: #000000;">,
      filename: </span>'assets/admin.html'<span style="color: #000000;">
    })
  ]
}</span></pre>

<p>&nbsp;</p>
<p>&nbsp;</p>
<h1>生成多个 HTML 文件</h1>
<p>通过在配置文件中添加多次这个插件，来生成多个 HTML 文件。</p>

<pre><span style="color: #000000;">{
  entry: </span>'index.js'<span style="color: #000000;">,
  output: {
    path: </span>'dist'<span style="color: #000000;">,
    filename: </span>'index_bundle.js'<span style="color: #000000;">
  },
  plugins: [
    </span><span style="color: #0000ff;">new</span> HtmlWebpackPlugin(), <span style="color: #008000;">//</span><span style="color: #008000;"> Generates default index.html </span>
    <span style="color: #0000ff;">new</span> HtmlWebpackPlugin({  <span style="color: #008000;">//</span><span style="color: #008000;"> Also generate a test.html </span>
      filename: 'test.html'<span style="color: #000000;">,
      template: </span>'src/assets/test.html'<span style="color: #000000;">
    })
  ]
}</span></pre>

<p>&nbsp;</p>
<h1>编写自定义模板</h1>
<p>如果默认生成的 HTML 文件不适合你的需要看，可以创建自己定义的模板。方便的方式是通过 inject 选项，然后传递给定制的 HTML 文件。html-webpack-plugin 将会自动注入所有需要的 CSS, js, manifest 和 favicon 文件到标记中。</p>

<pre><span style="color: #000000;">plugins: [
  </span><span style="color: #0000ff;">new</span><span style="color: #000000;"> HtmlWebpackPlugin({
    title: </span>'Custom template'<span style="color: #000000;">,
    template: </span>'my-index.html', <span style="color: #008000;">//</span><span style="color: #008000;"> Load a custom template </span>
    inject: 'body' <span style="color: #008000;">//</span><span style="color: #008000;"> Inject all scripts into the body </span>
<span style="color: #000000;">  })
]</span></pre>

<p>my-index.html 文件</p>

<pre><span style="color: #0000ff;">&lt;!</span><span style="color: #ff00ff;">DOCTYPE html</span><span style="color: #0000ff;">&gt;</span>
<span style="color: #0000ff;">&lt;</span><span style="color: #800000;">html</span><span style="color: #0000ff;">&gt;</span>
  <span style="color: #0000ff;">&lt;</span><span style="color: #800000;">head</span><span style="color: #0000ff;">&gt;</span>
    <span style="color: #0000ff;">&lt;</span><span style="color: #800000;">meta </span><span style="color: #ff0000;">http-equiv</span><span style="color: #0000ff;">="Content-type"</span><span style="color: #ff0000;"> content</span><span style="color: #0000ff;">="text/html; charset=utf-8"</span><span style="color: #0000ff;">/&gt;</span>
    <span style="color: #0000ff;">&lt;</span><span style="color: #800000;">title</span><span style="color: #0000ff;">&gt;</span><span style="background-color: #ffff00; color: #000000;">&lt;%</span><span style="background-color: #f5f5f5; color: #000000;">=</span><span style="background-color: #f5f5f5; color: #000000;"> htmlWebpackPlugin.options.title </span><span style="background-color: #ffff00; color: #000000;">%&gt;</span><span style="color: #0000ff;">&lt;/</span><span style="color: #800000;">title</span><span style="color: #0000ff;">&gt;</span>
  <span style="color: #0000ff;">&lt;/</span><span style="color: #800000;">head</span><span style="color: #0000ff;">&gt;</span>
  <span style="color: #0000ff;">&lt;</span><span style="color: #800000;">body</span><span style="color: #0000ff;">&gt;</span>
  <span style="color: #0000ff;">&lt;/</span><span style="color: #800000;">body</span><span style="color: #0000ff;">&gt;</span>
<span style="color: #0000ff;">&lt;/</span><span style="color: #800000;">html</span><span style="color: #0000ff;">&gt;</span></pre>

<p>&nbsp;</p>
<p>如果你有模板加载器，可以使用它来解析这个模板。</p>

<pre><span style="color: #000000;">module: {
  loaders: [
    { test: </span>/\.hbs$/, loader: "handlebars"<span style="color: #000000;"> }
  ]
},
plugins: [
  </span><span style="color: #0000ff;">new</span><span style="color: #000000;"> HtmlWebpackPlugin({
    title: </span>'Custom template using Handlebars'<span style="color: #000000;">,
    template: </span>'my-index.hbs'<span style="color: #000000;">,
    inject: </span>'body'<span style="color: #000000;">
  })
]</span></pre>

<p>&nbsp;</p>
<p>另外，如果你的模式是一个字符串，可以使用 templateContent 传递它。</p>
<div class="cnblogs_code">
<pre><span style="color: #000000;">plugins: [
  </span><span style="color: #0000ff;">new</span><span style="color: #000000;"> HtmlWebpackPlugin({
    inject: </span><span style="color: #0000ff;">true</span><span style="color: #000000;">,
    templateContent: templateContentString
  })
]</span></pre>
</div>
<p>&nbsp;</p>
<p>如果 inject 特性不适合你的需要，你希望完全控制资源放置。 可以直接使用 lodash 语法，使用 &nbsp;<a href="https://github.com/ampedandwired/html-webpack-plugin/blob/master/default_index.ejs">default template</a>&nbsp;作为起点创建自己的模板。</p>
<p>templateContent 选项也可以是一个函数，以便使用其它语言，比如 jade：</p>

<pre><span style="color: #000000;">plugins: [
  </span><span style="color: #0000ff;">new</span><span style="color: #000000;"> HtmlWebpackPlugin({
    templateContent: </span><span style="color: #0000ff;">function</span><span style="color: #000000;">(templateParams, compilation) {
      </span><span style="color: #008000;">//</span><span style="color: #008000;"> Return your template content synchronously here </span>
      <span style="color: #0000ff;">return</span> '..'<span style="color: #000000;">;
    }
  })
]</span></pre>

<p>&nbsp;</p>
<p>或者异步版本</p>

<pre><span style="color: #000000;">plugins: [
  </span><span style="color: #0000ff;">new</span><span style="color: #000000;"> HtmlWebpackPlugin({
    templateContent: </span><span style="color: #0000ff;">function</span><span style="color: #000000;">(templateParams, compilation, callback) {
      </span><span style="color: #008000;">//</span><span style="color: #008000;"> Return your template content asynchronously here </span>
      callback(<span style="color: #0000ff;">null</span>, '..'<span style="color: #000000;">);
    }
  })
]</span></pre>

<p>&nbsp;</p>
<p>注意，如果同时使用 template 和 templateContent ，插件会抛出错误。</p>
<p>变量 o 在模板中是在渲染时传递进来的数据，这个变量有如下的属性：</p>
<ul>
<li>htmlWebpackPlugin: 这个插件的相关数据

<li>htmlWebpackPlugin.files: 资源的块名，来自 webpack 的 stats 对象，包含来自 entry 的从 entry point name 到 bundle 文件名映射。</li>
<li>

<pre>"htmlWebpackPlugin"<span style="color: #000000;">: {
  </span>"files"<span style="color: #000000;">: {
    </span>"css": [ "main.css"<span style="color: #000000;"> ],
    </span>"js": [ "assets/head_bundle.js", "assets/main_bundle.js"<span style="color: #000000;">],
    </span>"chunks"<span style="color: #000000;">: {
      </span>"head"<span style="color: #000000;">: {
        </span>"entry": "assets/head_bundle.js"<span style="color: #000000;">,
        </span>"css": [ "main.css"<span style="color: #000000;"> ]
      },
      </span>"main"<span style="color: #000000;">: {
        </span>"entry": "assets/main_bundle.js"<span style="color: #000000;">,
        </span>"css"<span style="color: #000000;">: []
      },
    }
  }
}</span></pre>

<p>&nbsp;如果在 webpack 配置文件中，你配置了 publicPath，将会反射正确的资源</p>
</li>
<li>htmlWebpackPlugin.options: 传递给插件的配置。</li>
<li>webpack: webpack 的 stats 对象。</li>
<li>webpackConfig: webpack 配置信息。</li>
</ul>
<h1>过滤块</h1>
<p>可以使用 chunks 来限定特定的块。</p>
<div class="cnblogs_code">
<pre><span style="color: #000000;">plugins: [
  </span><span style="color: #0000ff;">new</span><span style="color: #000000;"> HtmlWebpackPlugin({
    chunks: [</span>'app'<span style="color: #000000;">]
  })
]</span></pre>
</div>
<p>&nbsp;</p>
<p>还可以使用 excludeChunks 来排除特定块。</p>
<div class="cnblogs_code">
<pre><span style="color: #000000;">plugins: [
  </span><span style="color: #0000ff;">new</span><span style="color: #000000;"> HtmlWebpackPlugin({
    excludeChunks: [</span>'dev-helper'<span style="color: #000000;">]
  })
]</span></pre>
</div>
<p>&nbsp;</p>
<h1>事件</h1>
<p>通过事件允许其它插件来扩展 HTML。</p>
<ul>
<li><code>html-webpack-plugin-before-html-processing</code></li>
<li><code>html-webpack-plugin-after-html-processing</code></li>
<li><code>html-webpack-plugin-after-emit</code></li>
</ul>
<p>使用方式：</p>
<div class="cnblogs_code">
<pre>compilation.plugin('html-webpack-plugin-before-html-processing', <span style="color: #0000ff;">function</span><span style="color: #000000;">(htmlPluginData, callback) {
  htmlPluginData.html </span>+= 'The magic footer'<span style="color: #000000;">;
  callback();
});</span></pre>
</div>
<p>&nbsp;</p></div><div id="MySignature"></div>
<div class="clear"></div>



	</div>