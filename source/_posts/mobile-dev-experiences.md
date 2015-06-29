title: 移动web开发技巧收集
categories: Mobile
date: 2015-06-26 10:08:39
---

## __meta相关__

* 设置viewport
      <meta name="viewport" content="width=device-width,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no">

* 设置格式检测format-detection
      <meta name="format-detection" content="telephone=no,email=no,adress=no">

* 添加到主屏幕后，全屏显示
      <meta name="apple-touch-fullscreen" content="yes">
      <meta name="full-screen" content="yes">

* 开启webapp功能，全屏显示，删除默认的工具栏和菜单栏
      <meta name="apple-mobile-web-app-capable" content="yes">

* 设置苹果状态栏显示样式为black
      <meta name="apple-mobile-web-app-status-bar-style" content="black">

## __link相关(web app)__

* 设置web应用程序的启动画面(对应不同设置使用不同size的图片)
      <link rel="apple-touch-startup-image" size="640x1096" href="/startup5.png" media="(device-height:568px)">

      <link rel="apple-touch-startup-image" size="640x920" href="/startup.png" media="(device-height:480px)">

* 添加至主屏幕(桌面)时的图标
      <link rel="apple-touch-icon-precomposed" sizes="57x57" href="/touch-icon-57-precomposed.png">

      <link rel="apple-touch-icon-precomposed" sizes="72x72" href="/touch-icon-72-precomposed.png">

      各尺寸自适应代码：默认：57x57; iPad：72x72; iPhone 4和Retina屏：114x114（原尺寸的2倍）;

## __CSS相关__

* 字体大小设置
      html, body { font-size: 10px; }
      otherElement { font-size: 1.4rem; }

* 实现网页在Safari快速滚动和回弹
      body {
        position: relative;
        -webkit-overflow-scrolling: touch;
      }

* 屏蔽ios和android下点击元素时出现的阴影
      body { -webkit-tap-highlight-color: rgba(255,255,255,0); }

* 阻止旋转屏幕时自动调整字体大小
      body { -webkit-text-size-adjust: 100%; }

* 禁止用户选中文字
      body { -webkit-user-select:none; }

* 禁止长按屏幕出现系统菜单(可以：禁止用户保存图片,复制图片,在新窗口打开)
      img { -webkit-touch-callout:none; }

* 屏蔽输入框怪异的内阴影
      input,textarea { -webkit-appearance:none }

* 做高清图标(宽高各缩放到一半: 100 * 100 -> 50 * 50)
      background-size

* 设置元素的宽高
      -webkit-box-sizing: border-box;


## __DOM相关__

* 自动大写与自动修正
      <input type="text" autocapitalize="off" autocorrect="off" />

## __图片设置相关__

* 通常情况下设计师在设计移动网页psd图片时要按照 320 * 320 的两倍来设计图片大小，即 640 * 640。然后从图片到页面的时候统一又缩放到一半，图片用 background-size 来设置或img标签，这样做可以放图片在不同尺寸的设备上显示差异不会太大。

## __一些实用技巧__

* 让元素border包含在的指定的宽高范围内
      border-size: border-box;

_此文章未完，将会不断更新总结_
