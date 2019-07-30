---
title: 浮動排版與clearfix的建議
thumbnail: 
date: 2019-03-23 00:55:04
categories: 編程
tags:
- CSS
- float
- clearfix
---

前天在六角學院的不公開社團 [1] 看到六角校長洧杰丟了一個題目給大家思考 [2]，我猜應該是在練習浮動排版時，時常會看到的父元素高度塌陷吧。因此我以 clearfix 的角度去思考這個題目，下面的文字是我在該貼文底下的留言

[1]: https://www.facebook.com/groups/110635703123103/permalink/362891001230904/ (六角學院社團)
[2]: https://codepen.io/liao/pen/EMPWZd (思考題目)

<!-- more -->

---

以下是我目前程度會想給出的建議

1.把多餘的 code 修掉，能更聚焦。例如，css reset 可以用 codepen 內建的選項載入；CSS 中的 .footer、.end 等等樣式設定其實在這裡沒用到，也可以刪掉；HTML 中的 html、head 等標籤 codepen 會幫忙處理好，因此也可以刪掉

2.從 clearfix 這個命名可以看出，這些 code 應該是想練習如何利用 float 來排版，以及避免浮動元素的父元素的高度塌陷。因此我把 codpen 的標題改成「浮動排版修改」，方便日後回顧時能更容易回想起來

3.CSS 中我覺得有些設定會干擾到效果呈現，所以就先刪掉了。例如，.header 的 height: 150px 設定，會讓本來應該高度塌陷的 .header 繼續有高度，這樣就算設定成正確的 clearfix 用法，也看不出來成效，這樣就失去練習的用意了

4.清除 (閉合) 浮動的第一步與第二步，是要列出網頁中有哪些浮動元素，以及浮動元素的父元素是誰。從 CSS 中可看出，浮動元素有 .topmenu 與 .topmenu li，因此從 HTML 的結構中可找出，它們各自的父元素是 .header 以及 ul，代表我們需要對這兩個父元素進行一個清除浮動的動作

5.再來是第三步，設定 clear:both 來清除浮動。清除 (閉合) 浮動我目前學過的主要有兩種方法。第一個方法是，在最後一個浮動元素的後面，添增一個自帶 clear: both 設定的元素。以我的修改範本為例，需要對 .header 以及 ul 的最後一個子元素的後頭，添加 `<div class="clearfixOld"></div>` 元素。另外，也可以用 `<br clear=both>` 放在父元素內部的最後，一樣會有清除浮動的效果

6.清除 (閉合) 浮動的第二種方式是，利用偽元素會插入被設定元素的最後一個子元素後頭的原理，來進行清除浮動。以該範本為例，就是在 .header 和 ul 在兩個元素，新增 clearfix 這個 class，就能自動在最後插入一個帶有 clear:both 設定的子元素，以達成清除浮動的需求了

7.其他 margin、padding 的設定，就要再根據視覺效果進行微調了。我的建議先聚焦在 clearfix 的設定就好，避免超展開 (?)

(完)

https://codepen.io/ayugioh2003/pen/NJxjpB?editors=1100
