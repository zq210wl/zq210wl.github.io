title: 自己刚开始学习移动web开发时的一些基础知识的学习笔记
categories: Mobile
date: 2014-03-29 16:21:26
---

1. 设备/物理/屏幕像素（px）:  点（dot）；一个 px 代表一个点。
2. css像素（px）: 相对与物理像素的像素；一个css px 等于 一个或多个物理px。
3. 分辨率像素：指整个设备屏幕里所能容纳的像素（dot）数。1024px * 768px ；当分辨率调整到最大值时，一个px代表一个物理px。分辨率调小时，一个px代表多个物理px。
4. 像素（px）密度：不同分辨率下的像素密度不用。这里的px也是相对的。
5. 图片在设备中的显示情况：一个图片设计为 80px*90px，这里的px指的是真正物理像素点，如果缩放比为2，则图片将被放大到两倍的物理像素 160px*180px 。
6. devicePixelRatio = 手机的物理像素与实际使用像素的缩放比。
7. width=device-width：
    width指的是layout（页面布局）宽度；
    device指的是屏幕分辨率宽度，即设备独立像素（dip）。
8. DPI：Dots Per Inch
9. PPI: Pixels Per Inch
