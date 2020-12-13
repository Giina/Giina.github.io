---
title: VUE框架调研
date: 2017-03-30 16:39:50
tags:
---

* VueJs
    * Mobile
        * [vue-carbon](https://github.com/myronliu347/vue-carbon)
        * [vux](https://github.com/airyland/vux)
    * PC
        * [vue-material](https://github.com/marcosmoura/vue-material)
    * Operation
        * [vue-admin](https://github.com/vue-bulma/vue-admin)
        * [GoPilot](https://github.com/misterGF/CoPilot)
    * Css
        * [bulma](http://bulma.io/)
	
有点心烦，先从最简单的入手：

##### 1. Operation
需求：多角色登录，高操作性表格（表格扩展），可视化图表（图标支持）

* vue-admin = vue 2.0 + bulma 0.3
[ ]登录模块
[x]一般展示性表格
[x]可视化图表（比例图、趋势图等）：chartist(3)+chartjs(8)+piety(4)+ploty(7)
[x]富文本编辑器
[x]样式库

* GoPilot = AdminLTE with Bootstrap 3  + vue 2.0
[x]登录模块
[x]可操作表格（列筛选+数据源搜索）
[x]可视化图表（比例图、趋势图等）(2)
[ ]样式库

* 结论 
GoPilot就是一个admin模板，给出项目结构和基本样式或者插件，想要更多样式或者功能还需要自己引入其他样式库和插件库，可以用于快速搭建项目；vue-admin是一个基于admin应用场景的样式库，比前者包含了更多的自建样式和组件，适合缩短设计周期的项目开发。

##### 2. Mobile
需求：多版本兼容，移动使用习惯，网络适应，主题配置

 * ~~vue-carbon = vue 1.0 + webpack~~
 
 * muse-ui = vue 2.0 + webpack
 
 [x]主题配置稍微丰富，以白色为主
 [x]基本实现Material UI组件+其他组件
 [x]IE 10+ , Andorid 4.4+ , IOS 7+
  
 * vux = vue 2.0 + webpack
 
 [x]主题配置比较简单，以白色和灰色为主
 [x]组件比较丰富
 [x]目标用户主要为微信页面，没有明确指出支持版本
 
##### 3. PC
需求：自适应，浏览器兼容，

* vue-material

[ ]IE11中下拉框不兼容
