---
title: addLoadEvent：一个共享onLoad触发事件的JavaScript函数
date: 2018-10-28 02:10:31
tags:
  - Js
categories: JavaScript
---
## 函数说明

一个共享onLoad的JavaScript函数，适用于HTML页面加载完毕之后需要同时触发多个onLoadJS事件，由Simon Willison 编写。

<!-- more -->

## 函数代码

```JavaScript
/* test为需要加载的函数名 */
addLoadEvent(test);

/**
 * [addLoadEvent description]
 * @param {[type]} func [description]
 */
function addLoadEvent(func) {
    var oldonload = window.onload;
    if (typeof window.onload != "function") {
        window.onload = func;
    } else {
        window.onload = function() {
            oldonload();
            func();
        };
    }
}

/**
 * [test description]
 * @return {[type]} [description]
 */
function test() {
   //你的代码
}
```
