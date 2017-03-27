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

5. ### webstorm总是因为npm_modules崩溃

通常我都是在打开项目npm install结束之后设置文件夹目录exclude，但是这样很容易在没设置之前开启项目时webstorm崩溃，然后我在想是不是有什么方式能让webstorm自动忽略npm_modules，不用每次手动exclude。[答案](http://www.cnblogs.com/chengwb/p/6183440.html)

6. ### 浏览器访问http://localhost:8080 时不加载template文件：net::ERR_BLOCKED_BY_CLIENT

装了adblocker[答案](http://stackoverflow.com/questions/23341765/getting-neterr-blocked-by-client-error-on-some-ajax-calls)

7. ### 打开vue-hackernews-2.0的js文件会报错：“are not supported by current JavaScript version”

`ctrl`+`alt`+`s`调出设置项，点击`Languages & Frameworks`目录下的`javascript`，右侧选择 javascript language version