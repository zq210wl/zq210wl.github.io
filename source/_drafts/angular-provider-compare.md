title: angular中自定定义服务service的方法以及比较
date: 2015-06-29 10:57:19
categories: Angular
---
* 第一种 provider 方法
  * 需要实现 __this.$get__ 方法，并且此方法返回一个对象
  * Providers 是唯一一种你可以传进 __.config()__ 函数的 __service__。当你想要在service对象启用之前，先进行模块范围的配置，那就应该用 __provider__。
  * 所有的provider都可以通过在后面添加后缀__Provider__串来传进.config().
    - 比如一个叫 __xxx__ provider service, 需要写成 __xxxProvider__ .
  * 写法如图：
    ![](/imgs/angular_provider.png)

* 第二种 factory 方法
  - Factory   方法直接把一个函数当成一个对象的 __$get__ 方法, 可以直接返回字符串
  - 用  Factory 就是创建一个对象，为它添加属性，然后把这个对象返回出来。你把 __service__ 传进 __controller__ 之后，在 __controller__ 里这个对象里的属性就可以通过 __factory__ 定义的 service 使用了。
  - 写法如图：
    ![](/imgs/angular_factory.png)

* 第三种 service 方法
  - Service 是用"new"关键字实例化的。因此，你应该给"this"添加属性，然后 __service__ 返回"this"。你把 __service__ 传进 __controller__ 之后，在controller里  "this" 上的属性就可以通过 __service__ 来使用了.
  - 写法如图：
    ![](/imgs/angular_service.png)