---
title: Bootstrap-Sass
date: 2016-01-26 13:39:40
tags: 技
---

# 关于Bootstrap和Sass

* 定制自己的主题时，将原生属性复制到自己的文件中，进行新的赋值/覆盖

```variables in customize file
//$font-size-base:14px !default;
$font-size-base:20px !default;
```

* 查找需要修改的变量时在整个原生项目中查找（知道变量名时），当你不知道变量名，可以根据模块在文件中查找

* 善于使用bootstrap-sass的mixin方法

```mixin in bootstrap-sass
@mixin make-row($gutter: $grid-gutter-width) {
    margin-left:  ($gutter / -2);
    margin-right: ($gutter / -2);
    @include clearfix;
}
```
