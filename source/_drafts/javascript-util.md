title: 实用工具方法
date: 2015-07-16 13:58:10
categories: Javascript
---

* 获取两个数之间的一个整数
      function getRandomInt(min, max) {
        return Math.floor(Math.random() * (max - min)) + min;
      }

* 获取数组中的最大值
      function getMaxOfArray(numArray) {
        return Math.max.apply(null, numArray);
      }

* 获取数组中的最小值
      function getMinOfArray(numArray) {
        return Math.min.apply(null, numArray);
      }

* 将数组中的数字按升序排列
      function sortByAsc(numArray) {
        return numArray.sort(function(x, y){
          if(x > y){
            return 1;
          }else{
            return -1;
          }
        });
      }

* 将数组中的数字按降序排列
      function sortByAsc(numArray) {
        return numArray.sort(function(x, y){
          if(x < y){
            return 1;
          }else{
            return -1;
          }
        });
      }

* 去除数组重复的数据
      function delRepeat(arr){
        var newArr = [];
        var obj = {};
        for(var i=0;i<arr.length;i++){
          if(obj[arr[i]]==undefined){
            obj[arr[i]] = 1;
            newArr.push(arr[i]);
          }
        }
        return newArr;
      }

* 将一个伪数组转换为真正的数组
      var arg = Array.prototype.slice.call(arguments);



