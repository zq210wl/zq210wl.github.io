title: instanceof 和 typeof 的介绍
categories: Javascript
date: 2015-02-06 11:05:41
---

## typeof
* 返回对应数据的类型
* 语法：typeof xxx
* javascript常用类型及其typeof返回值：
  - Undefined : "undefined"
  - Null : __"object"__
  - Boolean : "boolean"
  - Number : "number"
  - String : "string"
  - Object
    - Function object : __"function"__
    - Any other object : "object"
* [MDN官方说明](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof)


* instanceof
* 判断一个对象的__prototype属性对象__是否在某个构造函数的__prototype链__中
* 语法：object instanceof constructor
* [MDN官方说明](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/instanceof)






* 火狐 javascript 文档
https://developer.mozilla.org/en-US/docs/Web/JavaScript