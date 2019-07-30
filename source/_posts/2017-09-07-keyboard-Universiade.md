---
title: 鍵盤世大運的作弊js語法
date: 2017-09-07 22:15:35
categories: 編程
tags:
- JavaScript

---

既然開發團隊都在 console 裡面放彩蛋了，那用 console 來玩遊戲也是很理所當然的吧(?)

總之呢，這段語法的概念就是，每隔 100 毫秒，就會點擊按鈕一次。當然，把間隔秒數調整成更小，加速度到滿速的時間就更短了 ... 嘿嘿

本來想找看看有沒有其他的作弊方式，但我才粗學淺，不知道該怎麼找 orz

```js
// 世大運網頁遊戲腳本 by Wheat's FBlog
function KPNO1( ){　
    document.getElementById("run-button").click();
    setTimeout("KPNO1( )", 100);
}

KPNO1()
```

順便放在我的 gitbook 記錄裡面

* [世大運網頁遊戲腳本 · Front2End](https://ayugioh2003.gitbooks.io/front2end/content/shi-da-yun-wang-ye-you-xi-wai-gua.html)