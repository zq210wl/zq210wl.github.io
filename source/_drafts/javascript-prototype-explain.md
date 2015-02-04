title: 详解prototype
tags:
---
* prototype 和 constructor 中声明属性的不同
* prototype 属性的修改以及顺序会对实例属性造成声明影响

详细解释一下prototype的原理


## 实例属性的获取
```
function A(){
  this.y = "yy";
}
A.prototype.x = "xx";
A.prototype.y = function(){
  console.log("yyyyy");
}
var a = new A();
```

  * `a.x // "xx"`
  * `a.y // "yy"`
  * `a.y() // TypeError: string is not a function`


## 只有构造函数才有prototype属性