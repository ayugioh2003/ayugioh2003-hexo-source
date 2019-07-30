---
title: Google Sheet 的自訂函式
thumbnail: 
date: 2019-02-19 21:22:04
categories: 編程
tags:
- GoogleSheet
- JavaScript
- JSDoc
---

很久沒更新這個 Blog 了，但覺得應該要重新經營一下，就直接先在 Github 的網頁寫 md 了。之後應該會把過去文章備份起來，重新再建立 Blog 一次吧。

剛剛看到赤燭的包子在臉書上問說，Google Sheet 的某個語法要怎麼用，底下有人額外提到 Google Sheet 的自訂函數。一時好奇，就想說來研究一下好了。
* [王瀚宇 - 有人用過Google Sheet的Conditional Format Rules嘛？...](https://www.facebook.com/huw12313212/posts/2102607726482619)

<!-- more -->

看了一下 Google Sheet 自訂函數教學 [1]，還滿好懂的。先到 Google Sheet 控制菜單找到 `Tools > Script editor`，然後就可以在裡面寫自己想要的函式了。

[1]: https://developers.google.com/apps-script/guides/sheets/functions


例如，如果要把 cell 的數值加倍的話，就在頁面自訂一個 DOUBLE 函式：

![範例程式](https://i.imgur.com/juxyZqV.png)

然後回到 Google Sheet 介面，在細格中引用自訂的函式：

![範例sheet](https://i.imgur.com/STZ2o2Q.png)

這樣就大公告成了。BTW，Google App Script 好像支援用 JSDoc 語法來說明函式的功能。之前不曉得這可以做什麼用，但現在懂惹

* [Use JSDoc: Getting Started with JSDoc 3](http://usejsdoc.org/about-getting-started.html)
