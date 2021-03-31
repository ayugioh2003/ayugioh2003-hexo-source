---
title: 偵測網頁滾動或元素是否進入到畫面
date: 2020-03-25 16:38:44
thumbnail:
categories: 前端開發
tags:
- w3HexSchool
- w3Hexschool-2020-challenge
- 接案
- 接案2019
- JavaScript
---

前面幾週提到，當初開發專案時，用碰到視差滾動、或是滾動到某一元素時，就啟動某一個動畫效果。這邊整理一下如何偵測滾動、或是如何偵測元素是否進到畫面。

目前我知道有兩種方式：scroll 事件與 Intersection Observer 這個 Web API。

<!-- more -->

## 一、scroll 事件

當使用者透過輸入裝置改變網頁畫面高度時，就會觸發 scroll 事件，例如用滑鼠滾輪捲動、左鍵拖曳瀏覽器捲軸、down 方向鍵輸入等等。

可以在 .js 檔中用 (1) `addEventListner` 來偵測 scroll 事件。若偵測到的話，就在第二個參數傳入一個 function，接著這個 function 會自動執行。或是用 (2) `onScroll` 來偵測。
```js
// 第一種
window.addEventListener('scroll', function(){
  // doSomething()
})
// 第二種
window.onscroll = function() {
  // doSomething()
}
```
* [scroll - Web APIs | MDN](https://developer.mozilla.org/zh-TW/docs/Web/API/Document/scroll_event)
* [window.onscroll - Web API 接口參考 | MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/onscroll)


## IntersectionObserver Web API

先來個望詞生義。Intersection 意思是「相交處、路口」，Obersever 意思是「觀察者」。假設網頁上有幾個角色：ABC。A 是整個目前看到的畫面(viewport)、B 是在畫面外的元素(例如一張圖片) 、C 是一個只存在 JS 中且不在畫面上出現的觀察者(IntersectionObserver)。當使用者滾動畫面，B 圖片進入 A 畫面範圍時(香蕉時)，C 這個觀察者接受到這個事件發生後，就會去執行某個被設定好的 function。

這是一支我沒用過也不太熟的 API，在撰文的當下其實我不會用 XD。先簡單整理幾個它常被用來處理什麼需求好了：

1. 無限滾動，滾到底部自動載入剩下的資訊
2. 圖片的 lazy load

爬了 w3c 的一些文，這支 API 好像是 Google 在 2016 年提出構想、在 2017 年提出草案的，目前已經有四個瀏覽器引擎實做了這支 API，分別是 Chromium、Edge、Firefox、Webkit，可以說主流的瀏覽器都支援了這支 API。
* [IntersectionObserver’s Coming into View  |  Web  |  Google Developers](https://developers.google.com/web/updates/2016/04/intersectionobserver)
* [w3c/IntersectionObserver: Intersection Observer](https://github.com/w3c/IntersectionObserver)
* [Intersection Observer](https://www.w3.org/TR/2017/WD-intersection-observer-20170914/)
* [IntersectionObserver/explainer.md at master · w3c/IntersectionObserver](https://github.com/w3c/IntersectionObserver/blob/master/explainer.md)


### IntersectionObserver 簡單說明

假設一個情境好了，即獵人看到鏡頭中出現獵物的話就開槍。那麼偽代碼如下
```js
// 1. 研發「開槍」技能樹
function 開槍(){} 
// 2. 招募一個獵人，跟他說看到畫面中有某個東西跑出來的話就開槍，什麼東西晚點跟你說
var 獵人 = new IntersectionObserver(開槍) 
// 3. 想抓的獵物是誰
var 獵物 = document.getElementById('兔兔')
// 4. 跟獵人說，看到指定的獵物就開槍
獵人.observe(獵物)
```

除了獵人(觀察者 observer)和獵物(目標 target) 外這兩個重要概念外，還有兩個重要概念：entry 和 option。不過這就等我之後再次遇到這個需求時再慢慢研究好了。有興趣的人可以參考相關資源。

```js
var 獵人 = new IntersectionObserver(function 開槍(entry) {
  const {
    time,
    rootBounds,
    boundingClientRect,
    intersectionRect,
    intersectionRatio,
    target
  } = entry
  // doSomething()
}, option = {
  threshold,
  root,
  rootMargin
}) 

var 獵物 = document.getElementById('兔兔')
獵人.observe(獵物)
```


## 相關資源
* [Intersection Observer - Web API 接口參考 | MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/IntersectionObserver)
* [IntersectionObserver：上篇 - 基本介紹及使用 - Front-End - Let's Write](https://letswrite.tw/intersection-oserver-basic/#3-true-false-callback)
* [IntersectionObserver：下篇-實際應用 lazyload、進場效果、無限捲動 - Front-End - Let's Write](https://letswrite.tw/intersection-oserver-demo/)
* [IntersectionObserver API 使用教程 - 阮一峰的網絡日志](https://www.ruanyifeng.com/blog/2016/11/intersectionobserver_api.html)
* [超好用的API之IntersectionObserver - 掘金](https://juejin.im/post/5d11ced1f265da1b7004b6f7)
* [Using the Intersection Observer API to Trigger Animations and Transitions](https://alligator.io/js/intersection-observer/)
* [[教學] 如何用 Intersection Observer API 實作 Infinite Scroll/Lazy Loading](https://shubo.io/intersection-observer-api/)
* [Timing element visibility with the Intersection Observer API - Web APIs | MDN](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API/Timing_element_visibility)
* [[教學] 如何用 Intersection Observer API 實作 Infinite Scroll/Lazy Loading](https://shubo.io/intersection-observer-api/)