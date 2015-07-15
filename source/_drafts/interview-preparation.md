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
  * CORS(Cross-Origin Resource Sharing)
    - 只需要服务器返回数据的时候添加一个标头：
      * header("Access-Control-Allow-Origin：http://www.aa.com");

* 为什么要将静态资源放到多个域下？
  * 把静态资源放到另一个域名下，在请求静态资源的时候就不会发送cookie了，因为静态资源下不会放置cookie
  * 浏览器对一个域名下的并发连接数是有限的，所以多个域名可以提高并发连接
  * 可以做CDN(content distribution network,内容分发网络)

* defer 和 async 的区别?
  - defer
    * 延迟脚本的执行，注意这里是执行，不是加载
    * 文档完全被解析和显示后，在onload时间之前，执行
    * 执行的顺序还是按照脚本在页面中的书写顺序执行
  - async
    * 实现异步加载，不会阻塞页面，会继续往下执行
    * 当一个脚本加载完后会马上执行，这样会导致脚本执行的顺序没法控制

* Response
  - Last-Modified/Etag
    - Etag (实体标记)
      * 图片的指纹
    - Last-Modified
      * 上次修改时间
    - Date
      * 响应时间
    - Cache-control: max-age=3215645
      * 控制是否缓存和缓存声明周期
      * HTTP 1.1 的字段
      * 如果客户端不支持Cache-control，还可以用Expires
    - Expires
      * 设置失效时间
      * HTTP 1.0 定义的字段



* Request
  - If-Modified-Since/If-None-Match
    - If-Modified-Since(如果从某个时间段之后做了修改)
      * 对应Last-Modified
    - If-None-Match(如果实体标记不匹配)
      * 对应Etag

* http协议
  - http://www.cnblogs.com/bukudekong/archive/2014/07/09/3834020.html

* 回流与重绘
  - 优化
    * 用DocumentFragment完成修改，在放到页面
    * 直接使用ClassName来修改

* promise vs callback
  * JavaScript的Promises可以促进关注点分离代替紧密耦合接口