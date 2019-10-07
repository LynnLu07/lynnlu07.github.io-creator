---
title: "CSS知识总结"
date: 2019-10-05T10:09:45+08:00
draft: false
---

## 1. 浏览器渲染原理
根据 HTML 和 CSS 输入构建了 DOM 树和 CSSOM树。不过，它们都是独立的对象，分别网罗文档不同方面的信息：一个描述内容，另一个则是描述需要对文档应用的样式规则。我们该如何将两者合并，让浏览器在屏幕上渲染像素呢？



[JavaScript→style→layout→paint→composite](https://developers.google.com/web/fundamentals/performance/rendering/)

样式计算style。此过程是根据匹配选择器，例如 `.headline` 或 `.nav > .nav__item`计算出哪些元素应用哪些 CSS规则的过程。从中知道规则之后，将应用规则并计算每个元素的最终样式。 
    
布局layout。在知道对一个元素应用哪些规则之后，浏览器即可开始计算它要占据的空间大小及其在屏幕的位置。

绘制paint。填充像素的过程。它涉及绘出文本、颜色、图像、边框和阴影，基本上包括元素的每个可视部分。绘制一般是在多个表面（通常称为层）上完成的，使用最终渲染树将像素渲染到屏幕上。

合成composite。由于页面的各部分可能被绘制到多层，由此它们需要按正确顺序绘制到屏幕上，以便正确渲染页面。对于与另一元素重叠的元素来说，这点特别重要，因为一个错误可能使一个元素错误地出现在另一个元素的上层。


![[来源](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-tree-construction)](https://user-gold-cdn.xitu.io/2019/10/5/16d99e7ee4207ce5?w=1150&h=537&f=png&s=69908)


## 2. CSS基础概念
### 文档流 normal flow
* inline元素的宽度为内部inline元素的和，不能用width来指定；高度由line-height间接确定，与height无关。
* block元素默认自动计算宽度，可用width指定；宽度由内部文档流元素决定，可以设height。
* inline-block结合二者特点，可用width和height指定。

### 盒模型 box
CSS 盒模型分为 content-box 和 border-box。

content-box 宽度 width = content，不包含 padding 和 border

border-box 宽度 width = content + padding + border 

一般使用`border-box`
## 3.CSS布局
### float布局
子元素加上`float:left`和`width`            
父元素加上`.clearfox`
### flex布局
```
justify-content:
    flex-start: 元素和容器的左端对齐。
    flex-end: 元素和容器的右端对齐。
    center: 元素在容器里居中。
    space-between:元素之间保持相等的距离。
    space-around:元素周围保持相等的距离。
```
```
align-items:
    flex-start: 元素与容器的顶部对齐。
    flex-end: 元素与容器的底部对齐。
    center: 元素纵向居中。
    baseline: 元素在容器的基线位置显示。
    stretch: 元素被拉伸以填满整个容器。
```
```flex-direction:
    row: 元素摆放的方向和文字方向一致。
    row-reverse: 元素摆放的方向和文字方向相反。
    column: 元素从上放到下。
    column-reverse: 元素从下放到上。
```
```flex-wrap:
nowrap: 所有的元素都在一行。
wrap: 元素自动换成多行。
wrap-reverse: 元素自动换成逆序的多行
```
```flex-flow:flex-drection flex wrap方向和换行```
```
align-content:
    flex-start: 多行都集中在顶部。
    flex-end: 多行都集中在底部。
    center: 多行居中。
    space-between: 行与行之间保持相等距离。
    space-around: 每行的周围保持相等距离。
    stretch: 每一行都被拉伸以填满容器。
```
可能有些容易混淆，但align-content决定行之间的间隔，而align-items决定元素整体在容器的什么位置。只有一行的时候align-content没有任何效果。


## 4.CSS定位

position的取值

`static` 默认值，待在文档流里。

`relaive`相对定位，提升层级，不会使元素脱离文档流。用z-index样式的值可以改变一个定位元素的层级关系，从而改变元素的覆盖关系，值越大越在上面（z-index只能在position属性值为relative或absolute或fixed的元素上有效）。 （两个都为定位元素，后面的会覆盖前面的定位）
`absolute`绝对定位，通过指定元素相对于最近的非 static 定位祖先元素的偏移，来确定元素位置。绝对定位的元素可以设置外边距（margins），且不会与其他边距合并。
`fixed`固定定位，相对于浏览器窗口进行定位。


使当前元素变成一个[层叠上下文](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Understanding_z_index/The_stacking_context)
```
html元素
position:relative;z-index:0;
position:absolute;z-index:0;
opacity:不为1；
position:fixed;z-index:auto;
```

## 5.CSS动画
### transition
[MDN文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS/transition)

作用：补充中间帧
transition:属性名 时长 过渡方式 延迟

过渡方式：linear匀速、ease先快后慢、ease-in先慢后快。ease-out先快后慢。ease-in-out快-慢-快。
`transition:all 3s liner 1s`

[示例](http://js.jirengu.com/wugonugifo/1/edit?html,css,output )


并不是所有属性都能过渡。display:none=>block没法过渡，一般改为visibility:hidden=>visible。
`visibility: hidden` 与 `display: none` 是不一样的。前者隐藏元素，但元素仍占据着布局空间（即将其渲染成一个空框），而后者 (display: none) 将元素从渲染树中完全移除，元素既不可见，也不是布局的组成部分。

过渡必须有起始。如果需要有中间点，可以选择使用两次transform或者animation。

![](https://user-gold-cdn.xitu.io/2019/10/5/16d9a60c8352c893?w=1592&h=604&f=png&s=304798)
注意要延续上一点的属性。

### animation
[animation的MDN文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS/animation)

animation:时长 过渡方式 延迟 次数 方向 填充模式 是否暂停 动画名
方向: reverse alternate alternate-reverse
填充模式: none forwards backwards both
是否暂停: paused running

[keyframes的MDN文档](https://developer.mozilla.org/en-US/docs/Web/CSS/@keyframes)

keyfames可以写from to，也可以写百分数，百分数使用较多。
![](https://user-gold-cdn.xitu.io/2019/10/5/16d9a655f4f03786?w=1453&h=564&f=png&s=236593)

[示例]( http://js.jirengu.com/tarasiraxu/1/edit?html,css,output)