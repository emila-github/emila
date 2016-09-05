---
title: SVG - 学习笔记
date: 2016-09-02 20:42:05
tags: [svg]
---
# SVG - 学习笔记 #

## SVG Shapes ##
SVG有一些预定义的形状元素，可被开发者使用和操作：

- 矩形 `<rect>`
- 圆形 `<circle>`
- 椭圆 `<ellipse>`
- 线 `<line>`
- 折线 `<polyline>`
- 多边形 `<polygon>`
- 路径 `<path>`


## 圆形 `<circle>`##

	<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
	  <circle cx="100" cy="50" r="40" stroke="black"
	  stroke-width="2" fill="red"/>
	</svg>

**代码解析:**

SVG 代码以 `<svg> `元素开始，包括开启标签 <svg> 和关闭标签 </svg> 。这是根元素。
width 和 height 属性可设置此 SVG 文档的宽度和高度。
version 属性可定义所使用的 SVG 版本，xmlns 属性可定义 SVG 命名空间。

- SVG 的 `<circle>` 用来**创建一个圆**。
- `cx` 和 `cy` 属性定义**圆中心的 x 和 y 坐标**。如果忽略这两个属性，那么圆点会被设置为 **(0, 0)**。
- `r` 属性定义圆的半径。
- `stroke` 和 `stroke-width` 属性控制如何显示形状的轮廓。我们把圆的轮廓设置为**黑边框**， **2px 宽**。
- `fill` 属性设置**形状内的颜色**。我们把填充颜色设置为红色。


## 矩形 - `<rect>` ##

		<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
		  <rect width="300" height="100"
		  style="fill:rgb(0,0,255);stroke-width:1;stroke:rgb(0,0,0)"/>
		</svg>

**代码解析:**

- rect 元素的 width 和 height 属性可定义矩形的高度和宽度
- style 属性用来定义 CSS 属性
- CSS 的 fill 属性定义矩形的填充颜色（rgb 值、颜色名或者十六进制值）
- CSS 的 stroke-width 属性定义矩形边框的宽度
- CSS 的 stroke 属性定义矩形边框的颜色

		<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
		  <rect x="50" y="20" width="150" height="150"
		  style="fill:blue;stroke:pink;stroke-width:5;fill-opacity:0.1;
		  stroke-opacity:0.9"/>
		</svg>

**代码解析:**

- x 属性定义矩形的左侧位置（例如，x="0" 定义矩形到浏览器窗口左侧的距离是 0px）
- y 属性定义矩形的顶端位置（例如，y="0" 定义矩形到浏览器窗口顶端的距离是 0px）
- CSS 的 `fill-opacity` 属性定义填充颜色透明度（合法的范围是：0 - 1）
- CSS 的 `stroke-opacity` 属性定义笔触颜色的透明度（合法的范围是：0 - 1）


		<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
		  <rect x="50" y="20" rx="20" ry="20" width="150" height="150"
		  style="fill:red;stroke:black;stroke-width:5;opacity:0.5"/>
		</svg>


**代码解析:**

- CSS 的 `opacity` 属性定义整个元素的**不透明度**（合法的范围是：0 - 1）

		<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
		  <rect x="50" y="20" rx="20" ry="20" width="150" height="150"
		  style="fill:red;stroke:black;stroke-width:5;opacity:0.5"/>
		</svg>

**代码解析:**

- `rx` 和 `ry` 属性可使**矩形产生圆角**。


## 椭圆 - `<ellipse>` ##

椭圆与圆很相似。不同之处在于椭圆有不同的x和y半径，而圆的x和y半径是相同的：

		<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
		  <ellipse cx="300" cy="80" rx="100" ry="50"
		  style="fill:yellow;stroke:purple;stroke-width:2"/>
		</svg>


**代码解析：**

- `CX`属性定义的椭圆中心的x坐标
- `CY`属性定义的椭圆中心的y坐标
- `RX`属性定义的水平半径
- `RY`属性定义的垂直半径


## 直线 - `<line>` ##

`<line>` 元素是用来创建一个直线：

	<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
	  <line x1="0" y1="0" x2="200" y2="200"
	  style="stroke:rgb(255,0,0);stroke-width:2"/>
	</svg>

**代码解析：**

- x1 属性在 x 轴定义线条的开始
- y1 属性在 y 轴定义线条的开始
- x2 属性在 x 轴定义线条的结束
- y2 属性在 y 轴定义线条的结束



## 多边形 - `<polygon>` ##

`<polygon>` 标签用来创建含有不少于三个边的图形。

多边形是由直线组成，其形状是"封闭"的（所有的线条 连接起来）。
> polygon来自希腊。 "Poly" 一位 "many" ， "gon" 意味 "angle".

	<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
	  <polygon points="200,10 250,190 160,210"
	  style="fill:lime;stroke:purple;stroke-width:1"/>
	</svg>

**代码解析：**

- `points` 属性定义多边形每个角的 x 和 y 坐标


下面的示例创建一个**四边的多边形**：

	<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
	  <polygon points="220,10 300,210 170,250 123,234"
	  style="fill:lime;stroke:purple;stroke-width:1"/>
	</svg>


使用 <polygon> 元素创建**一个星型**:

	<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
	  <polygon points="100,10 40,180 190,60 10,60 160,180"
	  style="fill:lime;stroke:purple;stroke-width:5;fill-rule:nonzero;" />
	</svg>

-  `fill-rule` 属性为 "nonezero|evenodd":

## 曲线 - `<polyline>` ##

