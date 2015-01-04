title: Angular之$compile函数的使用
date: 2014-12-31 16:29:45
categories: Angular
---
* __Angular之$compile函数的使用__

  在用Angular写一些比较复杂的功能的时候，难免会遇到这样的需求：需要懂动态的往页面中插入一些元素，而且这些元素还需要跟scope中的的某些值绑定。

  比如要将一个div动态的插入到body中,如下:
      scope.attr = "hello";
      $("body").append('<div ng-bind="attr"></div>');
  _但是如果只是上面这么写的话，不管你`scope.attr`怎么变化, div的html都不会有变化。那么怎么才能让它们绑定到一起的呢？这就要用到`$compile`函数了。_

* __$compile函数的作用__
  `$compile`函数可以将一段html字符串或者DOM元素跟scope编译绑定到一起。

* __$compile函数如何使用__
      $compile(element)(scope);
      //element可以是一段html字符串，也可以是DOM元素；return值为编译完后的DOM元素

* __用$compile完成上面的需求__
      scope.attr = "hello";
      var html = $compile('<div ng-bind="attr"></div>')(scope);
      $("body").append(html);
      scope.$digest();//遍历scope