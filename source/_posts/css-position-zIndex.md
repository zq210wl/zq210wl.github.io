title: position属性和z-index属性对页面节点层级的影响总结
date: 2014-07-14 18:30:55
categories: CSS
---
> 最近在做的一个Web项目中因为很多地方都要用tooltip对某些功能和操作做一些信息提示，以便用户可以很容易的理解和使用本系统，由于页面和tips比较多，做的当中遇到了各种奇葩的z-index的问题，也相信很多人在项目中也都多多少少曾因遇到各种不可预期层级遮盖问题而烦恼，所以我决定花点时间来好好研究一些这方面的问题，跟大家分享一下，希望能对大家有所帮助。

## 同级元素比较：
一.
结论：只设置z-index还没有设置position为relative或absolute或fixed，则z-index是不会起作用的。
示例：
{
A: {z-index:3}
B: {z-index:2}
C: {z-index:1}
}
从上到下的层级关系为：C > B > A
二：
结论：同级元素不设置position,则后面元素会覆盖前面元素
示例：
{
A: {}
B: {}
C: {}
}
从上到下的层级关系为：C > B > A
三：
结论：同级元素之间设置了position(非static)的元素会覆盖没有设置position(或为static)的元素
示例：
{
A: {position:relative;}
B: {}
}
从上到下的层级关系为：A > C
四：
结论：同级元素之间都设置了position(非static)，则后面的元素会覆盖前面的元素
示例：
{
A: {position:relative;}
B: {position:relative;}
}
从上到下的层级关系为：B > A
五：
结论：同级元素之间都设置了position(非static)，那么设置了z-index(大于0)的元素会覆盖没有设置的元素
示例：
{
A: {position:relative;z-index:1}
B: {position:relative;}
}
从上到下的层级关系为：A > B
六：同级元素之间，各种层级的混合比较，直接看示例：
{
A: {}
B: {position:relative;z-index:2}
C: {position:relative;}
D: {position:relative;z-index:1}
E: {position:relative;z-index:0}
F: {position:relative;}
G: {}
H: {position:relative;z-index:-1}
}
从上到下的层级关系为：B > D > F > E > C > G > A > H

## 多级元素比较：
一.
结论：父级元素设置了position(非static)或者没有设置的情况下，当子节点没有设置position或只设置了position的情况下，则子节点的层级会受到父节点的影响; 当子节点设置了position(非static)且又设置了z-index(大于0)，则子节点的层级不会受到父节点层级的影响
示例1：
{
A: {}
A-1: {}
B: {}
B-1: {}
}
B以及B的所以子元素会覆盖在A以及A的所有子元素
从上到下的层级关系为：B-1 > B > A-1 > A
示例2：
{
A: {position:relative}
A-1: {}
B: {position:relative}
B-1: {}
}
B以及B的所以子元素会覆盖在A以及A的所有子元素
从上到下的层级关系为：B-1 > B > A-1 > A
示例3：
{
A: {}
A-1: {position:relative}
B: {}
}
从上到下的层级关系为：A-1 > B > A
示例4：
{
A: {position:relative;}
A-1: {position:relative;z-index:2;}
A-2: {}
B: {position:relative;}
B-1: {position:relative;z-index:1}
B-2: {}
}

从上到下的层级关系为：A-1 > B-1 > B-2 > B > A-2 > A

二.
结论：父级元素设置了position(非static)和z-index的情况下，则子节点的层级会受到父节点层级的影响，且子节点会一直覆盖父节点的。
示例1：
{
A: {position:relative;z-index:1}
A-1: {position:relative;z-index:2}
A-2: {position:relative;z-index:-100}
B: {position:relative;z-index:3;}
B-1: {position:relative;z-index:4}
B-2: {position:relative;z-index:5}
}
B以及B的所有子元素会覆盖A以及A的所有子元素
从上到下的层级关系为：B-2 > B-1 > B > A-1 > A-2 > A

很多人将 z-index 设得很大, 9999 什么的都出来了, 如果不考虑父节点的影响, 设得再大也没用, 那是无法逾越的层级.

三.【负z-index跟position的关系】
结论1：当父节点设置了position(非static)但没有设置z-index的情况下，子节点如果设置position(非static)和负的z-index值，子节点会被父节点覆盖
{
A: {position:relative;}
A-1: {position:relative;z-index:-1}
}
从上到下的层级关系为：A > A-1

结论2：当父节点设置了position(非static)和z-index的情况下，子节点如果设置position(非static)和负的z-index值，子节点不会被父节点覆盖
{
A: {position:relative;z-index:1}
A-1: {position:relative;z-index:-1}
}
从上到下的层级关系为：A-1 > A

## 总结
__上中下三个大层级__(非W3C官方定义，只是个人为了好理解，以下文字总结可能不是太准确，请参照示例来分析)：
将没有设置z-index值，或z-index值为0，或z-index值为auto的所有元素归为一类(AAA);
将设置了position(非static)和z-index值大于0的所有元素归为一类(BBB);
将设置了position(非static)和z-index值小于0的所有元素归为一类(CCC);
结论：BBB类的元素会高于AAA和CCC类, AAA类元素会高于CCC类。
示例：
{
A: {position:relative}
A-1: {position:relative;z-index:-20}
B: {position:relative;z-index:2}
B-1: {position:relative;z-index:-10}
C: {position:absolute;z-index:3}
D: {}
E: {position:fixed;z-index:1}
F: {position:fixed;z-index:-1}
G: {position:relative;z-index:0}
H: {position:fixed;z-index:-2}
}
从上到下的层级关系为：B B-1 C E > A D G > A-1 F H

## 后话：
以上是我本人对position属性和z-index属性的所有可能性情况的分析以及总结。相信很多人也曾遇到过这样的问题：滚动条任你如何滚动，也奈何不了子节点一动不动。 针对这个问题，有时间我会写一篇position属性和scroll属性之间关系的文章跟大家分享一下。