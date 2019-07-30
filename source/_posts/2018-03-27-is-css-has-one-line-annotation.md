---
title: CSS 有單行註解這種東西嗎
thumbnail: /images/index.JPG
date: 2018-03-27 15:47:50
categories: 編程
tags:
- CSS
---

最近在重新學習前端的基礎知識。跟著影片做中學的時候，突然想在 CSS 裡記錄想法，就跑去找 CSS 的註解方式。看到有文章寫 CSS 有單行註解 `//` 的時候，還很高興的使用了好幾天。

後來才發現，奇怪，怎麼預覽畫面跟想像中的不一樣，後來發現 CSS 似乎沒有單行註解，只有多行註解 `/***/`？

在搜尋後發現，其實好像真的沒這個規範，但很多開發者有一直討論過這件事情，VScode 裡也沒有支援這種註解方式。

BTW，之所以不支援 `//` 註解，好像是因為在壓縮程式碼的時候，有這種註解方式的話，會讓後面的屬性失效。但其實，我在 VScode 裡試驗過，只要在後面加個逗號 `//;` 就不會有影響了。

<!-- more -->


---

參考資料

* [[問題] css 的單行註解是不是有兼容問題？ - 看板 Web_Design - 批踢踢實業坊](https://www.ptt.cc/bbs/Web_Design/M.1456285299.A.E04.html)
* [CSS //- 註解的可行性研究 from Kang-Hao (Kenny) Lu on 2012-09-05 (public-html-ig-zh@w3.org from September 2012)](https://lists.w3.org/Archives/Public/public-html-ig-zh/2012Sep/0000.html)