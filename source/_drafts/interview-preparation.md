title: interview_preparation
date: 2015-07-06 14:44:57
categories: other
---
* 熟悉 Array 常用方法
  -

* 熟悉 String 常用方法
  - str.split(",");
  -

* 熟悉 Data 常用方法

* 熟悉CSS3新增的一些属性

* 事件相关的知识
  - 冒泡和捕获
  - 如何注册监听
  - ...

* Jquery中一些方法的比较
  - live, bind
  - delegate
  - ...

* Ajax 原声写法

* 自动化测试
  - jasmine
  - Karma
  - protractor
    * Protractor is an end to end test framework for AngularJS applications built on top of WebDriverJS.
  - Selenium

* 测试代码的性能工具
  - Speed Tracer: chrome的1个插件，speedtrace的优势点是用于监控JS的解析执行时间，还可以监控页面的重绘、回流
    * 使用：https://developers.google.com/web-toolkit/speedtracer/get-started?csw=1

* SASS常用的一些方法

* SASS和LESS的区别

* CSS权重
  - style : 1000
  - id : 100
  - class, psuedo-class, attribute : 10
  - element: 1

* Describe BFC(Block Formatting Context) and how it works.

* What's the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?

* 用CSS预处理器的好处和坏处？SASS,less
  - http://segmentfault.com/q/1010000002527156/a-1020000002527759

* 深度克隆

  function deepClone(data){
    var newData;
    if(Object.prototype.toString.call(data) == "[object Object]"){
      newData = {};
      for(var i in data){
        newData[i] = deepClone(data[i]);
      }
    }else if(Object.prototype.toString.call(data) == "[object Array]"){
      newData = [];
      for(var i in data){
        newData[i] = deepClone(data[i]);
      }
    }else{
      newData = data;
    }
    return newData;
  }

* getPosition() 方法实现

  function getPosition(obj){
   var x = obj.offsetLeft;
   var y = obj.offsetTop;
   while(obj.offsetParent){
      obj = obj.offsetParent;
      x += obj.offsetLeft + window.getComputedStyle(obj, null).borderLeftWidth.split("px")[0]);
      y += obj.offsetTop + window.getComputedStyle(obj, null).borderTopWidth.split("px")[0]);
   }
   return {"x":x,"y":y};
  };

* 跨域的几种方式：
  * jsonp
  * window.postMessage
  * window.name + location = '';
  * CORS