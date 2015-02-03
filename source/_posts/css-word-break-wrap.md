title: 文本换行相关的CSS属性说明
date: 2015-02-03 16:43:41
categories: CSS
---

> 在div中，文本布局经常出现，换行混乱的情况。问题表现：
> 1.如果是全英文字符串,中间不包含任何符号(包括空格)，不自动换行.
> 2.中英文混写，则在英文字符串的开始处换行（英文长度>div长度），结尾处不换行。
> 3.英文整个单词换行。等等，可能还有一些问题，这里只列出了常见的几个；

- word-wrap
  - 设置文字的能被中断和包裹
  - 是针对元素内的__每一个单词__而言，比如文字超长超出边界，将如何处理。
  - `word-wrap: break-word;` - 当长单词超出container的限制时，单词会折断到下一行显示

- word-break
  - 规定__非中日韩__文本的换行规则。(对中文正常换行，对英文按照如下说明处理)
  - `word-break: break-all;` - 允许在单词被截断换行。(即在容器末端有长单词不能完全显示，会截断单词)
  - `word-break: keep-all;` - 只能在半角空格或连字符处换行。

- text-overflow
  - `text-overflow:clip;` - 显示省略标记（...），而是简单的裁切
  - `text-overflow:ellipsis;` - 当对象内文本溢出时（超过width部分）显示省略标记（...）
    - 要想让`text-overflow:ellipsis;`生效，必须要先设置`overflow:hidden;white-space:nowrap;`

- white-space
  - 设置如何处理元素内的空白
  - 是针对元素内的__整段文本__而言，比如整段文本是强制显示在一行还是分行显示
  - `white-space: nowrap` - 强制在同一行内显示所有文本，直到文本结束或者遭遇br对象。

