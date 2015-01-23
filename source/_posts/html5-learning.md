title: HTML5学习总结
date: 2015-01-23 16:44:25
categories: HTML
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
* 去掉table双边框效果
      table {
        border-collapse: collapse;
      }

## Layouts(布局)
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

## Color value
* 颜色值有三种写法：
  - 1)直接写颜色单词;2)"#"加一个十六进制的数字;3)rgb颜色。最终都为被转化为十六进制来显示

## Responsive(响应式)
* `viewport` - 响应式的meta标签的参数
* 参数的属性值：

|     属性    |   描述  |
|    :-----   | :------ |
| width | 虚拟视窗的宽度 |
| device-width | 设备屏幕的宽度 |
| height | 虚拟视窗的高度 |
| device-height | 设备屏幕的高度 |
| initial-scale | 页面初始化的缩放倍数。1.0为不缩放 |
| minimum-scale | 可以缩放的最小倍数 |
| maximum-scale | 可以缩放的最大倍数 |
| user-scalable | 是否允许缩放,值为Boolean |
```
<meta name="viewport" content="width=device-width, initial-scale=1">
```

## Charset Encoding(字符集编码)
```
<meta charset="UTF-8">
```

## Form Elements(表单元素)
* html5新增加的元素：
  - `<datalist>` - 指定一个有默认选项值的input
        <datalist id="browsers">
          <option value="Internet Explorer">
          <option value="Firefox">
          <option value="Chrome">
          <option value="Opera">
          <option value="Safari">
        </datalist>
  ![](/imgs/html5-datalist.png)

* html 新增加的input type:
  - color
  - date
  - datetime
  - datetime-local
  - email
  - month
  - number
  - range
  - search
  - tel
  - time
  - url
  - week

* Input Attributes(input常用属性)
  - readonly - 只读
  - disabled - 不能用
  - maxlength - 最大长度
  - autofocus
  - min - 最小值
  - max - 最大值
  - multiple - 多选，针对file和image类型
  - pattern - 正则验证，如：pattern="[A-Za-z]{3}"
  - placeholder - 默认值
  - required - 必须填写
  - step - 数字间隔，针对number类型

## New HTML5 Elements(html5 新增的几个常用元素)
* 语义化
  - `<header>`
  - `<footer>`
  - `<article>`
  - `<section>`
* 图像处理
  - `<svg>`
  - `<canvas>`
* 多媒体
  - `<audio>`
  - `<video>`
```
<video width="320" height="240" controls>
  <source src="forrest_gump.mp4" type="video/mp4">
  <source src="forrest_gump.ogg" type="video/ogg">
  <track src="subtitles_en.vtt" kind="subtitles" srclang="en" label="English">
  <track src="subtitles_no.vtt" kind="subtitles" srclang="no" label="Norwegian">
</video>
```
## SVG 和 Canvas 最大的不同
* SVG是基于XML的，每一个元素都是一个DOM元素，可以添加事件
* Canvas是通过javascript一像素一像素的画出来的

## HTML plug-ins(插件)

```
<object width="400" height="50" data="bookmark.swf"></object>
```

```
<embed width="400" height="50" src="bookmark.swf">
```

## HTML5 APIs
* Geolocation - 定位
* Drag/Drop - 拖拽
* Local Storage - 本地存储
* Web Workers - 可以在后台运行脚本而不影响页面的性能

## 详细使用请参考：
http://www.w3schools.com/html/


