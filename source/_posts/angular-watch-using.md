title: Angular之watch的特殊使用
date: 2014-12-31 15:44:19
categories: Angular
---
> 使用AngularJs开发项目的同学应该对watch很熟悉了，在项目中难免会用到watch来监听scope中值的变化来执行相应的操作.

* $watch的常规使用：
      scope.name = 'aa';
      scope.$watch('aa', function(newVal, oldVal){
         //执行相应操作
      });

* 特殊使用，因为watch可以用来监听一个函数，所以当我们需要每次执行$digest()都执行一个操作（即scope发生变化的时候），这是我们就可以把第一个参数设置成一个我们需要每次都执行的函数。
      scope.$watch(function(){
         //每次都需要执行的操作
      });