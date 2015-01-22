title: HTML5学习总结
tags:
---
## Element(元素)
* html5的空标签，如`<br>`,`<hr>`, 建议都带结束符，如：`<br/>`,`<hr/>`
* html5的标签是大小写不敏感的，不过建议都小写

## Attributes(属性)
* `alt`
  - 指定`alt`属性，可以在元素不能正常显示的时候，显示一段执行的文本
  - 如：`<img src="hello.jpg" alt="This is the description of img">`
* 建议所有的属性名称都__小写__
* 建议所有的属性值都用__引号__括起来,通常都用`双引号`，特殊情况下用`单引号`
  - `<p title='John "ShotGun" Nelson'>`
  - `<p title="John 'ShotGun' Nelson">`

## Meta Elements(源元素)
* meta element 也叫做meta data, 即：元数据，用来描述数据的数据
* 主要有：`<title>`,`<meta>`,`<style>`,`<link>`,,`<script>`

## paragraphs(段落)
* `<p>` - 用来显示一个段文字，不过格式不好控制
* `<pre` - 用来显示已经格式化好的文本，此元素间的内容会把内容的格式如实显示

## Formatting Elements(格式化元素)
* `<strong>` - 加重(字体会加粗)
* `<em>` - 强调(字体会倾斜)
* `<small>` - 字体变小(在一段正常的字体中加一些小字体的文本)
* `<mark>` - 标记或高亮文本(默认会给文本添加黄色背景)
* `<del>` - 标记文本为删除(在文本中线上会添加一条线)
* `<ins>` - 插入文本(在文本下面会有一条下划线)
* `<sub>` - 下标文字
* `<sup>` - 上标文字

## Quotation and Citation Elements(表引用或举证的元素)
* `<q>` - 行内引用，文本会被双引号括起来

* `<blockquote>` - 块级引用
  - cite属性可以用于搜索引擎来搜索相关信息
        <blockquote cite="http://www.worldwildlife.org/who/index.html">
          For 50 years, WWF has been protecting the future of nature.
        </blockquote>


* `<cite>` - 定义一个work的标题，比如一本书、一首歌、一幅画、一个雕塑、一部电视剧
      <p><cite>The Scream</cite> by Edward Munch. Painted in 1893.</p>

* `<abbr>` - 缩写(全称可以写在title属性中)，字体样式没有变化
      <p>The <abbr title="World Health Organization">WHO</abbr> was founded in 1948.</p>

* `<dfn>` - 定义一个术语或缩写，跟`<abbr>`类似，但字体会倾斜
      <p>The <dfn title="World Health Organization">WHO</dfn> was founded in 1948.</p>
* `<address>` - 定义一个文档或文章的联系方式或信息，字体会倾斜

* `<bdo>` - 重写文本的显示方向位置
  - `<bdo dir="rtl">This text will be written from right to left</bdo>`
  - 通过控制dir属性来决定是从左到右显示，还是从右到左显示
  - `<bdo dir="ltr|rtl">`

## Computer Code Elements(代码元素)
* `<code>` - 用来显示一段代码，为了保持代码的显示格式，内容可以用`<pre>`包起来

## Links(超链接)
* 超链接(a)的四种状态的顺序从高到低如下：
  - a:link - 正常的，没被访问过
  - a:visited - 已访问过
  - a:hover - 鼠标移动之上
  - a:active - 点击的瞬间动作

## Table(表格)
* 却掉table双边框效果
      table {
        border-collapse: collapse;
      }

## HTML Layouts(布局)
* html5中跟布局相关的几个元素：
  - `header` - 定义一个document或一个section的头部区域
  - `nav` - 定义一个导航的容器
  - `section` - 在document中定义一个模块
  - `article` - 定义一个独立的文章区域块
  - `aside` - 定义除了具体内容一个外的其他内容(如：侧边栏)
  - `footer` - 定义一个document或一个section的底部区域
  - `details` - 定义额外的细节
  - `summary` - 为details元素定义一个标题
  ![](/imgs/html5_layout.png)















学到：http://www.w3schools.com/htmL/html_computercode_elements.asp


## 在显示的时候，前后会自动增加空白(margin)的元素
  - `<hn>`
  - `<p>`



