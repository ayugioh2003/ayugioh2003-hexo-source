---
title: 簡單的視差滾動
date: 2020-03-10 14:38:46
thumbnail: https://i.imgur.com/thSI12p.png
categories: 前端開發
tags:
- w3HexSchool
- w3Hexschool-2020-challenge
- 接案
- 接案2019
- JavaScript
- CSS
---

![視差滾動示意圖](https://i.imgur.com/thSI12p.png)

在專案開始前，覺得有可能會碰到視差滾動的需求，就先複習了一下。後來雖然有用到一下，但因為需求變更，後來在專案中就把視差滾動效果拿掉了。這邊記錄一下視差滾動的東西。

## 視差滾動是什麼、它的用處？

視差滾動就是，讓平面的疊加影像，產生出有層次的移動速率不同的感覺。以現實生活的情境為例，當我們坐在火車上看窗外時，會覺得遠方的景物移動的較慢，近方的景物移動的較快。

視差滾動有什麼好處呢？許多的網頁資訊，都是像貼紙一樣直接擺在畫面上。採用視差滾動效果後，除了會讓人有新鮮的感覺，有時也能突顯出背景與前景的差異。


## 在網頁實現視差滾動

前述提到，視差滾動原理其實就是讓背景和前景的移動速度不同。當時做研究時，大概整理出兩種用原生 CSS、JavaScript 做視差滾動的方式：


一、純 CSS 方案

要簡單快速的實現視差滾動效果，可以用這個純 CSS 方案嚐鮮。

在 CSS 中，有一個屬性是 `background-attachment`，這屬性用來設定，背景圖片的是要固定在 viewport （視圖，瀏覽器視窗畫面）上，還是背景圖片的 containing block （父層容器）上。

當裝著背景圖的容器元素添加了 `background-attachment: fixed;` 設定後，背景圖會被固定在 viewport 上。也就是說，當使用者滾動網頁時，背景的移動速度會是零，前景(網頁內容)的移動速度是一般的滾動速度，因此達到視差滾動的效果。

* [background-attachment - CSS | MDN](https://developer.mozilla.org/zh-TW/docs/Web/CSS/background-attachment)
* [簡單的視差滾動 - iT 邦幫忙：：一起幫忙解決難題，拯救 IT 人的一天](https://ithelp.ithome.com.tw/articles/10197613)
* [CSS沒有極限 - 意想不到的background-attachment | 卡斯伯 Blog - 前端，沒有極限](https://wcc723.github.io/css/2013/09/25/background-att/)


二、混合 JavaScript 方案

雖然前面提到的 CSS 方案可以實現簡單視差滾動效果，但當畫面由多個背景圖疊加，想產生多層次感的視差滾動時，純 CSS 方案就不夠用了。例如，有一個畫面由高山、矮山、人物組成。網頁設計師希望讓使用者滾動網頁時，看到遠景的高山移動很慢、中景的矮山移動稍快，近景的人物移動較快。

而原生 JavaScript 實現視差滾動的觀念是
1. 抓取需要在視差滾動時移動的圖片元素、並得知目前它們在網頁上 Y 軸方向的座標
2. 監測到使用者讓網頁滾動時，執行一些事情
  - 遠景圖片讓他移動距離增加少一點
  - 中景圖片移動距離普通
  - 近景圖片移動距離多一點

抓取元素在網頁上的座標有一些 JavaScript API 可以用
1. `getBoundingClientRect`、`getClientRects` 系列
2. `offsetTop`、`scrollTop`、`clientTop` 系列做運算

當圖片位置進入到瀏覽器視窗畫面中時，有這些 JavaScript API 能讓圖片開始移動。不過我只試過第一種，第二種還沒試過。第一種寫法雖比較簡單，但會消耗性能，因為每次使用者滾動時都會觸發這個函式。
1. `onScroll`
2. `IntersectionObserver`

其他好像還有不少種方式，但先前我研究比較通用的方式就是這兩種了。

## 相關資料
* [視差滾動研究 - HackMD](https://hackmd.io/8ss1-w5sQeyac50zFLUj4A?view)
* [ayugioh2003/parallax-scrolling-exercise: 視差滾動練習](https://github.com/ayugioh2003/parallax-scrolling-exercise)