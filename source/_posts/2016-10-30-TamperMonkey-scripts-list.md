---
title: 目前安裝的 TamperMonkey 腳本
date: 2016-10-30 01:43:28
categories: 編程
tags:
- TamperMonkey
- Chrome
- 整理
---

![來源:https://git.io/vX4D3](/images/20161030TamperMonkey.png)

# 前言

自從對 JavaScript 稍微有了解後，就斷斷續續的在學習語法。某日碰見 TamperMonkey 這個套件，就瞬間一見傾心了 XD 以下記錄有在使用的 js 腳本

<!-- more -->

---

<!-- toc -->

- [前言](#前言)
- [腳本整理](#腳本整理)
	- [Anti-Adblock Killer｜擋偵測廣告](#anti-adblock-killer擋偵測廣告)
	- [Facebook HD Video Downloader｜下載臉書影片](#facebook-hd-video-downloader下載臉書影片)
	- [Highlight Every Code｜高亮網頁上選取的代碼](#highlight-every-code高亮網頁上選取的代碼)
	- [Switch Traditional Chinese and Simple｜簡繁互換](#switch-traditional-chinese-and-simple簡繁互換)
	- [Youtube +｜魔改youtube](#youtube-魔改youtube)
	- [Youtube Best Video Downloader 2｜下載Youtube](#youtube-best-video-downloader-2下載youtube)
	- [為什麼你們就是不能加個空格呢？｜中英之間加空格](#為什麼你們就是不能加個空格呢中英之間加空格)
- [自己寫的腳本](#自己寫的腳本)
	- [FB分享引文](#fb分享引文)
		- [FB分享引文 fb-quote](#fb分享引文-fb-quote)
		- [FB分享引文 fb-root](#fb分享引文-fb-root)
- [參考連結](#參考連結)

<!-- tocstop -->

---

# 腳本整理

因為腳本沒有很多，所以就不分類介紹惹

## Anti-Adblock Killer｜擋偵測廣告

- 連結：[reek/anti-adblock-killer: Anti-Adblock Killer helps you keep your Ad-Blocker active, when you visit a website and it asks you to disable.](https://github.com/reek/anti-adblock-killer/)

至今還不知道該怎麼使用它 ...（原本用途是，繞開那些能偵測到 安裝者有裝擋廣告套件的機制），可能再過一陣子就把它刪了

## Facebook HD Video Downloader｜下載臉書影片

- 連結：[Facebook HD Video Downloader](https://greasyfork.org/zh-TW/scripts/3481-facebook-hd-video-downloader)

可以下載 Facebook 上的影片。雖然平常用不到，但還是下載起來備份用。


## Highlight Every Code｜高亮網頁上選取的代碼

- 連結：[代碼片斷高亮](https://greasyfork.org/zh-TW/scripts/24150-highlight-every-code)

這腳本超厲害的，按 `ctrl + 反白`，就能排列、高亮被圈選到的程式碼，省去一些整理程式碼時間。

## Switch Traditional Chinese and Simple｜簡繁互換

- 連結：[繁簡自由切換](https://greasyfork.org/zh-TW/scripts/24300-switch-traditional-chinese-and-simplified-chinese)

按 `F8` 能切換簡轉繁或繁轉簡。預設會自動轉繁體

## Youtube +｜魔改youtube

* 連結：[YouTube +](https://greasyfork.org/zh-TW/scripts/9932-youtube)

這腳本也猛猛的，把 Youtube 改造成我快不認識了 XD

- Play your videos in a pop-out window
- Turn off 60fps
- Navigate through videos frame by frame (No longer necessary, YouTube already has it)
- Allow ads only in videos from your subscribed channels
- Blacklist entire channels from your suggestions and search results
- Make the player fill the entire browser with the Fullbrowser mode feature
- Player always visible where you want while reading the comments
- Play your most recent subscriptions in a playlist
- Reverse any playlist
- Control any playlist autoplay
- Take video screenshots and save them
- View and save the video thumbnail like old times
- Bring back the total number of videos uploaded by the creator
- Use the relative video post time to know quickly how old the video is
- and many more!

## Youtube Best Video Downloader 2｜下載Youtube

- 連結：[Youtube Best Video Downloader 2](https://greasyfork.org/zh-TW/scripts/19592-youtube-best-video-downloader-2)

顧名思義，這是可以下載 Youtube 影片的腳本

## 為什麼你們就是不能加個空格呢？｜中英之間加空格

- 連結：[為什麼你們就是不能加個空格呢？](https://greasyfork.org/zh-TW/scripts/2185-%E7%82%BA%E4%BB%80%E9%BA%BC%E4%BD%A0%E5%80%91%E5%B0%B1%E6%98%AF%E4%B8%8D%E8%83%BD%E5%8A%A0%E5%80%8B%E7%A9%BA%E6%A0%BC%E5%91%A2#)

這腳本也很厲害啊 ~ 能在中文和英文之間插入空白，提供文章的可讀性。之前裝過 Chrome 套件的版本，看到有腳本版的就開心的把之前的套件給移除了

---

# 自己寫的腳本

還不穩定 orz

## FB分享引文

2016年04月左右，臉書出了一個功能：分享引文。只要在有開啟此功能的網頁中反白選取文字，就會跳出「分享到臉書」的按鈕。點擊按鈕，跳出來的分享視窗就會多引用了剛剛反白選取的文字。

因為我很想讓自己分享的文章都能引用上面的文字，但又不是每個網頁都有此功能，我就自己想辦法自己土砲一下 js 語法。此功能的介紹可參考這裡

* [Facebook Quote Plugin 臉書選取文字後自動跳出「分享引文」外掛功能設定教學](https://free.com.tw/facebook-quote-plugin/)

簡單的說，就是在想開啟分享引文功能的網頁上，放上以下程式碼

```js
// 程式碼一
<div id="fb-root"></div>
<script>(function(d, s, id) {
var js, fjs = d.getElementsByTagName(s)[0];
if (d.getElementById(id)) return;
js = d.createElement(s); js.id = id;
js.src = "//connect.facebook.net/zh_TW/sdk.js#xfbml=1&version=v2.6";
fjs.parentNode.insertBefore(js, fjs);
}(document, 'script', 'facebook-jssdk'));</script>
```

以及

```js
// 程式碼二
<div class="fb-quote"></div>
```

參考這兩段 Facebook SDK 程式馬後，以下是我修改的能放到 TamperMonkey 的兩段語法。因為能力不足的關係，這兩個語法要拆開來使用比較適合，詳情在後文說明。

### FB分享引文 fb-quote

在有些網頁中，如果它已經安裝臉書的按讚分享工具的話，那可能也已經安裝 `程式碼一` 的片段了。如此，只要再添加 `程式碼二` 就好。`程式碼二` 的目的是在 html 中加入 `<div class="fb-quote"></div>` 這個帶有 `fb-quote` class 的 div。

```js
// 程式碼三
// ==UserScript==
// @name         FB分享引文 fb-quote
// @namespace    https://ayugioh2003.github.io/
// @version      0.1
// @description  try to take over the world!
// @include      *
//
// @homepage     https://ayugioh2003.github.io/
// @author       ChiuCW
// @grant        none
// ==/UserScript==
// https://free.com.tw/facebook-quote-plugin/

var newHTML = document.createElement('div');
// newHTML.innerHTML='<div class="fb-quote">second</div>';
newHTML.setAttribute("class","fb-quote");
document.body.appendChild(newHTML);

```

### FB分享引文 fb-root

如果想分享引文的網頁沒有安裝 Facebook SDK 的話，就要載入 SDK 才行。添加以下腳本就能夠有分享引文的功能。但要注意的是，載入此腳本後，網頁會一直在 loading ... 速度會變慢。但如果在網頁載入後馬上關掉此腳本的話，仍然能有分享引文的功能。

```js
// 程式碼四
// ==UserScript==
// @name         FB分享引文 fb-root
// @namespace    https://ayugioh2003.github.io/
// @version      0.1
// @description  try to take over the world!
// @include      *
//
// @homepage     https://ayugioh2003.github.io/
// @author       ChiwCW
// @grant        none
// ==/UserScript==
// https://free.com.tw/facebook-quote-plugin/

var newHTML2 = document.createElement('div');
// newHTML2.innerHTML='<div class="fb-quote">second</div>';
newHTML2.setAttribute("id","fb-root");
document.body.appendChild(newHTML2);

(function(d, s, id) {
  var js, fjs = d.getElementsByTagName(s)[0];
  if (d.getElementById(id)) return;
  js = d.createElement(s);
  js.id = id;
  js.src = "//connect.facebook.net/zh_TW/sdk.js#xfbml=1&version=v2.6";
  fjs.parentNode.insertBefore(js, fjs);
}(document, 'script', 'facebook-jssdk'));
```

---

# 參考連結

- 暫無
