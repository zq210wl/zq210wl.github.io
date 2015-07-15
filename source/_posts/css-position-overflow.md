title: position属性对overflow的影响, 深入理解position和overflow的关系
date: 2014-04-14 18:29:23
categories: CSS
---
> 项目中遇到了一个问题，就是明明父节点设置overflow:scroll,但是不管滚动条如果滚动，但是子节点一直都不动，因此就小研究了一下position对overflow的影响，跟大家分享一下。

## 当父节点不设置position情况下，子节点position的四种值的分析：
示例1.1:
body{
A {overflow: scroll;}
A-1 {}
}
效果：A-1会根据A滚动条的滚动而滚动
分析：A-1的默认position设置为static，当position为static时，A-1元素还是遵循正常的文档流，因此A-1会受它父节点属性的影响

示例1.2:
body{
A {overflow: scroll;}
A-1 {position: relative;}
}
效果：A-1会根据A滚动条的滚动而滚动
分析：当A-1的position设置为relative时，A-1元素还是遵循正常的文档流，因此A-1会受它父节点属性的影响

示例1.3:(重点)
body{
A {overflow: scroll;}
A-1 {position: absolute;}
}
效果：A-1不会根据A滚动条的滚动而滚动
分析：当A-1的position设置为absolute时，A-1元素脱离了文档流，所以A-1不再受父节点属性的影响
注意：这时在父节点没有设置position的时，只会受到body节点的影响

示例1.4:
body{
A {overflow: scroll;}
A-1 {position: fixed;}
}
效果：A-1不会根据A滚动条的滚动而滚动
分析：当A-1的position设置为fixed时，A-1元素脱离了文档流，这时A-1只受body元素的影响


## 当父节点设置position值为非static情况下，子节点position的四种值的分析：
示例2.1:
body{
A {position：relative; overflow: scroll;}
A-1 {}
}
效果：A-1会根据A滚动条的滚动而滚动
分析：跟示例1.1一样，当父节点A设置了position之后，子节点A-1还是遵循正常的文档流，因此A-1会受它父节点属性的影响

示例2.2:
body{
A {position：relative; overflow: scroll;}
A-1 {position: relative;}
}
效果：A-1会根据A滚动条的滚动而滚动
分析：跟示例1.2一样，当父节点A设置了position之后，子节点A-1还是遵循正常的文档流，因此A-1会受它父节点属性的影响

示例2.3:(重点, 注意跟1.3示例对比)
body{
A {position：relative; overflow: scroll;}
A-1 {position: absolute;}
}
效果：A-1会根据A滚动条的滚动而滚动
分析：当父节点A设置了position之后，效果就跟示例1.3不一样了，这时A-1会受到离它自己最近的一个设置了position属性的父节点的影响，再看下面一个示例：
body{
A {position：relative; overflow: hidden;}
A-1 {overflow: scroll;}
A-1-1 {position: absolute;}
}
注意：这时A-1-1不会收A-1的影响，但是会受到A的影响

示例2.4:
body{
A {position:relative; overflow: scroll;}
A-1 {position: fixed;}
}
效果：A-1不会根据A滚动条的滚动而滚动
分析：跟1.4示例一样，当子节点的position属性设置为fixed之后，不管的父节点是否设置了position值，都只会受到body节点的影响，其他任何节点都不会影响它