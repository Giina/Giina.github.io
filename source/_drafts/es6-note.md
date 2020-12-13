---
title: es6 note
tags:
---

notes for es6

[es6特性展示与es5实现方式对比](http://es6-features.org)

[babel:es6翻译工具](http://babeljs.io/repl/)

1. hoisting

2. 参数默认值：undefined与null

3. arrow functions:箭头函数

    * `(参数[,参数]...) => ({})`
    * `参数 => {表达式[;表达式]...}`
    * `() => 表达式并返回`
    * this
    * 返回值

q1:`const createListView = name => () =>System.import('../views/CreateListView').then(m => m.createListView(name))`
联系上下文解决问题

[深入浅出ES6（十四）：let和const](http://www.infoq.com/cn/articles/es6-in-depth-let-and-const/)