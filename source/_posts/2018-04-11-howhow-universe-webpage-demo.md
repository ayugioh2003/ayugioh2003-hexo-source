---
title: How 哥宇宙宣傳網頁試作
thumbnail: /images/index.JPG
date: 2018-04-11 00:05:37
categories: 編程
tags:
- Html
- CSS
- YouTube
---

因為太喜歡 Howhow 了，我課程作業想不到題材，就拿來宣傳 How 哥宇宙好了 XD
以下記錄頁內錨點、Youtube Player API 的部份

<!-- more -->

先放上作品 (有彩蛋，記得開耳機 XD)


<p data-height="430" data-theme-id="0" data-slug-hash="bvzxKM" data-default-tab="result" data-user="ayugioh2003" data-embed-version="2" data-pen-title="HW4-32  設計三欄版型_ytapi| Hexschool HTML, CSS" class="codepen">See the Pen <a href="https://codepen.io/ayugioh2003/pen/bvzxKM/">HW4-32  設計三欄版型_ytapi| Hexschool HTML, CSS</a> by Chiu (<a href="https://codepen.io/ayugioh2003">@ayugioh2003</a>) on <a href="https://codepen.io">CodePen</a>.</p>

---

## 一、設定頁內錨點與滾動效果

其實設定頁內錨點還滿簡單的，只要 a 的連結和 id 的名字一樣就好。這樣點下去，頁面就會自動跳到 div 那裡。

```html
<div class="header">
    <h1>How哥宇宙</h1>
    <ul class="menu">
    <li><a href="#intro">關於How哥宇宙</a></li>
    <li><a href="#tree">How哥宇宙分支</a></li>
    <li><a href="#review">別人的評價</a></li>
    <li><a onclick="playAll()">彩蛋</a></li>
    </ul>
</div>
<div class="intro" id="intro">
<div class="content" id="tree">
<div class="review" id="review">
```

至於產生滾動效果的話，只要加入以下 css 就好。不過目前(2018.04)貌似只有 Firefox 和 Chrome 兩個瀏覽器有支援而已 orz

```css
html {
  scroll-behavior: smooth;
}
```

參考資料

* [神奇的 html 錨點，讓你的網頁在內部自由的跳轉 - 每日頭條](https://kknews.cc/zh-tw/tech/ena88ry.html)
* [css3 - CSS: pure CSS scroll animation - Stack Overflow](https://stackoverflow.com/questions/17631417/css-pure-css-scroll-animation)
* [Can I use... Support tables for HTML5, CSS3, etc](https://caniuse.com/#search=scroll-behavior)


---


## 二、Youtube Player API

Howhow 在三月多的時候，發佈了一個影片。因為內嵌一個品質不錯、但又無腦的、叫做 How 哥宇宙的 MV。後來就很多人開始二創，用自己會的樂器來接龍演奏樂器。先附上原始影片和始作俑者


<iframe width="560" height="315" src="https://www.youtube.com/embed/DSYLan4xT8s" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube.com/embed/9ss0iRp9RGM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>


總之呢，我的目標就是在網頁上放一個按鈕，然後我只要按這個按鈕，就能控制所有被內嵌在網頁上的 Youtube iframe 的播放。然後我就一直撞牆了，冏。

在查詢的過程中，發現要操作 iframe 好像是件困難的事情，因為 iframe 裡的資料其實是其他網站的資料，這有點像是跨域請求的概念。之前有接觸過一點 AJAX，知道跨域的東西 hen 麻煩。

就當我快失去信心，意興闌珊的隨便組合關鍵字在 google 上 google 時，意外發現 [Youtube IFrame Player API](https://developers.google.com/youtube/iframe_api_reference#playVideo) 這個東西。這東西帶給了我一線生機啊！

假設原本使用 iframe 內嵌的話，語法會是這樣

```html
<iframe src="https://www.youtube.com/embed/PEr5agHOTcg" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe>
```

改用 API 後， html 部份只要加入一個 div，其他靠 JS 來處理

```html
 <body>
      <!-- 這個DIV是用來顯示iframe的 -->
      <div id="ytplayer"></div>
  </body>
  <script src="https://www.youtube.com/iframe_api"></script> 
  <script>

    // 自訂影片物件的變數名稱
    var player; 
  
    // API 提供的函數名稱。API js 已經準備好了，這函式就會開始執行
    function onYouTubeIframeAPIReady() {  

      // 初始化影片物件，並指定影片要放在哪個 id 的 div 上面
      player = new YT.Player('ytplayer', {
        videoId: 'PEr5agHOTcg', //你的Youtube 影片ID
        events: {
          'onStateChange': function(event) {
            if (event.data == YT.PlayerState.PLAYING) {
              alert('hello!');  //這邊是當開始播放後，需要做的動作
            }
          }
        }
      });
    }
  </script>
```

之後要控制影片的播放的話，就可以透過 api 來操作。例如

```js
player.playVideo();
player.stopVideo();
```

如果要達成自訂按鈕來播放影片的話，就需要添加 [JavaScript DOM EventListener](https://www.w3schools.com/js/js_htmldom_eventlistener.asp)

```js
// js
var btn = document.querySelector("button");
btn.addEventListener('click', playVideo)   // 我想像中應該是這樣用啦
```

只是後來我不曉得哪邊沒調整到，試不出來，就只好用 [HTML onclick 事件屬性](http://www.w3school.com.cn/tags/event_onclick.asp) 來添加

```html
<button onclick="player.playVideo()">Click ME</button>
```

最後在附上一次 How 哥宇宙宣傳網頁 XD
(這是我自己的二創啦，不是真的官方 der)

<p data-height="430" data-theme-id="0" data-slug-hash="bvzxKM" data-default-tab="result" data-user="ayugioh2003" data-embed-version="2" data-pen-title="HW4-32  設計三欄版型_ytapi| Hexschool HTML, CSS" class="codepen">See the Pen <a href="https://codepen.io/ayugioh2003/pen/bvzxKM/">HW4-32  設計三欄版型_ytapi| Hexschool HTML, CSS</a> by Chiu (<a href="https://codepen.io/ayugioh2003">@ayugioh2003</a>) on <a href="https://codepen.io">CodePen</a>.</p>


---

附上參考資料
BTW，這 API 好像更新的很快，要用之前可先確認官方的說明手冊變了沒 orz

* [【YouTube】(三) 如何透過 YouTube IFrame Player API 控制 Youtube 撥放器？ - Elaine Wu](http://blog.elaine-iic.tw/2015/07/youtube-iframe-player-api.html)
* [【筆記】Youtube 與網頁互動的好幫手 - YouTube IFrame Player API - ParkerRo 趴克肉](https://parkerro.tw/%E3%80%90%E7%AD%86%E8%A8%98%E3%80%91youtube%E8%88%87%E7%B6%B2%E9%A0%81%E4%BA%92%E5%8B%95%E7%9A%84%E5%A5%BD%E5%B9%AB%E6%89%8B-youtube-iframe-player-api/)
* [YouTube Player API Reference for iframe Embeds  |  YouTube IFrame Player API  |  Google Developers](https://developers.google.com/youtube/iframe_api_reference)


<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
