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

