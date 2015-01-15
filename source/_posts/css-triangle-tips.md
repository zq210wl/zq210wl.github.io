title: 纯CSS代码实现小三角效果
date: 2015-01-15 11:09:05
categories: CSS
---
* 实现方法：
  ```
  <div class="triangle"></div>
  ```
  ```
  .triangle-all{
    width: 0;
    height: 0;
    border-width: 30px;
    border-style: solid;
    border-color: #c03 #fc0 #69c #6c6;/* 红 黄 蓝 绿 */
  }
  ```
* 效 果 图
  ![](/imgs/css_triangle.png)
* 实现原理
  - 利用元素的四个border会彼此叠加的性质来制作三角形，只要让其他三条边隐藏起来就可达到效果。

## 通过上面的原理，我们来制作一个指向下的三角形：
* 实现方法：
  ```
  <div class="triangle-all"></div>
  ```
  ```
  .triangle_down{
    width:0;
    height:0;
    border-width:30px 30px 0;
    border-style:solid;
    border-color:#c03 transparent transparent ;/* 红 透明 透明 */
  }
  ```
* 效 果 图
  ![](/imgs/css_triangle_down.png)
* 原理分析
  - border-color:#c03 transparent transparent ;是将需要隐藏的边的颜色设置成透明；
  - border-width:30px 30px 0; 是将三角形对边的宽度设置为0(这里对边是border-bottom)这么做的原因是减小三角形有效作用区域。

## 通过上面的原理，我们来制作类似下面的tip效果：
![](/imgs/css_triangle_tip.png)
* 实现方法
  ```
  <div class="triangle-tip-up"></div>
  ```
  ```
  .triangle-tip-up{
    width: 200px;
    height: 30px;
    background:#3FB58E;
    border-radius: 4px;
    position: relative;
  }
  .triangle-tip-up:before{
    content:'';
    width: 0;
    height: 0;
    border-width: 0 10px 10px;
    border-style: solid;
    border-color: transparent transparent #3FB58E;
    position: absolute;
    left: 80px;
    top: -10px;
  }
  ```
* 实现原理
  - 利用一个div来做tip的主体框，设置其position为relative(为了控制三角形的位置)
  - 利用css的:before属性来做三角形的主体元素，设置其position为absolute(这样可以通过设置left和top的值来随意控制小三角的位置)

## 实现类似下面的不规则三角形
![](/imgs/css_triangle_scalene.png)
* 实现方法
  ```
  <div class="triangle-scalene"></div>
  ```
  ```
  .triangle-scalene{
    width: 0;
    height: 0;
    border-width: 0 0 60px 20px;/* 设置对角和相邻的border都为0来实现不规则效果 */
    border-style: solid;
    border-color: transparent transparent #69c;
  }
  ```
* 实现原理
  - 设置对角和相邻一边的border都为0,然后通过改变其余两边border的宽度来实现不规则效果

## 在线效果预览
<p data-height="750" data-theme-id="0" data-slug-hash="ogZpqP" data-default-tab="result" data-user="zq210wl" class='codepen'>See the Pen <a href='http://codepen.io/zq210wl/pen/ogZpqP/'>ogZpqP</a> by zhangqi (<a href='http://codepen.io/zq210wl'>@zq210wl</a>) on <a href='http://codepen.io'>CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>