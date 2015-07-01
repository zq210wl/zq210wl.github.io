title: Angular issue 之 ng-click事件被执行两次
date: 2014-04-01 16:51:06
categories: Angular
---
> 用 angular 做公司的一个内部系统时，自己写了一个公用的 Dialog directive, 但是遇到一个问题：注册到一个button上的ng-click事件上的方法莫名其妙的总是点击一次执行两次，都快把我郁闷死了，不过问题到最后总是能找到原因并且解决的。下面我就说下为什么会出现这种问题。

* 问题所在
  - 问题出现在我使用了$compile去编译了一些后加入到template中的element。但是我为了偷懒把真个template都compile了一次，这时候template中的一些元素等于被compile了两次，只要是被compile了两次的元素，在其上面注册事件都会被执行两次。

* 如何解决
  - 方法一：只compile后加入模板的元素(也就是没有编译过的元素)
  - 方法二：在preLink中完成对新元素的加入，因为这时候文章template都还么执行compile, 相加什么就加什么，加完之后，angular会自动把真个template compile 一次。

* 总结
  - $compile虽强大，但还需谨慎。



