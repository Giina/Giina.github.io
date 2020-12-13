---
title: 'mwb:pixels'
tags:
---
> reference:
> [移动端高清、多屏适配方案](http://www.html-js.com/article/Mobile-terminal-H5-mobile-terminal-HD-multi-screen-adaptation-scheme%203041)
> [rem 产生的小数像素问题](http://taobaofed.org/blog/2015/11/04/mobile-rem-problem/)
> [移动端尺寸基础知识](http://colachan.com/post/3435)
> [消除viewport的疑惑-移动网页开发](https://www.zybuluo.com/gongzhen/note/170557)
> [手机端页面自适应解决方案—rem布局进阶版（附源码示例）](http://www.jianshu.com/p/985d26b40199)

keywords:

* physical pixel: tiniest unit of a screen, defined by physical

* density-independent pixel: a parameter of a phone, decided by system and physical;equals to size of the device's screen shot

* device pixel ratio: dpr=pp/dip

`mark1`:retina screen need much more clear pictures, because a pixel in the pic will be showed by 4 physical pixels , meanwhile the same dip android screen show the pic better;

`mark2`: downsampling is a process shrinking 4 pixels to 1.

carefun:

1. image*2

2. border=1px