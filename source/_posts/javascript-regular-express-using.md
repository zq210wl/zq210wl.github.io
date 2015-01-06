title: javascript之正则表达式的使用
date: 2014-11-20 15:11:22
categories: Javascript
---
* __正则表达式的两种声明方法：__
  * 直接变量法(建议使用)
    * 语法: `/pattern/attributes`
  * 创建 RegExp 对象
    * 语法：`new RegExp(pattern, attributes)`
* __参数 attributes 是一个可选的字符串，包含属性 “g”、”i” 和 “m”，分别用于指定全局匹配、区分大小写的匹配和多行匹配。__
  例如：
      var regExp = /(\d+)|([A-Za-z]+)/igm;
      new RegExp("(\d+)|([A-Za-z]+)", "igm");

## RegExp 对象常用的两个方法的使用：

* test() 方法检索字符串中的指定值。返回值是 true 或 false。
      var patt1 = new RegExp("e");//也可直接写为：var patt1 = /e/;
      var str1 = 'fdfedsfsf';
      console.log(patt1.test(str1));// true
* exec() 方法检索字符串中的指定值。返回值是被找到的值。如果没有发现匹配，则返回 null
      var patt2=new RegExp("e");
      console.log(patt2.exec("The best things in life are free"));//["e", index: 2, input: "The best things in life are free"]

## String对象会用到正则的四个方法：

* match() 方法可在字符串内检索指定的值，或找到一个或多个正则表达式的匹配;
  返回值：存放匹配结果的数组
      var regExp1 = /(\d+)|([A-Za-z]+)/g;
      //或者：regExp1 = new RegExp('(\\d+)|([A-Za-z]+)', "g");
      var regStr1 = 'jkj12dsfs,.,fddsfFDF,.FDfsdfdsFdsfDSf￥32￥324f';
      var matchArr1 = regStr1.match(regExp1);
      console.log(matchArr1);

* replace() 方法用于在字符串中用一些字符替换另一些字符，或替换一个与正则表达式匹配的子串。
  返回值：一个新的字符串
      var regExp2 = /\d+/gm;
      var regStr2 = 'fdf78767ds6f6gf87dsf67ds8f5ds7f7dsf';
      var newStr = regStr2.replace(regExp2, '');
      console.log(newStr);//["jkj", "12", "dsfs", "fddsfFDF", "FDfsdfdsFdsfDSf", "32", "324", "f"]

* split() 方法用于把一个字符串分割成字符串数组。
  返回值：一个字符串数组
      console.log("2:3:4:5".split(":"));  //返回["2", "3", "4", "5"]
      console.log("|a|b|c".split("|"))  //返回["", "a", "b", "c"]

* search() 方法用于检索字符串中指定的子字符串，或检索与正则表达式相匹配的子字符串。
  返回值：第一个与 regexp 相匹配的子串的起始位置
  说明：search() 方法不执行全局匹配，它将忽略全局标志 g。
      var str="hello World!";
      console.log(str.search(/world/i));