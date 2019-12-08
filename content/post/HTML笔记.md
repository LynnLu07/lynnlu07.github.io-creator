---
title: "HTML笔记"
date: 2019-09-22T01:31:03+08:00
draft: false
---

1. HTML是谁发明的？
Tim Berners-Lee 李爵士

2. HTML 起手应该写什么？
文档类型hmtl，lang设置语言，head标签，body标签，字符编码UTF-8，content="width=device-width, initial-scale=1.0"禁用缩放，content="ie=edge"将引擎设为最新版，title标题。


![](https://user-gold-cdn.xitu.io/2019/9/22/16d59040ca54961d?w=1125&h=688&f=png&s=48948)

3. 常用的表章节的标签有哪些，分别是什么意思？
* h1~h6 不同大小的标题，依次递减。
* section 章节
* article 文章
* p 段落
* main 主要内容
* aside 旁支内容
* header 头部
* footer 脚部
* div 区块

4. 全局属性有哪些？
全局属性是所有标签都具有的属性。
* class 规定元素的类名
* contenteditable 规定是否可编辑元素的内容
* hidden 规定对元素进行隐藏
* id 规定元素的唯一id
* style 规定元素的行内样式（inline style）
* tabindex 设置元素的tab键控制次序
* title 规定元素的额外信息（可在工具提示中显示）
5. 常用的内容标签有哪些，分别是什么意思?
* ol+li (ordered list+list item) 有序列表
* ul+li (unordered list+list item)无序列表
* di+dt+dd (description list+term+data)
dl表示一组术语的列。dt定义术语名，dd定义术语解释。
* pre (preformatted)浏览器保留该标签内部原始的换行和空格，默认以等宽字体显示标签内容。
* hr 水平线，它没有闭合标签。
* br (break) 换行，没有闭合标签。
* a (anchor) 链接
* em (emphasis) 强调，浏览器会斜体显示。
* strong 标签包含的内容具有很强的重要性，浏览器会粗体显示。
* code 表示标签内容是计算机代码，浏览器会以等宽字体显示。如果需要表示多行代码，code标签必须放在pre标签内部，code本身仅表示一行代码。
* q (quote) 引用，有cite属性，浏览器斜体显示，添加半角的双引号，用于少量文字引用。
* blockquote 引用，有cite属性，浏览器斜体显，用于大量文字引用示。


