title: viewport到底是什么东西
date: 2015-02-06 17:09:53
categories: Mobile
---
## 浅显易懂理解viewport：
　　viewport：字面意思为视图窗口，在移动web开发中使用。表示将设备浏览器虚拟出一个新的（布局）视图窗口，并非只是ios上的独有属性，在android、window phone上同样支持viewport。它们要解决的问题是相同的，即无视设备的物理分辨率，而是直接在物理尺寸和浏览器之间重设分辨率，这个分辨率和设备的分辨率无关。比如，你拿个3.5寸-320 * 480的iphone3 gs、3.5寸-640 * 960的iphone4或者9.7寸-1024*768的ipad2，虽然设备的分辨率不同,物理尺寸也不同，但你可以通过设置viewport让它们在浏览器里有相同的分辨率。比如说，你的网站是800px宽，你可以通过设置viewport的width=800，来让你的网站在这三个不同的设备上都刚好满屏显示你的网站。这便是viewport的特性。

## viewport 相关文章
[指尖的触动-viewport非权威指南](http://jsdashi.com/development/218.html)