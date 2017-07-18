---
title: iconfont偏移调查
lang: zh
date: 2017-05-24 11:04:45
tags:
category: 调研
---

***注意***
* 下述“字体”仅针对iconfont（阿里巴巴图标库）

## 问题描述：
1.电脑版网页中iconfont在**position:absolute**情况下，不同环境中，字体向上偏移
2.手机版网页中iconfont在**chrome pc**和**chrome mobile**中，块位置相同，字体位置不同

### 问题1

#### 环境调查：
    * windows系统各种浏览器（chrome，火狐，qq浏览器，UC浏览器，360浏览器均为较新版本）
    * mac系统chrome

#### 调查结果
> 开发环境（windows系统各种浏览器）均符合设计图，其余环境出现字体偏移
* 使用chrome user-agent switcher在windows上修改user-agent后显示没问题——与user-agent中mozilla平台参数无关

#### 解决方案
1. 不用`position:absolute`，或者
2. 找到iconfont偏移原因

### 问题2

#### 环境调查：
    * ios系统微信浏览器
    * android系统微信浏览器+手机浏览器
    * chrome PC 模拟手机浏览器（开发环境）

#### 调查结果
> 开发环境（chrome PC 模拟手机浏览器）与设计图一致，其余字体偏移



@2017.06.07转交

@2017.06.14回到我手里

<script async src="//jsfiddle.net/geogia/n3q14axs/9/embed/"></script>