---
title: 抓取臉書粉專的留言
thumbnail: 
date: 2019-02-22 00:55:04
categories: 編程
tags:
- Facebook
- JavaScript
---

剛剛看到一個讓人生氣的臉書貼文 [1]，於是想了解一下底下的留言會有什麼反應。由於在短短五個小時內，就湧入三千多則留言，數據量很多；再加上臉書的留言載入很爛，就更難閱讀了。想說用些方法讓自己比較好閱讀些

[1]: https://www.facebook.com/mykmt/photos/a.150164682972/10157105754217973/?type=3&theater

<!-- more -->


## 透過 Graph API Explorer 

本來是想用這個方式抓留言的……，但現在好像只有自己管理的粉專，才能透過 API 抓留言的樣子，所以這條路行不通。鑑於之後可能有機會用到，就還是找了一下資料

* [抓下 FB 粉絲團留言中的 email - Ron's blog](http://ronyeh.me/2017/12/04/%E7%94%A8python%E6%89%BE%E5%87%BAcsv%E4%B8%AD%E7%9A%84email/)


## 展開全部留言，在 console 中用語法抓留言

我目前只想得到這種方式了 orz。首先，可以透過別人寫好的 Bookmarkelet，將貼文底下的留言自動打開。我之前試過，電腦要用好一點的，不然瀏覽器會 lag

* [想要在 自動展開臉書留言 　把這個加入書籤列中幫你一鍵搞定 - 電腦王阿達](https://www.kocpc.com.tw/archives/145296)
* [[Web] 在瀏覽器增加展開所有 facebook 留言的按鈕 @ 小攻城師的戰場筆記：：痞客邦 ::](http://fannys23.pixnet.net/blog/post/43518713-%E5%B1%95%E9%96%8B%E6%89%80%E6%9C%89facebook%E7%95%99%E8%A8%80)
* [【外掛】一鍵展開所有留言 - Dcard Dcard板](https://www.dcard.tw/f/dcard/p/7852146)

接下來，就是在 console 裡面寫 JavaScript 來過濾資料。先附上剛剛試用的程式碼：

```javascript
// 每個留言都被放在 <li> 裡面，所以抓取整個留言區的每個 <li>
var list = document.querySelectorAll('._77bp>li') 
// 接著抓 <li> 裡面的 <span>，抓出裡面的文字，然後印到 console 上
list.forEach(item=>console.log( item.querySelector('span').innerText ))
```

大概是這樣吧。如果我後續要改良的話，可能會朝這幾個方向走

1. 把資料存成 object、array 形式，方便整理。Chrome 的 console 用 `copy()` 能直接把值放到剪貼簿，這樣就能方便存資料了
2. 改成 Nodejs 可以執行的寫法。流程可能是用 Chrome headless 進入網頁，自動展開留言，抓取留言存成 Json，再寫入檔案吧。不過我完全不確定是否可行就是了

附上一些未來可能對我有幫助的參考資料

* [[译] JavaScript 自动化爬虫入门指北（Chrome + Puppeteer + Node JS）：和 Headless Chrome 一起装逼一起飞 - 掘金](https://juejin.im/post/5a4e1038f265da3e591e1247)
* [Chrome Headless — Puppeteer 小妙用 – Michael Hsu – Medium](https://medium.com/@evenchange4/chrome-headless-puppeteer-%E5%B0%8F%E5%A6%99%E7%94%A8-9ac2c3b4e761)
* [Puppeteer: 更友好的 Headless Chrome Node API - 謙行 - 博客園](https://www.cnblogs.com/dolphinX/p/7715268.html)