`<polyline>` 元素是用于创建任何只有直线的形状：

	<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
	  <polyline points="20,20 40,25 60,40 80,120 120,140 200,180"
	  style="fill:none;stroke:black;stroke-width:3" />
	</svg>


## 路径 - `<path>` ##

`<path>` 元素用于定义一个路径。

**下面的命令可用于路径数据：**

- M = moveto
- L = lineto
- H = horizontal lineto
- V = vertical lineto
- C = curveto
- S = smooth curveto
- Q = quadratic Bézier curve
- T = smooth quadratic Bézier curveto
- A = elliptical Arc
- Z = closepath



 
SVG路径中的A指令有7个参数，分别控制曲线的的各个属性。下面解释一下参数的含义：rx, 弧的半长轴长度
ry 弧的半短轴长度
x-axis-rotation 是此段弧所在的x轴与水平方向的夹角，即x轴的逆时针旋转角度，负数代表顺时针转动的角度。
large-arc-flag 为1 表示大角度弧线，0 代表小角度弧线。
sweep-flag 为1代表从起点到终点弧线绕中心顺时针方向，0 代表逆时针方向。
x,y 是弧终端坐标。

> s和s命令是绘制“光滑”三次贝塞尔曲线的命令。一条复杂的曲线由多个曲线弧段所构成，弧段与弧段之间要光滑衔接，各个弧段的控制点必须满足一定条件。首先，这一段曲线弧的起点必须是前一段曲线弧的终点，否则连不上；其次，这一段曲线弧的第一控制点必须与前一段曲线弧的第二控制点呈对称关系，对称中心是这段曲线弧的起点，只有这样才能保证曲线衔接处的光滑。S和s命令的语法是“S X2 y2 destx desty”，省略了光滑曲线弧所隐含的第一个控制点的坐标。命令执行完后，当前点坐标同样停留在最后绘制的一段曲线弧的终点上。

> 椭圆弧曲线命令用A或a来表示。其语法比较复杂，是"A rx ry x-axis-rotation large-arc-flag sweep-flag x y"  "x-axis-rotation"是此段弧所在的椭圆的X轴与水平方向的夹角，也即x轴的 旋转角度;large-arc-flag、sweep-flag决定了椭圆弧的绘制方向，值是0或1；(x，y)是椭圆弧
终点坐标。至于圆心坐标则是自动计算出来的。


> **注意：**以上所有命令均允许小写字母。**大写表示绝对定位(相对M定位)，小写表示相对定位（相对上一个点定位）**。

例子定义了一条路径，它开始于位置150 0，到达位置75 200，然后从那里开始到225 200，最后在150 0关闭路径 ：

	<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
	  <path d="M150 0 L75 200 L225 200 Z" />
	</svg>




使用**贝兹曲线流畅的曲线模型**，可无限期的缩放。一般情况下，用户选择两个端点和一个或两个控制点。一个一个控制点的贝塞尔曲线被称为二次贝塞尔曲线和两个控制点的那种被称为立方体。

下面的例子创建了一个二次贝塞尔曲线，**A和C分别是起点和终点，B是控制点**  ：



		<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
		  <path id="lineAB" d="M 100 350 l 150 -300" stroke="red"
		  stroke-width="3" fill="none" />
		  <path id="lineBC" d="M 250 50 l 150 300" stroke="red"
		  stroke-width="3" fill="none" />
		  <path d="M 175 200 l 150 0" stroke="green" stroke-width="3"
		  fill="none" />
		  <path d="M 100 350 q 150 -300 300 0" stroke="blue"
		  stroke-width="5" fill="none" />
		  <!-- Mark relevant points -->
		  <g stroke="black" stroke-width="3" fill="black">
		    <circle id="pointA" cx="100" cy="350" r="3" />
		    <circle id="pointB" cx="250" cy="50" r="3" />
		    <circle id="pointC" cx="400" cy="350" r="3" />
		  </g>
		  <!-- Label the points -->
		  <g font-size="30" font="sans-serif" fill="black" stroke="none"
		  text-anchor="middle">
		    <text x="100" y="350" dx="-30">A</text>
		    <text x="250" y="50" dy="-10">B</text>
		    <text x="400" y="350" dx="30">C</text>
		  </g>
		</svg>



### SVG路径中的A指令（画弧线） ###

**绘制圆弧指令：**`A rx ry x-axis-rotation large-arc-flag sweep-flag x y`
画笔从当前的点绘制一段圆弧到点(x,y)


SVG路径中的A指令有7个参数，分别控制曲线的的各个属性。下面解释一下参数的含义：

- rx, 弧的半长轴长度
- ry 弧的半短轴长度
- x-axis-rotation 是此段弧所在的x轴与水平方向的夹角，即x轴的逆时针旋转角度，负数代表顺时针转动的角度。
- large-arc-flag 为1 表示大角度弧线，0 代表小角度弧线。
- sweep-flag 为1代表从起点到终点弧线绕中心顺时针方向，0 代表逆时针方向。
- x,y 是弧终端坐标。
- x-axis-rotation代表旋转的角度

体会下面例子中圆弧的不同：
 
	<svg width="320px" height="320px">
	  <path d="M10 315
	           L 110 215
	           A 30 50 0 0 1 162.55 162.45
	           L 172.55 152.45
	           A 30 50 -45 0 1 215.1 109.9
	           L 315 10" stroke="black" fill="green" stroke-width="2" fill-opacity="0.5"/>
	</svg>


## 文本 - `<text>` ##

	<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
	  <text x="0" y="15" fill="red" transform="rotate(30 20,40)">I love SVG</text>
	</svg>
