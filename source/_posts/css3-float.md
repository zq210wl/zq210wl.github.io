title: float元素对兄弟元素的影响
date: 2015-01-30 10:54:38
categories: CSS
---
> 提示：下面所说的前、后，指的是元素在 html 节点中的书写顺序。

## 对块级元素的影响
1. 块级元素在float元素的前面和后面的显示效果是<b style="color:red;">不一样</b>的;
2. 块级元素在前，则float元素就会在块级元素之后<b style="color:red;">另起一行</b>来显示;
3. 块级元素在后，则块级元素会<b style="color:red;">占据float元素所在行</b>，且<b style="color:red;">被float元素覆盖</b>;
   但是块级元素内的inline元素遇到float元素则会<b style="color:red;">环绕</b>其显示;
4. 注意：上面的显示规则跟块级元素是否设置宽度无关;

## 二、对inline元素的影响
1. inline元素不多说，inline元素会环绕float元素显示;
2. 直接看[demo](/demo/floatFeaturesSummary.html)了解细节

## 三、float元素对float元素的影响
1. 父容器的宽度足够容纳所有子元素，则<b style="color:red;">在一行</b>显示
2. 父容器的宽度不够容纳所有子元素，则<b style="color:red;">后面</b>元素会另起一行显示

__请看：[demo](/demo/floatFeaturesSummary.html)__