title: 设置元素水平居中
date: 2015-01-30 15:33:47
categories: CSS
---

* 固定宽度的`block`元素的水平居中
  - 方法一: 设置左右margin为auto
        .center {
            margin-left: auto;
            margin-right: auto;
            width: 200px;
        }
  - 方法二：
        .center {
            position: relative;
            left: 50%;
            width: 200px;
            margin-left: -100px;
        }

> 注意：当把`img`元素设置成block元素之后，其宽度默认就是图片本身的宽度，所以也属于有固定宽度的。

* 不确定宽度的元素的居中
  - 方法一：设置父级元素text-align:center;然后自身display:inline;
  - 方法二：利用__浮动的包裹性__和相对定位__百分比数据值特性__,传说称之为“相对浮动”(推荐)
        .parent { /* 其父级元素要设置清楚浮动，不然可能会出现问题*/
          float: left;
          position: relative;
          left: 50%;
        }
        .children {
          position: relative;
          left: -50%;
        }
  - 方法三：使用table作为容器的方法来实现.(Table标签本身并不是块级元素,当我们不设置table的宽度的话,他里面的宽度是__由他内部元素的宽度撑起来的__。但即使我们没有设置table的宽度,直接设置table的外边距margin:0 auto;就可以实现水平居中了!这样我们就可以通过设置table水平居中,间接使里面的内容居中。)
        <table class="center"><tr><td>元素</td></tr></table>
        .center{margin:0 auto}
  - 方法四：利用table table-cell(利用table的可以宽度可以内容撑起来的特性)
        .container {
          display:table;
          margin:0 auto;
        }
        .children {
          display:table-cell;
        }