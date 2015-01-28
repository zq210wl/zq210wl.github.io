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














## CSS Box Model
* `width`属性值得只是内容的宽度，不包括padding、border
* 元素的总width = width + paddnig + border + margin