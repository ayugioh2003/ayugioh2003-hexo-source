---
title: 練習做一個網購商品列表首頁
thumbnail: /images/index.JPG
date: 2018-04-12 22:20:04
categories: 編程
tags:
- Html
- CSS
---

本來練習的課程只做了一個商品主題式列表，但因為看到很多人都做了有表頭表尾的網購首頁出來，想說不能輸，就越做越多了 XD

以下整理幾個用到的東西

<!-- more -->

## 主題式列表

其實就是 ul li 的結構而已

## 在商品列表左上方放折扣訊息

這可以用 `position: absolute` 做到
首先放了一個紅色三角形上去

* [【轉】純 CSS 畫的基本圖形（矩形、圓形、三角形、多邊形、愛心、八卦等），NB 麽 - 草根程序猿 - 博客園](http://www.cnblogs.com/jscode/archive/2012/10/19/2730905.html)
* [用 CSS 設計出三角形圖案 - Wibibi](http://www.wibibi.com/info.php?tid=%E7%94%A8_CSS_%E8%A8%AD%E8%A8%88%E5%87%BA%E4%B8%89%E8%A7%92%E5%BD%A2%E5%9C%96%E6%A1%88)
* [CSS 三角形產生器](http://apps.eky.hk/css-triangle-generator/zh-hant)
* [30 天掌握 Sass 語法 - (27) 使用 @if 提升 @Mixin 靈活度，以 CSS 圖形化為例 - iT 邦幫忙:: 一起幫忙解決難題，拯救 IT 人的一天](https://ithelp.ithome.com.tw/articles/10136641)

```css
.bg {
  position: absolute;
/*   top: 0;
  left: 0; */
  width: 0;
  height: 0;
  border-top: 70px solid red;
  border-right: 70px solid transparent;
}

/* 別人的寫法 */
.thick-border{
  height: 0;
  width: 0;
  border-width: 0 0 60px 60px;
  border-color: transparent rgba(255, 0, 0, 0.9);
  border-style: solid;
  position: absolute;
}

```


之後再把文字擺上去，順便用了 `transform: rotate(-45deg);` 讓文字旋轉

```css
.productList li .sale {
  position: absolute;
  top: 15px;
  left: 9px;
/*   background-color: red; */
  color: #fff;
/*   padding: 8px; */
  transform: rotate(-45deg);
/*   text-align: center; */
}
```

## 回到最上頁

先用了 `position: fixed` 讓按鈕固定在右下角
再配合平滑滾動，讓畫面看起來比較和緩

```css
html {
  scroll-behavior: smooth;
  background-color: #eee;
}
```

按鈕也有用 `border-radius: 5px;` 來產生圓角


## 其他

好像沒什麼了。剩下大概就
- 大量使用 hover 製造互動效果
- 使用 `display: flow-root` 閉合浮動

之後也要花時間學習怎麼配色，不然我一直都用粉紅色和淡藍色 XD

附上試作的網頁

<p data-height="480" data-theme-id="0" data-slug-hash="dmLREa" data-default-tab="result" data-user="ayugioh2003" data-embed-version="2" data-pen-title="利用絕對定位設計左上角圖案" class="codepen">See the Pen <a href="https://codepen.io/ayugioh2003/pen/dmLREa/">利用絕對定位設計左上角圖案</a> by Chiu (<a href="https://codepen.io/ayugioh2003">@ayugioh2003</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>