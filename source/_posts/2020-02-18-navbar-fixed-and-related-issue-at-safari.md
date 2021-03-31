---
title: 讓 navbar 置頂、隨滾動變化樣式、並探討與 Safari 相關的跨平台議題
date: 2020-02-18 11:29:11
thumbnail: https://i.imgur.com/VKailFS.gif
categories: 前端開發
tags:
- w3HexSchool
- w3Hexschool-2020-challenge
- 接案
- 接案2019
---

![navbar 置頂與滾動變化效果示意圖](https://i.imgur.com/VKailFS.gif)
> 類似效果的示意圖

## 前言

在專案開發期間，有要求網站的上方要有 navbar。不過需求有更改過幾次：一開始是會隨著瀏覽器捲動而消失，後來要求下滾時消失上滾時出現，最後則改成 navbar 在頂端時背景透明、下滾後背景白色。

除了置頂、偵測滾動外，在這個需求也遇上了跨平台問題（通常都是跟 Safari 相關 QQ）。偵測滾動之後的再獨立一篇出來，這邊先談 navbar 置頂與跨平台的問題。

<!-- more -->

## navbar 置頂方式

將 navbar 置頂其實不難，在 CSS 學習中算是基礎的應用。主要就是透過 `position` 屬性，把值設定成 `fixed`，讓元素絕對定位在畫面上。但搭配一些動畫效果後，發現在 Safari 上有時會出現問題 QQ。

* [position - CSS（層疊樣式表） | MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position)

```css
.navbar {
  position: fixed;
  /* top: 0; */
}
```

## Safari 相關問題與跨平台除錯

因為我是在 Windows 平台開發，我本身沒有 Mac 或 iPhone 等裝置，所以跨平台問題通常是 PM 幫忙看。當時遇到不少問題，都是 PM 先描述或螢幕錄影給我看，我再試圖通靈改動程式碼，上線後再請 PM 幫我查看。整個測試過程滿辛苦的 QQ。當時情況好像是，原本 navbar 上滾回頂端時預期會是背景透明，但在 Safari 操作時背景卻是白色。當時評估是 `position: fixed` 在 Safari 上有些奇怪的 issue。

回到如何跨平台除錯。當時遇到跨平台問題時，我會先在網路上查詢相關議題，像是 Google、[Can I use](https://caniuse.com/)、Stack Overflow。這時就會考驗拆解問題與下關鍵字的能力。以我當時狀況為例，我印象有以「fixed」、「position」、「navbar」、「Safari」、「iOS」等關鍵字做排列組合去搜尋。caniuse 也滿好用的，除了列出瀏覽器對某個 CSS 屬性的支援程度外，也有幫忙收集一些已知的 issues，對跨平台 issue 除錯時的幫助很大。

我現在已經有點忘記怎麼解決的了 orz。好像是 PM 繞過被設定 fixed 的元素，把動畫效果做在其他元素上，避免 fixed 在 Safari 上的奇怪問題。以下附上一些當時參考的資料：

> 橡皮筋效果
  * [iOS safari 如何阻止「橡皮筋效果」？ - GetIt01](https://www.getit01.com/p20180115822256539/)
  * [阻止移动端浏览器下拉橡皮筋效果（下拉滚动露底） - 简书](https://www.jianshu.com/p/dc6c2a7744fd)
  * [iOS safari 如何阻止“橡皮筋效果”？ - 知乎](https://www.zhihu.com/question/22256539)
  * [前端小學堂｜禁止行動裝置瀏覽器的橡皮筋效果 - Anna.Hsaio｜前端開發記 - Medium](https://medium.com/anna-hsaio-前端開發記/前端小學堂-禁止行動裝置瀏覽器的橡皮筋效果-4b9f484c579e)

> 在 position: fixed 元素上添加能啟動 GPU 渲染的 CSS 屬性
* [Revisions to position: fixed doesn't work on iPad and iPhone - Stack Overflow](https://stackoverflow.com/posts/49264494/revisions)
* [Using Chrome DevTools to profile the jsconf.eu site - YouTube](https://www.youtube.com/watch?v=QU1JAW5LRKU)
* [Fix scrolling performance with CSS will-change property – Four Kitchens](https://www.fourkitchens.com/blog/article/fix-scrolling-performance-css-will-change-property/)
```css
.fixed-position-on-mobile {
  position: fixed;
  transform: translate3d(0,0,0);
}
```

設定 overflow、orerflow-scrolling 屬性。不確定要設在 body 還是 fixed 元素身上 (以專案來看，應該是加在 html, body 上)
* https://stackoverflow.com/a/10317817
* [Mobile Safari (Whyyyy?!) - Engineering Blog](https://www.eventbrite.com/engineering/mobile-safari-why/)
* [html - Buttons aligned to bottom of page conflict with mobile Safari's menu bar - Stack Overflow](https://stackoverflow.com/questions/23657943/buttons-aligned-to-bottom-of-page-conflict-with-mobile-safaris-menu-bar/)
* [Issues with position fixed & scrolling on iOS](https://remysharp.com/2012/05/24/issues-with-position-fixed-scrolling-on-ios/)
* [Momentum Scrolling on iOS Overflow Elements | CSS-Tricks](https://css-tricks.com/snippets/css/momentum-scrolling-on-ios-overflow-elements/?source=post_page-----1efacea28611----------------------)
```css
overflow:hidden;
-webkit-overflow-scrolling:touch;
```

> 各種方案避免 ios 果凍效果
* [javascript - Prevent iOS bounce without disabling scroll ability - Stack Overflow](https://stackoverflow.com/questions/29894997/prevent-ios-bounce-without-disabling-scroll-ability)
* [lazd/iNoBounce: Stop your iOS webapp from bouncing around when scrolling](https://github.com/lazd/iNoBounce)
* [用”-webkit-overflow-scrolling: touch”讓你的mobile web application支援momentum-based scrolling](https://medium.com/@littleDog/%E7%94%A8-webkit-overflow-scrolling-touch-%E8%AE%93%E4%BD%A0%E7%9A%84mobile-web-application%E6%94%AF%E6%8F%B4momentum-based-scrolling-1efacea28611)


## 小結

當時查了一些資料後，覺得 Safari 對「畫面定位」相關的 CSS 屬性感覺支援度沒有很好，像我在使用 `position: fixed` 和 `background-position: fixed` 時都有遇到問題。之後在做網頁時應該會特別避開這點，免得到時又要除錯很久找不出問題來 QQ。