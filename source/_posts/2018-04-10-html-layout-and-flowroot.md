---
title: 談網頁的佈局以及 display:flow-root 
thumbnail: /images/index.JPG
date: 2018-04-10 12:17:12
categories: 編程
tags:
---

## 前言

最近在學習網頁排版的時候，課程裡面使用 div 以及 float 來排版，而其實這種排版方式也還算是主流(吧)的一支。但我一直覺得這種排版方式有脫褲子放屁的感覺，很阿雜，因為需要清除浮動，才不會造成父元素的高度塌陷。(可能也有人這樣想吧，所以後來有了 flex 和 grid 排版方式 XD)

以下簡單介紹目前我知道的網頁佈局方式，之後再稍微談談 `display: flow-root` 這個比較新的東西

<!-- more -->

## 一、網頁佈局方式

我還記得大三的時候，跑去香妝系修網頁設計。當時使用的編輯器是 DreamWeaver，使用的佈局就是 table 了。害我後聽到 div 佈局的時候，花了很長一段時間去了解。但說實在的，我覺得 table 佈局比 div 佈局直覺多了。

就我的理解中，目前比較常被使用過的網頁佈局典範有這些

* table 佈局
* div 佈局
    * flow-root 佈局(等等會提到)
* flex 佈局
* grid 佈局

這些佈局典範，基本上都和 html 的元素屬性 display 有關。

