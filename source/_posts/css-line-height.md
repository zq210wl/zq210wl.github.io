title: 理解line-height
date: 2015-01-28 14:10:02
categories: CSS3
---
## 基本概念
* 基线、中线、顶线、底线
![](/imgs/css_line_height.png)
* 基线
  - 基线并不是汉字的下端沿，而是英文字母"x"的下端沿

* 行高
  - 文本间基线的距离

* 行距
  - 上行文本的底线到下行文本顶线之间的具体

* 内容区
![](/imgs/css_line_height_content.gif)

* 行内框
![](/imgs/css_line_height_inner.gif)
  * 行内框只是一个概念，它无法显示出来，但是它又确实存在
  * 它的高度就是行高
  * 在没有其他因素（padding）影响的时候，行内框等于内容区域

* 行框(line box)
![](/imgs/css_line_box.gif)
* 同行内框类似，行框是指本行的一个虚拟的矩形框
* 行框高度等于本行内所有元素中行高最大的值

## line-height的设置
* 行高继承
  - 默认情况下，如果父元素设置了line-height，而子元素没有设置，那么子元素将会将会继承父元素的line-height

* 行高的计算
  * 行高常用的单位：
    * px - 固定值
    * em - 一个em的大小等于当前行中font-size的大小
    * number - 一个纯数字，数字大小表示的是font-size的倍数
    * normal - 正常，默认值，默认一般为1.2
    * inherit - 继承
  * 一般情况下如果行内有多种大小字体，可以用一个纯数字设置行高，这样可以避免行高小于字体大小而导致文字重叠

