title: CSS相关的一些基本常识
tags:
---
> 本文所介绍的CSS属性都是就现代浏览器而言的，不包括"古董"浏览器。
* width属性
  - width所包含的区域为`border`、`padding`、`content`三者。

* font-size属性
  - 如果不指定值，则默认大小为16px(16px=1em)
  - em 和 % 都是针对父级元素的font-size而言的，如果没有则为默认的16px

* float和position属性
  - 只有在元素没有设置position或position值为relative时float才有效
  - 当元素设置了position:absoute|fixed之后，就设置float是不起作用的

* position属性
  - 设置了position:absolute的元素，其__参照对象__为__最近__的设置了position为__非static的父级元素__
  - left:n%或者right:n%是针对其__container元素__(必须是block或float元素)的宽度来说的

* img元素
  - img元素是inline元素，可以直接设置宽高，其默认宽高为图片本身的宽高

## 透明度
* opacity为__不__透明度, 取值范围为：0-1.0, __1.0为不透明__