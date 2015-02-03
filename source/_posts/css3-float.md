title: float属性详解
date: 2015-01-30 10:54:38
categories: CSS
---

## float:left 元素
  - 对__前面__元素的影响
    * 当前面为`Block`元素时,__会在Block元素之后另起一行显示__
    * 当前面为`inline`元素时
      - 当inline元素所在行__足够宽__(即:能容纳下这两者宽度之和),__会显示在inline元素之前__
      - 当inline元素所在行__不够宽__(即:不能容纳下这两者宽度之和),__会在inline元素之后另起一行显示__
  - 对__后面__元素的影响
    * 当后面为`Block`元素时
      - 当Block元素设置了宽度,__Block元素会占据float元素留出的空间，里面的内容会显示在float元素下面__
      - 当Block元素没有设置宽度,__Block元素会占据float元素留出的空间，里面的内容会围绕着foat元素显示__
    * 当后面为`inline`元素时,......
      - 当float元素所在行__足够宽__(即:能容纳下这两者宽度之和),__会显示在inline元素之前__
      - 当float元素所在行__不够宽__(即:不能容纳下这两者宽度之和),__inline元素会在float元素之后另起一行显示__

## float:right 元素
  - 对__前面__元素的影响
    * 当前面为`Block`元素时,__会在Block元素之后另起一行显示__
    * 当前面为`inline`元素时
      - 当inline元素所在行__足够宽__(即:能容纳下这两者宽度之和),__会显示在inline元素的右边__
      - 当inline元素所在行__不够宽__(即:不能容纳下这两者宽度之和),__会在inline元素之后另起一行显示__
  - 对__后面__元素的影响
    - 元素会占据float元素留出的空间，里面的__内容__会在float元素左边和下边围绕显示__
      - 当元素所在行__足够宽__(即:能容纳下__元素内容__`和float元素两者宽度之和),__会显示在元素的右边__
      - 当元素所在行__不够宽__(即:不能容纳下__元素内容__和float元素两者宽度之和),__元素内容会围绕在float元素的左边和下边显示__

> 总的来说：float元素会脱离文档流，其后的元素会占据它留下的空间。

## 子元素 float
* 当父元素设置了float,__父元素会包含子元素__
* 当父元素__没__设置了float
  - 当父元素触发了haslayout(比如：设置了width和height),__父元素会包含子元素__
  - 当父元素__没__触发了haslayout,__子元素会超出父元素包含，父元素不会被撑开__

## 如何清除浮动
> 清除浮动的办法很多,不过原理都是一样:只要触发父元素的haslayout就OK啦。

* 下面介绍几种清除浮动的方法：
  - 在父元素末尾添加一个空格`&nbsp`;(扯淡)
  - 给父元素设置宽和高(按需使用)
  - 让父元素也浮动(慎用)
  - 设置overflow:hidden|auto;(有副作用，慎用)
  - 使用:after伪类和内容声明在指定的现有内容的末尾添加新的内容(强烈推荐)
        .clear:after {
        　content:".";
        　height:0;
        　visibility:hidden;
        　display:block;
        　clear:both;
        }

## clear属性
* clear属性有三个值：left|right|both
* 指定某个元素的左边或右边`不能有浮动元素`(即换行显示了)