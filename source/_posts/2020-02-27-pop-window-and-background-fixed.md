---
title: 在彈出視窗時隱藏背景滾軸
date: 2020-02-27 18:50:19
thumbnail:
categories: 前端開發
tags:
- w3HexSchool
- w3Hexschool-2020-challenge
- 接案
- 接案2019
- CSS
---

先前專案在開發移動版時，本來是用推移的方式展開 navbar 選單，後來客戶希望用覆蓋全畫面的方式來打開選單。

本來想說要不要用 Bootstrap 提供的現有工具解決。移動版 navbar 點擊後跳出的覆蓋視窗，其實概念類似於 BS 提供的 modal，即強制彈出一個新畫面，脫離原先瀏覽網頁內容的情境。
* [互動視窗 (Modal)・Bootstrap 4 繁體中文手冊 [六角學院譯]](https://bootstrap.hexschool.com/docs/4.0/components/modal/)

最後我還是想嘗試用 CSS 土法煉鋼的方式，將 pop window 展開到全畫面以達成需求。

結果出現了一個問題：pop window 覆蓋全畫面時，右邊滾軸竟然還在，而且可以被滾動


<!-- more -->

## 彈出覆蓋畫面時隱藏背景捲軸

後來發現解法滿簡單的。就是在 pop window 出來時，將 body 加上 `overflow: hidden`，把整個畫面的滾軸拿掉，這樣就會符合需求了。

<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="html,result" data-user="ayugioh2003" data-slug-hash="vYOeWKW" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="pop window, background overflow hidden">
  <span>See the Pen <a href="https://codepen.io/ayugioh2003/pen/vYOeWKW">
  pop window, background overflow hidden</a> by Chiu (<a href="https://codepen.io/ayugioh2003">@ayugioh2003</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>