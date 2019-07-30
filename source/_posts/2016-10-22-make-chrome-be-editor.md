---
title: 讓chrome變成所見即所得編輯器
date: 2016-10-22 23:08:14
categories: 編程
tags:
  - JavaScript
  - Html
---

![來源：http://www.pc3mag.com/google-chrome-stop-flash/](/images/chrome.jpg)


剛剛看到一個能直接在 chrome 更改網頁內容的方式，就簡單紀錄一下

<!-- more -->

到 Chrome 的開發者控制台（快捷鍵是 `F12`），打入以下程式碼

``` html
document.body.contentEditable=true
```

就能直接編輯網頁內容了～
