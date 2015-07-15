title: 细说清除浮动
date: 2014-06-25 15:21:41
categories: CSS
---
## 一、什么是清除浮动？
  * __浮动的缺陷__

    - 在了解如何清除浮动之前，先介绍为什么需要清除浮动。如本文开头所说的，浮动虽然可以便于页面布局，但同时会产生一些问题，也就是我们常说的“副作用”。而一个元素设置了浮动（即 float 值为 left, right 或 inherit 并从父元素上继承 left 或 right 值）的常见缺陷是——影响它的兄弟元素的位置和父元素产生高度塌陷，下面对这两个问题展开说明。

    - 一个元素设置了浮动后，会影响它的兄弟元素，具体的影响方式较为复杂，这要视乎这些兄弟元素是块级元素还是内联元素，若是块级元素会无视这个浮动的块框，也就是我们平时看到的效果——使到自身尽可能与这个浮动元素处于同一行，导致被浮动元素覆盖，除非这些 div 设置了宽度，并且父元素的宽度不足以包含它们，这样兄弟元素才会被强制换行；若是内联元素，则会尽可能围绕浮动元素。

    - 另外，浮动的元素脱离了普通流，这样使得包含它的父元素并不会因为这个浮动元素的存在而自动撑高，这样就会造成高度塌陷。

    - 下面是演示效果图:
      ![](/imgs/css_clearfloat_1.png)

    - 关于这几点的更多说明，请看 [Demo](/demo/clearfix.html) 。

    - 很显然，无论是影响兄弟元素还是高度塌陷的问题，都不是我们使用浮动的目的，设置浮动，只是为了改变一个元素的布局，但最终的结果却造成了更多不必要的影响，这不利于布局，因此我们需要清除这些额外的影响，也就是本文要介绍的清除浮动，其实更加准确的说，是清除浮动带来的额外影响。

  * __清除浮动的常见方法__

    - 了解了为什么要清除浮动后，这里可以开始介绍清除浮动的常见方法了，不过这里并不急于探讨这些方法的原理，首先列出几种常见清除浮动的方法，再作探讨。

    - 说起清除浮动，大家肯定会想起 clear: both ，的确，这是 CSS 中清除浮动的属性，clear 有 both/left/right/none/inherit 几个属性值，分别代表在元素左右两侧不允许出现浮动元素/左侧不允许出现浮动元素/右侧不允许出现浮动元素/不清除浮动/继承父元素的值。

    - 如下图为清除浮动的例子：
      ![](/imgs/css_clearfloat_2.png)

    - 也可以看 [Demo](/demo/clearfix.html) 。

    - 从例子中可以看出，设置了 clear: both （当然在该例子中也可以为 clear: left）的元素不会跟浮动元素同行，并且会占据新的一整行，而不是根据内容来自动调整宽度。之所以会这样，要从 clear 的原理说起，clear 会为元素添加足够的空白空间，使到该元素的位置会放置在它前一个浮动元素之下，这跟增加元素外边距使到元素占据满行而强制换行的效果是一样的，事实上在 CSS1 和 CSS2 中，清除浮动正是通过自动为清除元素（即设置了 clear 属性的元素）增加外边距实现的，从 CSS 2.1 开始改为增加额外的空白空间，不改变外边距。现在大家应该清楚了，既然是增加足够的空间使到元素换行，那么最稳妥的办法就是使到该元素占据一整行，也就是 Demo 中的效果。
    - 现在清除了浮动，但是，这只是清除了浮动对于兄弟元素的影响，而高度塌陷的问题还没有解决，因此，我们需要更高级的清除浮动——闭合浮动。

    - 为什么叫闭合浮动？因为浮动的元素脱离了普通流，因此对于它的父元素，它并没有闭合，这时候就需要闭合浮动了。这个问题的解决方法经过多年的发展，已经有了比较完善的方法，下面为大家详细介绍三种常用方法。

    - __(1)空 div 方法__

      - 这是较为古老的方法了，除了 div ，也有使用其他标签的，但 div 更为适用，因为除了浏览器赋予它的 display: block 外，它没有其他的样式了，也不会有特殊的功能，干干净净。这里插一段题外话，display: block 是浏览器赋予 div 的，存在于浏览器的 user agent stylesheet ，而不是 div 默认 display 的值就为 block ，在 W3C 中，所有的 HTML 标签 display 的默认值都为 inline 。

      - 下面代码中使用到的 box main left aside 为预先设置了相关 CSS 的类，具体可以查看 Demo 的源码，在其他例子中也是如此。
            <div class="box">
              <div class="main left">我设置了左浮动 float: left</div>
              <div style="clear: both;"></div>
              <div class="aside">我是页脚，我的上面添加了一个设置了 clear: both 的空 div</div>
            </div>

      - 效果如图：
        ![](/imgs/css_clearfloat3.png)

      - 也可以看 [Demo](/demo/clearfix.html) 。
      - 空 div 方法很方便，但是加入了没有涵义的 div ，这违背了结构与表现分离的原则，并且后期维护也不方便。

    - __(2)overflow 方法__

      - 在浮动元素的父元素上设置了 overflow 的值为 hidden 或 auto ，可以闭合浮动。另外在 IE6 中还需要触发 hasLayout ，例如为父元素设置容器宽高或设置 zoom：1
            <div class="box" style="overflow: hidden; *zoom: 1;">
                <div class="main left">我设置了左浮动 float: left</div>
                <div class="aside left">我是页脚，但是我也设置了左浮动。</div>
            </div>

      - 效果如图：
        ![](/imgs/css_clearfloat_4.png)

      - 也可以看 [Demo](/demo/clearfix.html) 。

      - 这个方法相对前者更加方便，也更加符合语义要求，只是 overflow 并不是为了闭合浮动而设计的，因此当元素内包含会超出父元素边界的子元素时，可能会覆盖掉有用的子元素，或是产生了多余的滚动条。这也是在 overflow 方法诞生后依然需要寻找更佳方法的原因。

    - __(3)使用 :after 伪元素的方法__

      - 该方法来源于 [positioniseverything](http://www.positioniseverything.net/easyclearing.html) ,结合 :after 伪元素（注意这不是伪类，而是伪元素，代表一个元素之后最近的元素）和 IEhack ，可以完美兼容当前主流的各大浏览器，这里的 IEhack 指的是触发 hasLayout ，具体请看下面的方法。
            <style>
                .clearfix {/* 触发 hasLayout */ zoom: 1; }
                .clearfix:after {content: &quot;.&quot;; display: block; height: 0; clear: both; visibility: hidden; }
            </style>
            <div class="box clearfix">
                <div class="main left">我设置了左浮动 float: left</div>
                <div class="aside left">我是页脚，但是我也设置了左浮动。</div>
            </div>
      - 显然，相对来说，这个办法不但完美兼容主流浏览器，并且也很方便，使用重用的类，可以减轻代码编写，另外网页的结构也会更加清晰。

      - 效果如图：
        ![](/imgs/css_clearfloat_5.png)

## 二、清除浮动方法的实质 —— CSS clear 与 BFC 特性

* 通过上面的例子，我们不难发现清除浮动的方法可以分成两类：

  - 一是利用 clear 属性，包括在浮动元素末尾添加一个带有 clear: both 属性的空 div 来闭合元素，其实利用 :after 伪元素的方法也是在元素末尾添加一个内容为一个点并带有 clear: both 属性的元素实现的。

  - 二是触发浮动元素父元素的 BFC (Block Formatting Contexts, 块级格式化上下文)，使到该父元素可以包含浮动元素，关于这一点，下面会为大家进行详细的介绍。

* BFC 在 CSS 的可视化格式模型 (Visual Formatting Model) 中具有非常重要的地位，很多开发者因为不了解 BFC 的特性而在实际开发中产生很多让人感到莫名其妙的问题。尽管如此，因为 BFC 涉及 CSS 中很少接触的部分，因此国内的相关介绍很少，这里展开说明一下。

* 相关文章
  - [Understanding the Humble Clearfix](http://fuseinteractive.ca/blog/understanding-humble-clearfix#.VYuT6dyqqko)