---
title: 监控视频播放粗糙demo制作过程
lang: zh
date: 2018-02-01 16:49:14
tags:
category: "工作"
---
## PlayCtrl.dll
1. What is PlayCtrl.dll?
软解码库组件（windows），主要用于对实时码流数据进行解码显示（预览功能）和对录像文件进行`回放解码`等。
2. Why is PlayCtrl.dll?
项目需求：海康威视监控产品保存的录像格式需要特定的SDK才能解码播放。
3. How to use?
`Attention`本段内容仅关注录像播放，无任何复杂功能。

### step1：封装API
官方提供了C++的动态链接库(Dynamic-Link Library)，第一步就是用C#类来封装其中的方法，以供用户使用。
> A dynamic-link library (DLL) is a module that contains functions and data that can be used by another module (application or DLL).[[see more]](https://msdn.microsoft.com/en-us/library/windows/desktop/ms682589(v=vs.85).aspx)

基本用法如下：
    c++ 头文件中的定义：
    NPD_API int   NP_Init();
    C#中定义函数
    [DllImport("npd_api.dll")]
    public static extern int NP_Init();
[[see more:前辈经验]](http://www.cnblogs.com/wdysunflower/archive/2010/09/01/1813947.html)
[[使用实例1-胡双挺]](http://www.cnblogs.com/dashouqianxiaoshou/p/3953312.html)
[[使用实例2-农民伯伯]](http://www.cnblogs.com/over140/archive/2010/03/12/1683973.html)

### step2：简单粗糙的界面
只是为了测试播放，所以界面简单而粗糙。我在Winform和WPF中分别尝试了一下：

* ###Winform
pictureBox + openFileDialog + button
![如图](http://ww2.sinaimg.cn/large/0063MPrKjw1erua6gzu2ej308f08ezkk.jpg)

* ###WPF
在这里遇到了两个问题：
    * [WPF中获得句柄问题](http://bbs.csdn.net/topics/390363911)
    * [AllowsTransparency与win32控件冲突](http://q.cnblogs.com/q/45220/)、[关于WPF用DirectShow做视频播放问题](https://social.msdn.microsoft.com/Forums/zh-CN/60be586b-f7c1-4191-a578-756bc6707977/wpfdirectshow?forum=wpfzhchs)、[How to avoid Airspace problem](https://social.msdn.microsoft.com/Forums/zh-CN/3ac7f98c-e128-4c84-9138-e5d8d51904fc/how-to-avoid-airspace-problem-wpf-with-winforms-control?forum=wpf)、[WPF下YUV播放的D3D解决方案](http://blog.csdn.net/yangyy9611/article/details/17464133)

界面代码请自行百度：wpf picturebox

### step3：两行代码搞定播放
`PlayM4_OpenFile()`、`PlayM4_Play()`