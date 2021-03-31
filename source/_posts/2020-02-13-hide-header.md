---
title: 網頁下滾時隱藏header，上滾時才顯示
date: 2020-02-13 15:12:35
thumbnail: https://i.imgur.com/5XIMwLs.png
categories: 前端開發
tags:
- w3HexSchool
- w3Hexschool-2020-challenge
- 接案
- 接案2019
- NPM package
---

![能隱藏header的工具，headroom.js](https://i.imgur.com/5XIMwLs.png)


## 前言

在 2019 年接案時，曾接到一個需求是，當網頁處在往下滾動狀態時，header是隱藏起來的；而在網頁往上滾動、或網頁已經在最頂端時，header 才會顯示出來。之所以想完成這個效果，可能是想節省空間。因為 header 是讓使用者跳轉到其他頁面的導覽列，而當使用者做出向下滾動網頁的動作時，代表他們需要的是瀏覽後續的網頁。如果在往下滾動時隱藏 header，就能留給使用者更多的螢幕空間去看內容，體驗會更好。

以下是我當時的解法：headroom.js

![下滾時隱藏header，上滾時顯示](https://i.imgur.com/5KfwFWr.gif)

<!-- more -->

## headroom.js

我記得當時有想過用 CSS 方案（例如 `position: sticky`），或是 JS 方案（監測網頁位置，改變 header 的狀態）。在 google 的過程中，剛好看到有 headroom.js 工具，就決定使用它了。headroom.js 同時有 CDN 和 NPM 途徑可使用，對試用或前期開發都用 CDN 的我來說還滿方便的。先附上官網：
* [Hide your header on scroll - Headroom.js](https://wicky.nillia.ms/headroom.js/)

引入 headroom.js 的方式如下
```
// cdn 方案
<script src="https://unpkg.com/headroom.js@0.9.4/dist/headroom.js"></script>

// npm 方案
npm install headroom.js --save
```

使用的方式也很簡單。如果是預設用法的話，在 header 上加個 class、再搭配官網提供的 JS 初始化程式碼就 OK 了。
```html
<!-- initially -->
<header class="headroom">

<!-- scrolling down -->
<header class="headroom headroom--unpinned">

<!-- scrolling up -->
<header class="headroom headroom--pinned">

```
```js
// if you're using a bundler, first import:
import Headroom from "headroom.js";
// grab an element
var myElement = document.querySelector("#header");
// construct an instance of Headroom, passing the element
var headroom  = new Headroom(myElement);
// initialise
headroom.init();
```

## 小結

當時因為用 headroom.js 就已解決需求，後續就沒研究細節或其他方案了。若後續若有相關需求的話，我應該會把其他的設定再好好讀一遍。


## 延伸/參考資源

官方
* [Hide your header on scroll - Headroom.js](https://wicky.nillia.ms/headroom.js/)
* [WickyNilliams/headroom.js: Give your pages some headroom. Hide your header until you need it](https://github.com/WickyNilliams/headroom.js)
* [Headroom.js demo](https://codepen.io/WickyNilliams/pen/AFsKB?editors=1010)

教學介紹
* [[十分鐘學習] Headroom.js - 活化導覽列 - iT 邦幫忙：：一起幫忙解決難題，拯救 IT 人的一天](https://ithelp.ithome.com.tw/articles/10197806)
* [Build a Sticky Navigation with Headroom.js - Better Programming - Medium](https://medium.com/better-programming/lets-build-a-sticky-navigation-b20be4dd77f)