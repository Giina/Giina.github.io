---
title: 5月bug
lang: zh
date: 2017-06-06 14:12:51
tags: ["bug"]
category: bug
---

### 1. mobile在android浏览器和ios浏览器中体现不同
令人疑惑的是之前的HTML5页面没有这种问题，只好去恶补了一下移动网页开发的相关知识

### 2. windows环境，npm run指定外部访问
[Enable connecting to localhost:3000 from another computer](https://github.com/nuxt/nuxt.js/pull/90)

```
//Via a env variable HOST:not work
"scripts": {
  "dev": "HOST=0.0.0.0 nuxt"
}

//Via a nuxt config in the package.json:it's work
"config": {
    "nuxt": {
      "host": "0.0.0.0"
    }
},
"scripts": {
    "dev": "nuxt",
}
```

同事的mac环境中：
```
HOST=0.0.0.0 npm run dev
```

### 3. VUEX -> 中间件
从其参数context的变量和方法可以看出，中间件执行结果有路由重定向和展示错误页
可以使用在`nuxt.config.js`或者layouts/pages中使用

### 4. bootstrap modal 官方方法
企图在modal中实现多页面切换、给第一个页面的按钮添加了任何方法，都会导致modal隐藏