在 w3.org 在 [CSS basic box model](https://www.w3.org/TR/css3-box/#block-level0) 公佈的資料裡，有提到很多 display 的屬性。display 好像就翻譯叫佈局吧？但為了不讓它跟 與視覺效果的網頁佈局 搞混，下文就沿用英文 display 指這個屬性。

### 1.1 table 佈局

table 佈局，可以透過 html 的 table 元素、或是把 `<div>` 設定成 `display: table` 達成。我的理解是，這種佈局就像是在 word 裡面拉表格的樣子差不多。拉完表格、固定好細格的位置後，只要把資料放入細格，在螢幕看到的畫面就是實際呈現的畫面(好繞口)。

但因為 table 無法方便的 RWD、table 有預設樣式對 css 不太友善的關係，後來網路佈局的主流就換成了 div 佈局。

```html
<table>
　<tr>
　<td> 第一欄 </td>
  <td> 第二欄 </td>
  <td> 第三欄 </td> 
　</tr>
</table>
```

### 1.2 div 佈局

div 佈局，就是用 div 來堆疊網頁上內容的一種佈局方式。因為 div 這個元素沒有什麼對視覺有干擾的預設樣式，就像是空白的容器一樣，所以很適合 <s>拿來蓋房子</s> 用來區隔性質不同的網頁內容。再加上 div 有 `display: block` 的預設值，而 block 元素可以包裹 block 與 inline 元素，所以比起 span 更適合拿來當磚塊來蓋房子了。

但，div 佈局有個問題是，需要清除浮動。不管是在 block 或是 inline 元素中，在預設的情況下，他們的子元素都會依照 normal flow 的方式，由左至右、由上而下的乖乖排隊。但因為 block 父元素可以包裹 block 子元素，而 block 具有佔據一行的特性，所以 block 子元素雖然一樣會由上往下乖乖排隊，但卻沒辦法有左右鄰居。為了讓 block 子元素有能跟其他元素並排，於是有人想到 `float` 屬性。

`float` 屬性，就相當於 word 裡面的文繞圖功能。當我設定圖片有 `float: left` 屬性時，圖片就會貼在 block 父元素的左側，而父元素之下的其他文字就會依照著 normal flow，貼著圖片依序排序去。因此，div 子元素可以有鄰居了！而且這些飄在 normal flow 之上的浮動 div 子元素，彼此也是可以當鄰居的。

但，好景不常，有一好沒兩好。這些浮起來的 div 子元素，因為沒有人拉它們回來，於是時常飄著飄著，就飄出父元素的視覺範圍了。這個現象叫做父元素的高度塌陷，height collapsing (還是叫 margin collapsing?)。為了解決這個現象，於是很多人開始討論該如何「清除浮動」，也就是 clearfix。

#### 1.2.1 ClearFix

<p data-height="265" data-theme-id="0" data-slug-hash="xWMgee" data-default-tab="result" data-user="ayugioh2003" data-embed-version="2" data-pen-title="height collapsing" class="codepen">See the Pen <a href="https://codepen.io/ayugioh2003/pen/xWMgee/">height collapsing</a> by Chiu (<a href="https://codepen.io/ayugioh2003">@ayugioh2003</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

橘色的 div 是藍色和紅色 div 的父元素，本來應該是要將它們包起來的。但因為紅色藍色 div 有 `float: left` 的屬性，所以脫離了 normal flow。橘色 div 的高度本來是由它的最高的子元素所決定，但因為紅藍 div 離家出走了，所以橘色 div 的高度就沒辦法像自己的小孩那麼高（有種心酸的感覺）。

為了讓橘色 div 能包住紅藍 div 子元素，就需要「清除浮動」了。簡單的理解是，在紅色 div 後頭擺上一個不會逃家的小孩，這樣橘色 div 就可以抓到所有小孩了(咦)。

<p data-height="265" data-theme-id="0" data-slug-hash="oqmZgg" data-default-tab="css,result" data-user="ayugioh2003" data-embed-version="2" data-pen-title=".clearfix" class="codepen">See the Pen <a href="https://codepen.io/ayugioh2003/pen/oqmZgg/">.clearfix</a> by Chiu (<a href="https://codepen.io/ayugioh2003">@ayugioh2003</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

簡單的說明

* `.content:after` 是一種偽元素，能在橘色 div 後面產生一個虛的元素，並設定 css 屬性
* 要讓 `.content:after` 出現在網頁上，必須要針對 `content` 屬性設定值。就算是空白也沒關係。因為我們只是想讓紅色 div 子元素後還有個子元素，能用來清除浮動，於是 `content` 只要空白就好
* 這部份我沒有理解得很清楚。偽元素預設是 `display: inline`，為了讓它有自己的高度，需要設定成 `display: block` 或是 `display: table`
* 最後就是讓它背負「清除浮動」的任務啦 `clear: both`



以上就是我對 div 排版的大概理解。在 [那些年我們一起清除過的浮動](http://www.iyunlu.com/view/css-xhtml/55.html) 這篇文章中，有提到更多「清除浮動」的方式，他甚至認為「清除浮動」的原理主要可分成兩類

* 其一，通過在浮動元素的末尾添加一個空元素，設置 clear：both 屬性，after 僞元素其實也是通過 content 在元素的後面生成了内容爲一個點的塊級元素
* 其二，通過設置父元素 overflow 或者 display：table 屬性來閉合浮動

此外，在 2017 年，chrome 和 firefox 支援了一個新的 display 屬性：`flow-root`，也能達成類似 clearfix 的效果。這個方法和上文提到的第二種原理有相關。待會會在後面說明。


(另外，div 也有用 `display: inline-block` 排版方式，但 inline-block 有一些特別的 <s>feature</s> bug，所以還是不少人寧願用 block 搭配 float 來排版)

### 1.3 flex 佈局

還沒學，稍微看過教學，覺得厲害。聽說跟 div 佈局概念比較接近

* [Web 布局新系統：CSS Grid,Flexbox 和 Box Alignment_CSS3, CSS3 Grid Layout, Grid, Layout 教程_w3cplus](https://www.w3cplus.com/css/css-grids-flexbox-and-box-alignment-our-new-system-for-web-layout.html)

### 1.4 gird 佈局

還沒學，覺得厲害。聽說跟 table 佈局概念比較接近

* [Web 布局新系統：CSS Grid,Flexbox 和 Box Alignment_CSS3, CSS3 Grid Layout, Grid, Layout 教程_w3cplus](https://www.w3cplus.com/css/css-grids-flexbox-and-box-alignment-our-new-system-for-web-layout.html)

---

## 二、閉合浮動與 display: flow-root

在 [那些年我們一起清除過的浮動](http://www.iyunlu.com/view/css-xhtml/55.html)作者提到，其實「清除浮動」的說法並不是很精準，我們要的其實不只是「清除浮動」，而是要讓父元素高度不會塌陷，不會影響到父元素的後面鄰居。因此以「閉合浮動」的說法會比較精確。原理二就是使用閉合浮動的概念。

那如何達到閉合浮動，以及它是什麼原理呢？該文提到，在 CSS2.1 規範中，有一個新的概念，叫 BFC ( [Block formatting contexts，塊級格式化上下文](https://www.w3.org/TR/CSS21/visuren.html#block-formatting))。

我們可以把 BFC 想像成是一個控制欲很強的父元素。BFC 的小孩元素，永遠只能待在這個家的空間裡面，無法接觸到 BFC 之外的元素。因此，就能達到類似清除浮動的效果，但它其實是閉合浮動。

在比較久之前，只有符合特殊條件的元素，才能成為 BNC 這個比較特別的 block (inline-block)。在 [前端精選文摘：BFC 神奇背後的原理](https://www.cnblogs.com/lhb25/p/inside-block-formatting-ontext.html) 一文提到的條件有

* 根元素
* float 屬性不爲 none
* position 爲 absolute 或 fixed
* display 爲 inline-block, table-cell, 
* table-caption, flex, inline-flex
* overflow 不爲 visible

所以符合這些條件的父元素，就算沒有清除浮動，本身也自帶了閉合浮動的特殊效果，這個父元素的高度也就不會塌陷了。

有些 clearfix 的方案，會設定父元素 `overflow: hidden`，就是把父元素轉換成了 BNC，讓子元素只能乖乖待在家裡，無法逃出父元素的框框(聽起來好悲哀)。

### 2.1 display: flow-root

`flow-root` 就像是 `block`、`inline`這些值一樣，是 `display` 屬性可以選擇的值。作用就是，能直接把被設定成 `display: flow-root` 的元素，直接轉變成 BNF 喔！這樣應該能套用在父元素上，閉合浮動，避免父元素的高度塌陷了。

`flow-root` 是在 css3 中才被加入的，好像很長一段時間都沒被實作過。但在 2017 年四月釋出的 [Chrome 58](https://developers.google.com/web/updates/2017/04/nic58) 和 [Firefox 53](https://hacks.mozilla.org/2017/04/firefox-53-quantum-compositor-compact-themes-css-masks-and-more/) 都相繼支援 `flow-root` 功能啦 ~ 不過根據 [can i use](https://caniuse.com/#search=flow-root)，到 2018 年的今天，好像也只有 Chrome 和 Firefox 有支援而已。

總之就是，要閉合浮動的話，只要在父元素設定 `display: flow-root` 就好了。而還沒支援的瀏覽器上，可以使用 `@supports`，拿舊的 clearfix 方案出來檔

demo1

```css
.left,
.right {
    width: 50%;
}

.left {
    float: left;
    margin-bottom: 2em;
}

.right {
    float: right;
}

.wrapper::after {
    content: '';
    display: block;
    clear: both;
}

@supports (display: flow-root) {
    .wrapper {
        display: flow-root;
    }

    .wrapper::after {
        content: none;  
    }
}
```

demo2
```css
.wrapper {
    display: flow-root;
}

@supports not (display: flow-root) {
    .wrapper::after {
        content: '';
        display: block;
        clear: both;
    }
}
```

附上 flow-root 的參考資料

* [解決 float:left 走樣問題更簡單　使用 CSS 新屬性 display: flow-root - UNWIRE.PRO](https://unwire.pro/2017/04/29/css-display-flow-root/marketing/)
* [Using flow-root today – Anselm Hannemann](https://helloanselm.com/2017/flow-root-supports/)
* [css 技巧之：css 新屬性 display:flow-root 介紹。 - Div.IO](https://div.io/topic/1973)


---

以上是我的整理

因能力有限有誤或不清楚的地方，請多多指教與指正 orz

(像 Margin collapsing 和 height collapsing 我就分不太清楚差別；好像沒有後面用法的樣子)


附上主要參考資料

* [那些年我們一起清除過的浮動 - 層疊之美](http://www.iyunlu.com/view/css-xhtml/55.html)
* [flow-root_flow-root 教程_w3cplus](https://www.w3cplus.com/css3/display-flow-root.html)
* [The very latest clearfix reloaded](http://cssmojo.com/the-very-latest-clearfix-reloaded/)
