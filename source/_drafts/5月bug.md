---
title: 5月bug
tags:
---
1. mobile在android浏览器和ios浏览器中体现不同
令人疑惑的是之前的HTML5页面没有这种问题，只好去恶补了一下移动网页开发的相关知识

2. windows环境，npm run指定外部访问
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