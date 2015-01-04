title: Angular之required和ng-required的区别
date: 2014-12-31 16:16:21
categories: Angular
---
* required和ng-required的作用
  当提交的表单时，通常都会做一些表单验证，当然也避免不了空值的检测。在angular里可以给input，select等设置required属性来对表单进行验证，不用自己再花时间去写验证。

* 例如我们需要验证name名为myFrom下的userName文本框是否为空，我们可以给文本框设置required属性，然后通过myForm.userName.$error.required来获取验证结果。
      <form name="myForm">
        User name: <input type="text" name="userName" required>
        <span class="error" ng-show="myForm.userName.$error.required">Required!</span>
      </form>

* 也可以设置ng-required来进行验证设置，ng-required跟required的区别是前者可以通过设置一些表达式来判断是否需要验证。
      <javascript>
        scope.userName = {name: 'zhangsan', validate: true}
      </javascript>
      <form name="myForm">
        User name: <input type="text" name="userName" ng-required="userName.validate">
        <span class="error" ng-show="myForm.userName.$error.required">Required!</span>
      </form>