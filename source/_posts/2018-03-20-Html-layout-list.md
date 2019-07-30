---
title: Html_layout_list
thumbnail: /images/index.JPG
date: 2018-03-20 17:05:13
categories: 編程
tags:
- Html
- Css
- Layout
---

## 前言

最近想學前端的東西，接觸到切版的相關資訊，想說簡單記錄一下切版的類型，以及各種 display 類型置中的方式。資料應該是比較古早的，先不加入 bootstrap 和 flexbox，等之後學到再回來補

<!-- more -->

* 表格布局: table (我大學時用過 XD)
* 浮動布局: div `float: left`
    * 搭配 div.clearfix, clear: both
* 列表布局: div `display: inline-block`
    * 有副作用，inline-block 之間會有約 4px 的空格，需用 css hack 消除
    * 在父元素設定 `font-size: 0px`



* [CSS 屬性 display 的值 inline block inline-block none @ Vexed's Blog :: 隨意窩 Xuite 日誌](http://blog.xuite.net/vexed/tech/29221717-CSS+%E5%B1%AC%E6%80%A7+display+%E7%9A%84%E5%80%BC+inline+block+inline-block+none)
* [詳解 CSS display:inline-block 的應用 | 狼狼的藍胖子](http://luopq.com/2015/11/01/display-inline-block/)
* [拜拜了, 浮動布局 - 基于 display:inline-block 的列表布局 « 張鑫旭 - 鑫空間 - 鑫生活](http://www.zhangxinxu.com/wordpress/2010/11/%E6%8B%9C%E6%8B%9C%E4%BA%86%E6%B5%AE%E5%8A%A8%E5%B8%83%E5%B1%80-%E5%9F%BA%E4%BA%8Edisplayinline-block%E7%9A%84%E5%88%97%E8%A1%A8%E5%B8%83%E5%B1%80/)
* [拜拜了, 浮動布局 - 基于 display:inline-block 的列表布局 « 張鑫旭 - 鑫空間 - 鑫生活](http://www.zhangxinxu.com/wordpress/2010/11/%E6%8B%9C%E6%8B%9C%E4%BA%86%E6%B5%AE%E5%8A%A8%E5%B8%83%E5%B1%80-%E5%9F%BA%E4%BA%8Edisplayinline-block%E7%9A%84%E5%88%97%E8%A1%A8%E5%B8%83%E5%B1%80/)
* [如何解決 inline-block 元素的空白間距_inline-block 教程_w3cplus](https://www.w3cplus.com/css/fighting-the-space-between-inline-block-elements)

## Box Model

我大致理解成，有分成 block 類型的，與 inline 類型的 box model
inline 外層會包一個 iine box 

* [Box Model - CSS 框框模型 [2*] @ 網頁藝術思考 - CSS 網頁設計藝術, 友善的無障礙網頁 :: 痞客邦 ::](http://boohover.pixnet.net/blog/post/18087970-box-model-css-%E6%A1%86%E6%A1%86%E6%A8%A1%E5%9E%8B)
* [CSS float 浮動的深入研究、詳解及拓展 (二) « 張鑫旭 - 鑫空間 - 鑫生活](http://www.zhangxinxu.com/wordpress/2010/01/css-float%e6%b5%ae%e5%8a%a8%e7%9a%84%e6%b7%b1%e5%85%a5%e7%a0%94%e7%a9%b6%e3%80%81%e8%af%a6%e8%a7%a3%e5%8f%8a%e6%8b%93%e5%b1%95%e4%ba%8c/)