---
title: 4月bug
lang: zh
date: 2017-05-02 11:55:51
tags: ["bug"]
category: bug
---


1. ### Nuxj+bootstrap: jquery is not defined

[官方github issue](https://github.com/nuxt/nuxt.js/issues/178)

2. ### inline-block元素有间距

[去除inline-block元素间间距的N种方法](http://www.zhangxinxu.com/wordpress/2012/04/inline-block-space-remove-%E5%8E%BB%E9%99%A4%E9%97%B4%E8%B7%9D/)

3. ### vue when I use array to bind a class like `:class="{active:array[3]}"`, UI refreshes very slow

4. ### '$' is not defined no-undef

```
 ERROR  Failed to compile with 1 errors                         11:26:18

 error  in ./pages/technologies/index.vue

E:\Project\MetaLab2\maikeji_v6_front_mobile\pages\technologies\index.vue
  89:11  error  '$' is not defined       no-undef
  90:17  error  '$' is not defined       no-undef
  90:43  error  '$' is not defined       no-undef
  91:15  error  '$' is not defined       no-undef
  93:15  error  '$' is not defined       no-undef

✖ 6 problems (6 errors, 0 warnings)
```

[answer](https://github.com/SimulatedGREG/electron-vue/issues/36)
It looks like you got everything setup properly. The error you are receiving is from ESLint's no-undef rule. Since jQuery uses the global variable $ or jQuery, ESLint needs to be configured to know about it. Within your .eslintrc.js file, add them to globals.

.eslintrc.js (docs)

```
{
  // Other configs...
  "globals": {
    "$": true,
    "jQuery": true
  }
}
```

区分问题1和4

