---
title: 在網頁放影片，自動重複播放且靜音
date: 2020-03-17 16:03:32
thumbnail:
categories: 前端開發
tags:
- w3HexSchool
- w3Hexschool-2020-challenge
- 接案
- 接案2019
- CSS
---

在先前專案開發時，遇到一個需求是，想在 banner 地方放上一個滿版的重複自動播放影片，播放時不要有聲音。因為之前沒什麼在網頁中放影片的經驗，就研究了一下。

## 如何達成放上影片的需求

以下是在參考一些文章後整理出的方法
1. 用 `<video>` tag 引入影片，就像是使用 `<img>` 引入圖片一樣
2. 在 `<video>` 添加 autoplay, muted, loop 等屬性，達到自動播放、靜音、循環播放效果
3. 用 CSS 設定將影片滿版

```html
<video autoplay muted loop id="myVideo">
  <source src="rain.mp4" type="video/mp4">
</video>

<style>
#myVideo {
  position: fixed;
  right: 0;
  bottom: 0;
  min-width: 100%;
  min-height: 100%;
}
</style>
```

## 潛在需求

當時查完資料後，沒有多久完成了符合需求的程式碼。但現在想想，覺得影片播放可能還有一些潛在需求。簡單記錄一下

1. 流量問題。這次專案影片大小沒很大，所以直接跟網頁檔案放在一起。但感覺放在 Youtbube、vimeo、或專用伺服器可能會更好？
2. 不同版型的影片。專案時有將影片分成桌機版和手機版影片，我是先在網頁擺兩個 `<video>` 分別引入桌機版和手機版影片，當使用者使用桌機時則顯示桌機版的影片，使用手機時則顯示手機版影片。不過我不確定這是不是最佳解就是了。
3. 影片的格式。後來把網頁丟去測速時，被建議說換成 webm 格式會更好。這點可能也是要注意的地方。

## 參考資料


* [How To Create a Fullscreen Video Background](https://www.w3schools.com/howto/howto_css_fullscreen_video.asp)
* [Should I use a video as a background? | CSS-Tricks](https://css-tricks.com/should-i-use-a-video-as-a-background/)
* [Going beyond images with basic video for the web](https://web.dev/video-basics/)
* [How we add a video background to our home page](https://www.barkweb.co.uk/blog/how-we-added-a-video-background-to-our-home-page)
* [Can I use... Support tables for HTML5, CSS3, etc](https://caniuse.com/#search=video)
* [html5 - How to open .mov format video in HTML video Tag? - Stack Overflow](https://stackoverflow.com/questions/31380695/how-to-open-mov-format-video-in-html-video-tag)
* [Walking dog stock photos, royalty-free images, vectors, video](https://stock.adobe.com/tw/search/video?filters%5Bcontent_type%3Avideo%5D=1&order=relevance&safe_search=1&search_page=2&search_type=pagination&acp=&aco=walking+dog&limit=100&k=walking+dog&get_facets=0&asset_id=293514354)
* ffmpeg, mov, mp4, webm

套件
* [Vidim - Easy background videos](https://originalexe.github.io/vidim/)
* [jquery-youtube-background - npm](https://www.npmjs.com/package/jquery-youtube-background)
* [pupunzi/jquery.mb.YTPlayer: use a custom yutube player for a video as background on jQuery framework](https://github.com/pupunzi/jquery.mb.YTPlayer)
  * [How to Build a YouTube Video Website Background - Designmodo](https://designmodo.com/video-background-website/)