title: bower - 前端包管理器
date: 2015-01-07 14:54:05
categories: Tool
---

> 许多程序语言都有自己标准的包管理器，开发者可以用其来安装所有的库文件。比如:Ruby有gem, Python有pip,Server端的javascript有npm来管理。但是客户端的javascript有没有相应的包管理器啊?有，那就是bower.

* 什么是Bower？
  - 首先，Bower是node的一个插件。
  - Bower是一个前端资源包管理器，用于搜索、安装和卸载如JavaScript、HTML、CSS之类的网络资源。

* 用Bower为给前端开发带来什么好处？
  - 节省时间; 解放繁琐的人力劳动
    * 比如通常情况下如果你的项目要用到jQuery，你需要到jQuery的官网去找到你想要的版本下载下来，然后再拷贝到你项目中相应的目录中，这样很繁琐；但是如果用Bower,你只需要输入一个命令，jquery就会安装在本地计算机上指定的目录中，你不需要去记版本号之类的东西，你也可以通过Bower的info命令去查看任意库的信息。
  - 不用担心各种库之间的依赖关系
    * 比如你项目中会用到了`bootstrap`, `jquery`, `jquery.ui`. 这三个库都用到了`jquery`，所以你必须要去找到一个合适的jquery版本来让`bootstrap`和`jquery.ui`都可以正常工作。如果用Bower,你根本不用去管这些库的依赖关系，只需要执行一个命令来就可以了，Bower会自动帮你解决依赖关系，找到合适版本库。只需要执行下面三个命令即可：
      - `bower install jquery`
      - `bower install bootstrap`
      - `bower install bootstrap`
  - 可以很容易的了解到项目中用到的所有第三方库以及它们的版本信息
    * 你可以创建一个名为`bower.json`的文件，在这个文件里你可以指定所有库的依赖关系，任何时候你需要弄清楚你正在使用哪些库，你可以参考这个文件。如下可以在安装库的时候把库的信息添加到`bower.json`的文件中：
      - `bower install jquery --save`
  - 节省版本控制服务器的空间
    * 不去需要把第三库文件提交到版本库中，只需要提交`bower.json`文件即可。开发人员从版本库中下载下来项目之后只需要执行`bower install`就会自动安装第三库到本地。
  - 让升级变得简单
    * 假设某个库的新版本发布了一个重要的安全修补程序，为了安装新版本，你只需要运行一个命令，bower会自动更新所有有关新版本的依赖关系。

## bower具体使用

具体使用请参考下面这个链接，写的很详细：
http://segmentfault.com/a/1190000000349555

bower官网地址：
http://bower.io/










