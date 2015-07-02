title: 理解Directive中各个方法的执行顺序
date: 2015-07-02 14:46:43
categories: Angular
---
> Directive 在angular中扮演着非常重要的角色，而且对新手来说了使用起来也比较复杂。所以有必要来对 directive 做一个详细的分析，本片文章只来谈一下Directive中各个方法的执行顺序。

* 先看下面的比较完整的Directive代码：
      app.directive("simple", function(){
         return {
           restrict: "E",
           template:"<div></div>",
           controller: function(scope, element, attributes){
             console.log("controller");
           },
           compile: function(element, attributes){
             console.log("compile");
             return {
                 pre: function(scope, element, attributes, controller, transcludeFn){
                   console.log("pre");
                 },
                 post: function(scope, element, attributes, controller, transcludeFn){
                   console.log("post");
                 }
             }
           }
         };
      });

* controller, compile, pre 和 post 的执行顺序如下：
  1.compile (只会执行一次, 此过程是用来编译template, 但是不会执行渲染)
  2.controller (不执行渲染)
  3.pre (不执行渲染)
  4.post (执行渲染)

* 其他关于Directive的详细讲解请看下面链接：
  * [深入理解Directive里的每个方法](http://odetocode.com/blogs/scott/archive/2014/05/28/compile-pre-and-post-linking-in-angularjs.aspx)