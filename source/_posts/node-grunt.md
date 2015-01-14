title: Grunt介绍
categories: NodeJS
date: 2015-01-07 14:54:05
---

* Grunt是什么？
  - 官方解释：JavaScript 任务运行器
  - Grunt是nodeJS的一个插件。

* Grunt能干什么?
  - Grunt可以让你解放双手，做一些自动化的任务处理来简化你的工作。

* 那Grunt到底能干什么？
  - 前端你能想到的基本上grunt都能帮你解决，因为它有非常多的plugin供你选择，总有一个是你想要的。
  - 以下是我在项目中常用的一些plugin：
    * [grunt-contrib-cssmin](https://www.npmjs.com/package/grunt-contrib-cssmin)
      - 合并压缩CSS文件
    * [grunt-contrib-uglify](https://github.com/gruntjs/grunt-contrib-uglify)
      - 混淆、合并、压缩JS文件
    * [grunt-contrib-clean](https://www.npmjs.com/package/grunt-contrib-clean)
      - 删除文件用的
    * [grunt-contrib-connect](https://www.npmjs.com/package/grunt-contrib-connect)
      - 提供一个Webserver来方便浏览
    * [grunt-contrib-watch](https://www.npmjs.com/package/grunt-contrib-watch)
      - 用来监听文件的变化来实时做出响应执行响应的任务，
      - 可以和`grunt-contrib-connect`结合来实现文件改变后自动刷新页面
    * [grunt-este-watch](https://npmjs.org/package/grunt-este-watch)
      - 同样是用来监听文件变化的，性能比`grunt-contrib-watch`好，但功能相对弱点
    * [grunt-contrib-sass](https://www.npmjs.com/package/grunt-contrib-sass)
      - 将SASS文件编译成CSS文件
    * [grunt-contrib-less](https://www.npmjs.com/package/grunt-contrib-less)
      - 将LESS文件编译成CSS文件
    * [grunt-contrib-concat](https://npmjs.org/package/grunt-contrib-concat)
      - 将多个文件合并成一个文件
    * [grunt-contrib-copy](https://www.npmjs.com/package/grunt-contrib-copy)
      - 复制文件到对应的目录
    * [grunt-processhtml](https://www.npmjs.com/package/grunt-processhtml)
      - 处理html模板
    * [grunt-html2js](https://www.npmjs.com/package/grunt-html2js)
      - 编译Angular的template到JS文件
    * [grunt-notify](https://www.npmjs.com/package/grunt-notify)
      - 用来做桌面任务通知用的
      - 比如：在任务处理成功/失败后再桌面右下角弹出信息提示框来提示任务的处理情况

* 具体使用：
  - [中文版官方文档](http://gruntjs.cn/getting-started/)
  - [英文版官方文档](http://gruntjs.com/getting-started)