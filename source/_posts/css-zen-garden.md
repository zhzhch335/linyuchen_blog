---
title: CSS禅境花园——我第一次领略到CSS的魔力
date: 2022-08-01 08:43:00
tags: [前端,CSS]
cover: https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/86f26bb0d1394adc8b943817fa351ea9~tplv-k3u1fbpfcp-zoom-crop-mark:3024:3024:3024:1702.awebp?
---
我的学生时代，刚开始起步学前端的时候，曾经对CSS不屑一顾，直到我发现了CSS禅境花园，我才知道CSS包含的巨大魔力……

<!-- more -->

# 开始
相信每个刚开始接触前端的初学者都会听说过，一个前端项目由三部分组成：
- HTML-网页的结构，可以理解为骨架
- JavaScript-网页的交互，可以理解为动作和头脑
- CSS-网页的样式-网页的外观，可以理解为外貌

三者的共同作用下，将枯燥无味的代码构成了一个有血有肉的页面。

然而在我一开始学习前端的时候，觉得CSS不过如此——无非就是改一改颜色，换一换位置而已，然而，在偶然的机遇下，看到了CSS禅境花园，让我真正领略了CSS的魔力。

# 什么是CSS禅境花园
你能想想下面的几个图都来自同一个网页吗：
<p align=left>
    <img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1cce81cea6634225be257324056a4afa~tplv-k3u1fbpfcp-watermark.image?" width="350px" />
    <img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/be19bf529fdb4a6993d863be5d1debdd~tplv-k3u1fbpfcp-watermark.image?" width="350px" />
    <img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/04776bf901094be6adf8d9b41243a375~tplv-k3u1fbpfcp-watermark.image?" width="350px" />
    <img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/66593ee3879442f983c71881adb4c1f8~tplv-k3u1fbpfcp-watermark.image?" width="350px" />
</p>

当然，准确地来说，是它们共同使用了同一个HTML文件，拥有着相同的DOM结构，但是通过CSS，他们呈现了截然不同的样貌，有的清新婉约、有的雍容华贵、有的淡雅秀丽、有的热情奔放，这就是CSS的魅力，这就是禅境花园。

CSS禅境花园在2003年5月推出（那个时候CSS3还刚开始制定没几年），来自世界各地的平面设计师提供的样式用于更改同一个 HTML 文件的视觉呈现，从而产生数百种不同的设计。除了对外部 CSS 文件的引用之外，HTML文件本身永远不会改变。所有视觉差异都是CSS的成果。这个网站曾经被评为“Web标准化中最著名最鼓舞人心的项目之一”，“全世界数以万计的设计师因此学会并爱上了CSS”。

时至今日，主站虽仍然存在，但作品列表（最终网站上收录了222个设计）的页面已经无法打开，但仍然可以通过修改主站地址后面的数字来欣赏每一个设计方案：<br>
http://www.csszengarden.com/221/ (替换其中的221，注意100以内需要填0补位，比如第八个是008，第六十六个是066）<br>
或者访问主站的中文页面：<br>
http://www.csszengarden.com/tr/zh-cn/221/ (也是可以替换其中的221）<br>
无论如何，也许你打开这个页面的时候，也会同20年前的设计师一样，收获一份对于CSS魔力的惊奇与感动：
<p align=center>
    <img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d148a02ccad84c0880cc75e4d609f930~tplv-k3u1fbpfcp-watermark.image?" width="800px" />
</p>

# 代码分析&做一个自己的禅境花园
从任意一个禅境花园的页面中，你都可以下载到它的HTML文件和示例文件。

HTML文件的主要结构:
```HTML
<body>
    <section class="intro" id="zen-intro">
        ……
    </section>
    <div class="main supporting" id="zen-supporting" role="main">
        ……
    </div>
    <aside class="sidebar" role="complementary">
    </aside>
    <div class="extra1" role="presentation"></div>
    <div class="extra2" role="presentation"></div>
    <div class="extra3" role="presentation"></div>
    <div class="extra4" role="presentation"></div>
    <div class="extra5" role="presentation"></div>
    <div class="extra6" role="presentation"></div>
</body>
```
总共四部分，前面的zen-intro部分是最开始的禅境花园介绍：
<p align=center>
    <img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/cfa97407d43f43679c2e0290ede3c8f2~tplv-k3u1fbpfcp-watermark.image?" width="800px" />
</p>

第二个部分zen-supporting是中间文章的主体部分，是一些关于禅境花园的解读：
<p align=center>
    <img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7b78baafbfe240408fc6fefe9ed00da1~tplv-k3u1fbpfcp-watermark.image?" width="800px" />
</p>

第三个部分sidebar则是展示了一些设计以及导航栏：

<p align=center>
    <img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8bc2b4dbc617466eb7bdd4478d69e944~tplv-k3u1fbpfcp-watermark.image?" width="800px" />
</p>

以及最后一个部分预留了一些空白的DOM元素让你可以随心所欲自己放点东西。（不过官方文档实际上鼓励多使用伪类而并非这些额外的DOM）

接下来试着修改修改CSS样式自己做一个禅境花园吧（虽然我不是设计师）：

首先，加个页面背景：
```css
body {
	margin: 0;
	padding: 0;
	background: url(https://img.tukuppt.com//ad_preview/00/11/91/5c9951f8de1f1.jpg!/fw/980);
	background-size: cover;
}
```

将案例导航栏通过绝对定位独立出来：
```css
 .sidebar {
	top: 170px;
	margin-left: 588px;
	position: absolute;
	text-align: right;
	font-family: "lucida grande", verdana, tahoma, arial;
	width: 198px;
	padding: 0 12px;
	font-size: x-small;
	width: 174px;
}
```
给各个三级标题加上图标：
```css
  .preamble h3, 
  .explanation h3, 
  .participation h3, 
  .benefits h3, 
  .requirements h3 {
	margin: 8px 0 3px 0;
	padding: 3px 0 0 0;
	font-size: 17px;
	font-weight: 500;
	background: url(piuma.gif) no-repeat top left;
	text-indent: 33px;
}
```
最后再利用预留的DOM元素来做个小彩蛋：
```css
.extra1 {
	position: fixed;
	left: 20px;
	top: 150px;
	color: black;
	width: 120px;
	height: 120px;
}

.extra1:hover {
	color: white;
	background: url(https://lenadesign.org/wp-content/uploads/2019/12/untitled7-1.gif?w=580);
	background-size: cover;
}

.extra1::after {
	content: "Factastic CSS!";
	position: absolute;
	top: -20px;
}
```
让鼠标悬浮在文字上时出现一个CSS的动图：
<p align=center>
    <img width="150px" src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1a427245772445308d0d6943791f468b~tplv-k3u1fbpfcp-watermark.image?"/>
</p>

大体上就是这样啦（缺少设计感，这玩意还是需要个设计师啊）：

<p align=center>
    <img width="500px" src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d99d040494cb40af8ca694de426f5428~tplv-k3u1fbpfcp-watermark.image?"/>
</p>