---
title: hexo日记
tags: ['建站','hexo']
category: 建站
---
#### [2017/02/10]

1. #### path变量

* 1.path变量是不带有根目录的路径，如`about/index.html`，注意about前没有斜杠

2. #### is_current()函数

```
function isCurrentHelper(path, strict) {
  path = path || '';

  if (strict) {  //是否为严格模式
    if (path[path.length - 1] === '/') path += 'index.html';

    return this.path === path;
  }

  path = path.replace(/\/index\.html$/, '/');

  return this.path.substring(0, path.length) === path;
}
```
因此假如我要判断当前页面是不是About的时候，is_current('about')为true（因为“this.path.substring(0, path.length) === path”）。
