title: CSS3学习总结
tags:
---
## CSS的层叠优先级顺序(以下为从低到高优先级)
* 1)浏览器默认样式
* 2)外部CSS文件样式
* 3)内部样式(在head里面的)
* 4)行内样式
> 注意：
> 如果引入的外部css文件放在了内部样式之后，则外部样式就会覆盖内部样式！

## Links(超链接)
* 超链接(a)的四种状态的顺序从高到低如下：
  - a:link - 正常的，没被访问过
  - a:visited - 已访问过
  - a:hover - 鼠标移动之上
  - a:active - 点击的瞬间动作

## List(ul,ol)(列表)
* 隐藏ul列表前面符号
```
ul { list-style-type: none; }
```

## CSS Box Model(盒子模型)
![](/imgs/css_box_model.png)
  * `width`属性值得只是内容的宽度，不包括padding、border
  * 元素的总width = width + paddnig + border + margin

## Border(边框)
* 要设置border-width和border-color，必须先设置border-style

## Positioning(定位)
* fixed - 针对浏览器窗口的位置
* relative - 针对元素本身的位置
* absolute - 针对父元素设置了relative或absolute

## Combinators(关系选择器)
* 选定__所有子孙__
      div p { }
* 选定__直接子孙__
      div > p { }
* 选定元素`后面`__所有同辈元素__
      div ~ p { }
* 选定元素`后面`__紧邻的第一个同辈元素__
      div + p { }

## Pseudo(伪)
* pseudo-class(伪类)
  - :link
* pseudo-element(伪元素)
  - ::after

## Opacity(不透明度)
* 取值范围为：0-1.0, 1.0为不透明
```
img {
  opacity: 0.4;
  filter: alpha(opacity=40); /* For IE8 and earlier */
}
```

## CSS sprites
* `background:url(test.png) no-repeat 0 0;`
* 主要应用`background-position`属性
  - <percentage>： 用百分比指定背景图像填充的位置。可以为负值。
  - <length>： 用长度值指定背景图像填充的位置。可以为负值。
  - center： 背景图像横向和纵向居中。
  - left： 背景图像在横向上填充从左边开始。
  - right： 背景图像在横向上填充从右边开始。
  - top： 背景图像在纵向上填充从顶部开始。
  - bottom： 背景图像在纵向上填充从底部开始。

## Media queries

## Gradients

## Text Shadow

## @font-face (使用自定义字体)

```
@font-face {
  font-family: __myFirstFont__;
  src: url(sansation_light.woff); // 指定字体文件的位置
  font-weight: bold;
}
```
## 2D Transforms
* 2D transform 有以下常用方法：
  - translate(x,y) - 将元素沿着X轴和Y轴移动
  - scale(x,y) - 将元素的宽和高分别增加响应的倍数
  - rotate(angle) - 将元素沿着__垂直于元素水平面__的__中心轴__顺时针旋转响应角度，可以为负数
  - skew(x-angle,y-angle) - 斜交;将元素分别沿着X轴和Y收轴转动响应的度数
* 使用方法：
  - transform: method();
* 示例：

```
div {
    -ms-transform: translate(50px,100px); /* IE 9 */
    -webkit-transform: translate(50px,100px); /* Chrome, Safari, Opera */
    transform: translate(50px,100px);
}
```
## 3D Transforms
* 3D transform 的方法：
  - rotateX(angle)  --沿着X轴旋转
  - rotateY(angle)  - 沿着Y轴旋转

## CSS3 Transitions
* 什么是transition？
  - 让元素在一定时间内从一种样式渐渐地变化为另一种样式，从而形成一种渐变的动画效果
* 示例：(当div的width,height以及transform属性发生变化时，让其指定的相应属性在两秒内渐渐变化)

```
div {
  -webkit-transition: width 2s, height 2s,-webkit-transform 2s;  /* For Safari 3.1 to 6.0 */
  transition: width 2s, height 2s, transform 2s;
}
```
* 详细参数使用：
```
div {
  transition-property: width;
  transition-duration: 1s;
  transition-timing-function: linear;
  transition-delay: 2s;
}
```

## CSS3 Animations
1. 用 @keyframes 来定义动画

```
@keyframes myfirst {
  from {background: red;}
  to {background: yellow;}
}
```

2. 用animation属性将定义好的动画应用到元素上

```
div {
    -webkit-animation: myfirst 5s; /* Chrome, Safari, Opera */
    animation: myfirst 5s; // 需要指定动画名称和渐变的时间
}
```
* 用百分比指定更详细的动画,指定多个关键帧：

```
@keyframes myfirst {
    0%   {background: red;}
    25%  {background: yellow;}
    50%  {background: blue;}
    100% {background: green;}
}
```
* 更多animation参数的使用：
div {
  animation-name: myfirst;
  animation-duration: 5s;
  animation-timing-function: linear;
  animation-delay: 2s;
  animation-iteration-count: infinite;
  animation-direction: alternate;
  animation-play-state: running;
}

## box-sizing --__很有用__
* 指定对元素的width和height大小的设置是否包括边框在内

```
box-sizing: border-box;
```

