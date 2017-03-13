---
title: 3月bug
tags:
---
1. ### TypeError: encodeUriSegment is not a function... in angular-resource.js

> I got the issue with angualr-resource 1.6.0. I did not find the issue in 1.5.8 . [angular-resource.js encodeUriSegment Issue #5438](https://github.com/angular/angular.js/issues/5438)

2. ### Error: ENOENT: no such file or directory, scandir '**/node_modules/node-sass/vendor'

> `npm rebuild node-sass` [Error: ENOENT: no such file or directory, scandir '**/node_modules/node-sass/vendor' #1579](https://github.com/sass/node-sass/issues/1579)

3. ### 高企认定工具页面刷新测试bug

使用了SeedUI，页面的刷新逻辑是自己写的，由以下几部分组成：

```
//刷新则回到第一页
    if (location.href.split('#').length > 1) {
        location.href = location.href.split('#')[0].trim();
    }
    
//初始化时，历史记录就有了，说明刷新过了
            if (this.history.list.length > 0) {
                <!--console.log("刷新", this.history.list);-->
                document.querySelector("#intro-Section").classList.add("active");
                this.history.list = ["#intro"];
                <!--console.log("刷新", this.history.list);-->
            }
```

测试工具：微信web开发者工具、android手机、chrome浏览器
测试目标：高企工具本地站点、高企工具测试站点
测试功能：任何页面刷新都会回到首页
结论：只有在微信中打开高企工具测试站点进行测试时，刷新后一直处于loading动画

4. ### git感应不到的文件夹

在博客仓库中，我曾经在source文件夹下新建了git仓库，然后它的父文件夹作为一个git仓库时会记录source文件夹的存在但不记录其中内容的改变（git仓库嵌套），我删除source子仓库后父仓库对其中改变无动于衷。

解决：重命名source文件夹，提交，将文件夹名字改回source。我猜原因大概是要形成记录。