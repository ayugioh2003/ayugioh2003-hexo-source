---
title: CSS 的文字抹除效果
date: 2020-03-05 19:19:54
thumbnail:
categories: 前端開發
tags:
- w3HexSchool
- w3Hexschool-2020-challenge
- 接案
- 接案2019
- CSS
---

在接專案時遇到了不少動畫的需求，其中一個比較抽象，是關於文字出現時的動畫效果。我用兩種方式比喻。（一）就像是打字時文字慢慢出現，但不是突然地，而是平滑地由左往右浮現（二）就像是拿橡皮擦由右往左擦時文字消失，然後把這段影像往回播放的樣子

<!-- more -->

## 用 CSS 產生文字擦除效果

若只是單純的將文字逐步出現的話是相對簡單的，只要將文字元素的母元素套上 `overflow: hidden`，配合 css animation 改變文字元素的母元素的寬度就好。這是類似效果的範例：
* [Edit fiddle - JSFiddle - Code Playground](http://jsfiddle.net/4srtxofg/)

不過當時我看到的需求說「我想要有一點霧霧的感覺」。一時覺得不曉得該怎麼處理 QQ 後來 google 很久後，看到有人做出很相似的效果，就參考了它的語法。相較於前面 `overflow` 的掩蓋住溢出的文字與動態改變寬度，後一種則是則是用了 `mask` 系列的 CSS 屬性。放上範例

<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="css,result" data-user="ayugioh2003" data-slug-hash="oNXGoMp" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="text-erasing-reverse">
  <span>See the Pen <a href="https://codepen.io/ayugioh2003/pen/oNXGoMp">
  text-erasing-reverse</a> by Chiu (<a href="https://codepen.io/ayugioh2003">@ayugioh2003</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

CSS Masking 真的是很迷的屬性，查了一下 MDN 似乎是跟遮罩相關的屬性，規範在 CSS Masking Module Level 1 中。要不是為了這個文字抹除效果，我大概不會發現這個屬性 orz
* [CSS Masking - CSS: Cascading Style Sheets | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Masking)

## 參考資料
* https://medium.com/@polymermallard/pure-css-wiping-gradient-text-reveal-1bbddc2aeb54
* https://developer.mozilla.org/en-US/docs/Web/CSS/mask-position
* https://www.zhangxinxu.com/wordpress/2017/11/css-css3-mask-masks/
* https://cloud.tencent.com/developer/section/1072181
* https://stackoverflow.com/questions/39608618/linear-wipe-text-effect-using-css-or-css3-animate/39608663