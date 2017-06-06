---
title: 2月bug
lang: zh
date: 2017-02-27 10:01:45
tags: ["bug"]
category: bug
---
> 

### 1. 用webstorm在chrome调试页面时一直弹出说页面未经授权。

`ctrl_alt_s` 或者 `File > Settings > Build、Execution、Deployment > Debugger` 选中 `Allow unsigned request` 

> [答案](https://segmentfault.com/q/1010000005600389/a-1020000005648617)

### 2. jquery-ui.min.js: Uncaught TypeError: b.nodeName.toLowerCase is not a function

修改与之前貌似name是大小写+下划线，修改成全部小写以后就正常了，所以还是不知道错在哪

> [答案](http://blog.csdn.net/you23hai45/article/details/51881328)


