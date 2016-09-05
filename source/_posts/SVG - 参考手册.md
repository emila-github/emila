---
title: SVG - 参考手册
date: 2016-09-02 20:42:05
tags: [svg]
---

# SVG - 参考手册 #

## SVG 元素 ##

<table class="reference">
  <tbody>
    <tr>
      <th width="20%" align="left">元素</th>
      <th width="30%" align="left">说明</th>
      <th width="50%" align="left">属性</th>
    </tr>
    <tr>
      <td>&lt;a&gt;</td>
      <td>创建一个SVG元素周围链接</td>
      <td>xlink:show<br>
        xlink:actuate<br>
        xlink:href<br>
        target</td>
    </tr>
    <tr>
      <td>&lt;altGlyph&gt;</td>
      <td>允许对象性文字进行控制，来呈现特殊的字符数据</td>
      <td>x<br>
        y<br>
        dx<br>
        dy<br>
        rotate<br>
        glyphRef<br>
        format<br>
        xlink:href</td>
    </tr>
    <tr>
      <td>&lt;altGlyphDef&gt;</td>
      <td>定义一系列象性符号的替换</td>
      <td>id</td>
    </tr>
    <tr>
      <td>&lt;altGlyphItem&gt;</td>
      <td>定义一系列候选的象性符号的替换</td>
      <td>id</td>
    </tr>
    <tr>
      <td>&lt;animate&gt;</td>
      <td>随时间动态改变属性</td>
      <td>attributeName="目标属性名称"<br>
        from="起始值"<br>
        to="结束值"<br>
        dur="持续时间"<br>
        repeatCount="动画时间将发生"</td>
    </tr>
    <tr>
      <td>&lt;animateColor&gt;</td>
      <td>定义随着时间的推移颜色转换</td>
      <td>by="相对偏移值"<br>
        from="起始值"<br>
        to="结束值"</td>
    </tr>
    <tr>
      <td>&lt;animateMotion&gt;</td>
      <td>使元素沿着动作路径移动</td>
      <td>calcMode="动画的插补模式。可以是'discrete', 'linear', 'paced', 'spline'"<br>
        path="运动路径"<br>
        keyPoints="沿运动路径的对象目前时间应移动多远"<br>
        rotate="应用旋转变换"<br>
        xlink:href="一个URI引用&lt;path&gt;元素，它定义运动路径"</td>
    </tr>
    <tr>
      <td>&lt;animateTransform&gt;</td>
      <td>动画上一个目标元素变换属性，从而使动画控制平移，缩放，旋转或倾斜</td>
      <td>by="相对偏移值"<br>
        from="起始值"<br>
        to="结束值"<br>
        type="类型的转换其值是随时间变化。可以是 'translate', 'scale', 'rotate', 'skewX', 'skewY'"</td>
    </tr>
    <tr>
      <td>&lt;circle&gt;</td>
      <td>定义一个圆</td>
      <td>cx="圆的x轴坐标"<br>
        cy="圆的y轴坐标"<br>
        r="圆的半径". 必需.<br>
        <br>
        + 显现属性：颜色，FillStroke，图形</td>
    </tr>
    <tr>
      <td>&lt;clipPath&gt;</td>
      <td>用于隐藏位于剪切路径以外的对象部分。定义绘制什么和什么不绘制的模具被称为剪切路径 </td>
      <td>clip-path="引用剪贴路径和引用剪贴路径交叉"<br>
        clipPathUnits="userSpaceOnUse'或'objectBoundingBox"。第二个值childern一个对象的边框，会使用掩码的一小部分单位（默认："userSpaceOnUse"）"</td>
    </tr>
    <tr>
      <td>&lt;color-profile&gt;</td>
      <td>指定颜色配置文件的说明（使用CSS样式文件时）</td>
      <td>local="本地存储颜色配置文件唯一ID"<br>
        name=""<br>
        rendering-intent="auto|perceptual|relative-colorimetric|saturation|absolute-colorimetric"<br>
        xlink:href="ICC配置文件资源URI"</td>
    </tr>
    <tr>
      <td>&lt;cursor&gt;</td>
      <td>定义一个独立于平台的自定义光标</td>
      <td>x="x轴左上角光标（默认为0）"<br>
        y="y轴的左上角光标（默认为0）"<br>
        xlink:href="使用光标图像URI</td>
    </tr>
    <tr>
      <td>&lt;defs&gt;</td>
      <td>引用的元素容器</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>&lt;desc&gt;</td>
      <td>对 SVG 中的元素的纯文本描述 - 并不作为图形的一部分来显示。用户代理会将其显示为工具提示</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>&lt;ellipse&gt;</td>
      <td>定义一个椭圆</td>
      <td>cx="椭圆x轴坐标"<br>
        cy="椭圆y轴坐标"<br>
        rx="沿x轴椭圆形的半径"。必需。<br>
        ry="沿y轴长椭圆形的半径"。必需。<br>
        <br>
        + 显现属性：颜色，FillStroke，图形</td>
    </tr>
    <tr>
      <td>&lt;feBlend&gt;</td>
      <td>使用不同的混合模式把两个对象合成在一起</td>
      <td>mode="图像混合模式：normal|multiply|screen|darken|lighten"<br>
        in="标识为给定的滤镜原始输入：SourceGraphic | SourceAlpha | BackgroundImage | BackgroundAlpha | FillPaint | StrokePaint | &lt;filter-primitive-reference&gt;"<br>
        in2="第二输入图像的混合操作"</td>
    </tr>
    <tr>
      <td>feColorMatrix</td>
      <td>SVG滤镜。适用矩阵转换</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feComponentTransfer</td>
      <td>SVG 滤镜。执行数据的 component-wise 重映射</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feComposite</td>
      <td>SVG 滤镜</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feConvolveMatrix</td>
      <td>SVG 滤镜</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feDiffuseLighting</td>
      <td>SVG 滤镜</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feDisplacementMap</td>
      <td>SVG 滤镜</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feDistantLight</td>
      <td>SVG滤镜。定义一个光源</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feFlood</td>
      <td>SVG滤镜</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feFuncA</td>
      <td>SVG 滤镜。feComponentTransfer 的子元素</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feFuncB</td>
      <td>SVG 滤镜。feComponentTransfer 的子元素</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feFuncG</td>
      <td>SVG 滤镜。feComponentTransfer 的子元素</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feFuncR</td>
      <td>SVG 滤镜。feComponentTransfer 的子元素</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feGaussianBlur</td>
      <td>SVG滤镜。执行高斯模糊图像</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feImage</td>
      <td>SVG滤镜。</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feMerge</td>
      <td>SVG滤镜。建立在彼此顶部图像层</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feMergeNode</td>
      <td>SVG 滤镜。feMerge的子元素</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feMorphology</td>
      <td>SVG 滤镜。 对源图形执行"fattening" 或者 "thinning"</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feOffset</td>
      <td>SVG滤镜。相对其当前位置移动图像</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>fePointLight</td>
      <td>SVG滤镜</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feSpecularLighting</td>
      <td>SVG滤镜</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feSpotLight</td>
      <td>SVG滤镜</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feTile</td>
      <td>SVG滤镜</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>feTurbulence</td>
      <td>SVG滤镜</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>filter</td>
      <td>滤镜效果的容器</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>font</td>
      <td> 定义字体</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>font-face</td>
      <td>描述一种字体的特点</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>font-face-format</td>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>font-face-name</td>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>font-face-src</td>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>font-face-uri</td>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>foreignObject</td>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>&lt;g&gt;</td>
      <td>用于把相关元素进行组合的容器元素</td>
      <td>id="该组的名称"<br>
        fill="该组填充颜色"<br>
        opacity="该组不透明度"<br>
        <br>
        + 显现属性:<br>
        All</td>
    </tr>
    <tr>
      <td>glyph</td>
      <td>为给定的象形符号定义图形</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>glyphRef</td>
      <td>定义要使用的可能的象形符号</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>hkern</td>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>&lt;image&gt;</td>
      <td>定义图像</td>
      <td>x="图像的左上角的x轴坐标"<br>
        y="图像的左上角的y轴坐标"<br>
        width="图像的宽度". 必须.<br>
        height="图像的高度". 必须.<br>
        xlink:href="图像的路径". 必须.<br>
        <br>
        + 显现属性:<br>
        Color, Graphics, Images, Viewports</td>
    </tr>
    <tr>
      <td>&lt;line&gt;</td>
      <td>定义一条线</td>
      <td>x1="直线起始点x坐标"<br>
        y1="直线起始点y坐标"<br>
        x2="直线终点x坐标"<br>
        y2="直线终点y坐标"<br>
        <br>
        + 显现属性:<br>
        Color, FillStroke, Graphics, Markers</td>
    </tr>
    <tr>
      <td>&lt;linearGradient&gt;</td>
      <td>定义线性渐变。通过使用矢量线性渐变填充对象，并可以定义为水平，垂直或角渐变。</td>
      <td>id="id 属性可为渐变定义一个唯一的名称。引用必须"<br>
        gradientUnits="'userSpaceOnUse' or 'objectBoundingBox'.使用视图框或对象，以确定相对位置矢量点。 （默认为'objectBoundingBox）"<br>
        gradientTransform="适用于渐变的转变"<br>
        x1="渐变向量x启动点（默认0％）"<br>
        y1="渐变向量y启动点（默认0％）" <br>
        x2="渐变向量x的终点。 （默认100％）"<br>
        y2="渐变向量y的终点。 （默认0％）" <br>
        spreadMethod="'pad' or 'reflect' or 'repeat'"<br>
        xlink:href="reference to another gradient whose attribute values are used as defaults and stops included. Recursive"</td>
    </tr>
    <tr>
      <td>&lt;marker&gt;</td>
      <td>标记可以放在直线，折线，多边形和路径的顶点。这些元素可以使用maeker属性的"maeker-start"，"maeker-mid"和"maeker-end"，继承默认情况下或可设置为"none"或定义的标记的URI。您必须先定义标记，然后才可以通过其URI引用。任何一种形状，可以把标记放在里面。他们绘制元素时把它们附加到顶部</td>
      <td>markerUnits="strokeWidth'或'userSpaceOnUse"。如果是strokeWidth"那么使用一个单位等于一个笔划宽度。否则，标记尺度不会使用同一视图单位作为引用元素（默认为'strokeWidth'）"<br>
        refx="标记顶点连接的位置（默认为0）"<br>
        refy="标记顶点连接的位置（默认为0）"<br>
        orient="'auto'始终显示标记的角度。 "auto"将计算某个角度使得X轴一个顶点的正切值（默认为0）<br>
        markerWidth="标记的宽度（默认3）"<br>
        markerHeight="标记的高度（默认3）"<br>
        viewBox="各点"看到"这个SVG绘图区域。由空格或逗号分隔的4个值。(min x, min y, width, height)" <br>
        <br>
        + presentation attributes:<br>
        All</td>
    </tr>
    <tr>
      <td>&lt;mask&gt;</td>
      <td>度屏蔽是一种不透明度值的组合和裁剪。像裁剪，您可以使用图形，文字或路径定义掩码的部分。一个掩码的默认状态是完全透明的，也就是裁剪平面的对面的。在掩码的图形设置掩码的不透明部分</td>
      <td>maskUnits="'userSpaceOnUse' or 'objectBoundingBox'.设定裁剪面是否是相对完整的视窗或对象（默认：'objectBoundingBox'）"<br>
        maskContentUnits="第二个掩码相对对象的图形位置使用百分比'userSpaceOnUse'或'objectBoundingBox'（默认：'userSpaceOnUse'）"<br>
        x="裁剪面掩码（默认值：-10％）" <br>
        y="裁剪面掩码（默认值：-10％）" <br>
        width="裁剪面掩码（默认是：120％）"<br>
        height="裁剪面掩码（默认是：120％）"</td>
    </tr>
    <tr>
      <td>metadata</td>
      <td>指定元数据</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>missing-glyph</td>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>mpath</td>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>&lt;path&gt;</td>
      <td>定义一个路径</td>
      <td>d="定义路径指令"<br>
        pathLength="如果存在，路径将进行缩放，以便计算各点相当于此值的路径长度"<br>
        transform="转换列表"<br>
        <br>
        + 显现属性:<br>
        Color, FillStroke, Graphics, Markers</td>
    </tr>
    <tr>
      <td>&lt;pattern&gt;</td>
      <td>定义坐标，你想要的视图显示和视图的大小。然后添加到您的模式形状。该模式命中时重复视图框的边缘（可视范围）</td>
      <td>id="用于引用这个模式的唯一ID。"必需的。 <br>
        patternUnits="userSpaceOnUse'或'objectBoundingBox"。第二个值X，Y，width，height 一个会使用模式对象的边框的小部分，单位（％）。"<br>
        patternContentUnits="'userSpaceOnUse'或 'objectBoundingBox'"<br>
        patternTransform="允许整个表达式进行转换"<br>
        x="模式的偏移量，来自左上角（默认为0）" <br>
        y="模式的偏移量，来自左上角（默认为0）"<br>
        width="模式平铺的宽度（默认为100％）" <br>
        height="模式平铺的高度（默认为100％）"<br>
        viewBox="各点"看到"这个SVG绘图区域。由空格或逗号分隔的4个值。(min x, min y, width, height)" <br>
        xlink:href="另一种模式，其属性值是默认值以及任何子类可以继承。递归"<br>
        &nbsp;</td>
    </tr>
    <tr>
      <td>&lt;polygon&gt;</td>
      <td>定义一个包含至少三边图形</td>
      <td>points="多边形的点。点的总数必须是偶数"。必需的。<br>
        fill-rule="FillStroke演示属性的部分"<br>
        <br>
        + 显现属性:<br>
        Color, FillStroke, Graphics, Markers</td>
    </tr>
    <tr>
      <td>&lt;polyline&gt;</td>
      <td>定义只有直线组成的任意形状</td>
      <td>points=折线上的"点"。必需的。<br>
        <br>
        + 显现属性:<br>
        Color, FillStroke, Graphics, Markers</td>
    </tr>
    <tr>
      <td>&lt;radialGradient&gt;</td>
      <td>定义放射性渐变。放射性渐变创建一个圆圈</td>
      <td>gradientUnits="'userSpaceOnUse' or 'objectBoundingBox'. 使用视图框或对象以确定相对位置的矢量点。 （默认为'objectBoundingBox）"<br>
        gradientTransform="适用于渐变的变换" <br>
        cx="渐变的中心点（数字或％ - 50％是默认）"<br>
        cy="渐变的中心点。 （默认50％）"<br>
        r="渐变的半径。 （默认50％）" <br>
        fx="渐变的焦点。 （默认0％）"<br>
        fy="渐变的焦点。 （默认0％）"<br>
        spreadMethod="'pad' or 'reflect' or 'repeat'"<br>
        xlink:href="引用到另一个渐变，其属性值作为默认值。递归"</td>
    </tr>
    <tr>
      <td>&lt;rect&gt;</td>
      <td>定义一个矩形</td>
      <td>x="矩形的左上角的x轴"<br>
        y="矩形的左上角的y轴"<br>
        rx="x轴的半径（round元素）"<br>
        ry="y轴的半径（round元素）" <br>
        width="矩形的宽度"。必需的。<br>
        height="矩形的高度"。必需的。<br>
        <br>
        + 显现属性:<br>
        Color, FillStroke, Graphics</td>
    </tr>
    <tr>
      <td>script</td>
      <td>脚本容器。（例如ECMAScript）</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>set</td>
      <td>设置一个属性值指定时间</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>&lt;stop&gt;</td>
      <td>渐变停止</td>
      <td>offset="偏移停止（0到1/0％到100％）". 参考<br>
        stop-color="这个stop的颜色" <br>
        stop-opacity="这个Stop的不透明度 (0到1)"</td>
    </tr>
    <tr>
      <td>style</td>
      <td>可使样式表直接嵌入SVG内容内部</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>&lt;svg&gt;</td>
      <td>创建一个SVG文档片段</td>
      <td>x="左上角嵌入（默认为0）"<br>
        y="左上角嵌入（默认为0）"<br>
        width="SVG片段的宽度（默认为100％）"<br>
        height="SVG片段的高度（默认为100％）"<br>
        viewBox="点"seen"这个SVG绘图区域。由空格或逗号分隔的4个值。 (min x, min y, width, height)"<br>
        preserveAspectRatio="'none'或任何'xVALYVAL'的9种组合,VAL是"min"，"mid"或"max"。（默认情况下none）"<br>
        zoomAndPan="'magnify' or 'disable'.Magnify选项允许用户平移和缩放您的文件（默认Magnify ）"<br>
        xml="最外层&lt;svg&gt;元素都需要安装SVG和它的命名空间： xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" xml:space="preserve""<br>
        <br>
        + 显现属性:<br>
        All</td>
    </tr>
    <tr>
      <td>switch</td>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>symbol</td>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>&lt;text&gt;</td>
      <td>定义一个文本</td>
      <td>x="列表的X -轴的位置。在文本中在第n个字符的位置在第n个x轴。如果后面存在额外的字符，耗尽他们最后一个字符之后放置的位置。 0是默认"<br>
        y="列表的Y轴位置。（参考x）0是默认"<br>
        dx="在字符的长度列表中移动相对最后绘制标志符号的绝对位置。（参考x）"<br>
        dy="在字符的长度列表中移动相对最后绘制标志符号的绝对位置。（参考x）" <br>
        rotate="一个旋转的列表。第n个旋转是第n个字符。附加字符没有给出最后的旋转值"<br>
        textLength="SVG查看器将尝试显示文本之间的间距/或字形调整的文本目标长度。（默认：正常文本的长度）"<br>
        lengthAdjust="告诉查看器，如果指定长度就尝试进行调整用以呈现文本。这两个值是'spacing'和'spacingAndGlyphs'"<br>
        <br>
        + 显现属性:<br>
        Color, FillStroke, Graphics, FontSpecification, TextContentElements</td>
    </tr>
    <tr>
      <td>textPath</td>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>title</td>
      <td>对 SVG 中的元素的纯文本描述 - 并不作为图形的一部分来显示。用户代理会将其显示为工具提示</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>&lt;tref&gt;</td>
      <td>引用任何SVG文档中的&lt;text&gt;元素和重用</td>
      <td>相同的&lt;TEXT&gt;元素</td>
    </tr>
    <tr>
      <td>&lt;tspan&gt;</td>
      <td>元素等同于&lt;text&gt;，但可以在内部嵌套文本标记以及内部本身</td>
      <td>Identical to the &lt;text&gt; element<br>
        + in addition:<br>
        xlink:href="引用一个&lt;TEXT&gt;元素" </td>
    </tr>
    <tr>
      <td>&lt;use&gt;</td>
      <td>使用URI引用一个&lt;G&gt;,&lt;svg&gt;或其他具有一个唯一的ID属性和重复的图形元素。复制的是原始的元素，因此文件中的原始存在只是一个参考。原始影响到所有副本的任何改变。</td>
      <td>x="克隆元素的左上角的x轴"<br>
        y="克隆元素的左上角的y轴"<br>
        width="克隆元素的宽度"<br>
        height="克隆元素的高度"<br>
        xlink:href="URI引用克隆元素"<br>
        <br>
        + 显现属性:<br>
        All</td>
    </tr>
    <tr>
      <td>view</td>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>vkern</td>
      <td>&nbsp;</td>
      <td>&nbsp;</td>
    </tr>
  </tbody>
</table>


## 来源 ##
http://www.w3cschool.cc/svg/svg-reference.html