title: 当移动滚动条时固定table的第一行和第一列，类似excel的滚动效果，jquery实现
date: 2015-01-05 13:40:55
categories: Javascript
---

> 项目中遇到个需求，就是要把table的第一行和第一列固定，这样当出现滚动条的时候就方便在滚动数据的时候可以对照title来看，而且为了美观还必须要跟excel的滚动效果一样，也就是滚动条不能只出现在table内容区域，还必须包括title区域，这样的话就不能简单的只在内容区域的div上设置overflow:auto，刚开始本想在网上搜一些现成的代码，但是很不幸没有搜到有这样的需求，大部分都是只有固定头一行或头一列，这样还好实现，但是要两个都实现就有以下复杂了。最后我还是自己来实现了。


看效果图：

__页面刚初始化的table样式：__

![](/imgs/javascript_excel_table_init.jpg)

__拖动滚动条后的table样式：__

![](/imgs/javascript_excel_table_move.jpg)

__[在线看效果](http://plnkr.co/edit/MUxu6a87lzR2Xptishjq?p=preview)__

__[访问github上的源码](https://github.com/zq210wl/Fixed-the-first-line-and-first-column-of-table)__

