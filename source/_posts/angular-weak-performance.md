title: angular的性能分析
date: 2015-03-02 14:15:07
categories: Angular
---
> 我从2013年9月份开学习并在项目中使用 Angular, 期间遇到一些新能问题，特别是加载大数据的时候，性能明显慢下来了，当时用的还是Angular-1.0.4版本的。下面我就Angular-1.0.x版本谈下我发现的几个性能问题。


* $watch 的实现原理和性能分析
    * 只有双向绑定的scope才会被加入$watch队列，或者手动绑定$watch的$scope
    * 所有放在$scope中的变量或函数都被加入到了$watch队列当中，每次只要$scope中的一个变量的值发生变化，Angular就会自动调用$apply或者$digest来把所有在$watch队列中的变量或函数都执行一遍，然后把当前值和上一次的值就行比较，如果有变化，就会在执行一遍(一直循环，最多11次)，知道没有变化就会停止
    * 任何事件如果调用Angular的context中的函数之后，都会对$watch队列进行对比执行，不管有没有对$scope进行改变，例如：ng-click 执行了一个函数 $scope.say = function(){ \\noing },在这个函数里面没有任何操作，但还是会执行$watch队列


* ng-repeat 的原理和性能问题
    * 在ng-repeat循环中的每一个item都会建立一个单独的scope并对每个scope中的model进行$watch. 这样的话如果有200条数据，每条数据中5个属性要被$watch, 那么就是 200 \* 5次，又因为每次脏数据检测至少都需要执行两次来保证所有变化都被应用，那么就是 200 \* 5 \* 2, 在加上单独的 ng-repeat一个和其他的model为n个，就是 200 \* 5 \* 2 + 1 + n, 如果这个数据超过2500的话页面就会变得很慢了
    * 所以如果ng-repeat的数据如果只是用来展示不需要对其进行操作的话就可以取消$watch绑定，可以使用一个Angular的第三方directive： [Bindonce](https://github.com/Pasvaz/bindonce).

> 据说 Angular2.0 即将要发布了，跟之前的版本相比是一次革命性的改变。

