title: git使用中遇到的一些疑难杂症
date: 2015-01-07 14:34:21
categories: Tool
---
* 解决Git的大小不敏感问题:
  * 设置Git大小写敏感：
  `git config core.ignorecase false`
* 解决通过Git下载文件时显示无法连接的问题:
  * 将git的连接协议设置为https协议
  `git config --global url."https://".insteadOf "git://"`
_未完待续..._
