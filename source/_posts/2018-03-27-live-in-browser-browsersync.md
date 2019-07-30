---
title: 使用 browsersync 讓網頁能在瀏覽器中即時預覽
thumbnail: /images/index.JPG
date: 2018-03-27 15:59:52
categories: 編程
tags:
- FrontEnd
---

## 前言
在重新開始學前端後，就一直很想能像 Codepen 那樣，能編輯完程式碼後，就即時在瀏覽器看到即時畫面。曾測試過一些方法，但都無法。後來找到了 browser-sync 

<!-- more -->

## 原理

在我理解中，browser-sync 會建立一個簡易的 server，並監測專案資料夾裡面的檔案。如果檔案有變更的話，就重新整理頁面。另外，server 端會在 `<body>` 插入相關語法，因此沒加入 `<body>` 的網頁是不會自動重整的（我踩這個雷踩了好幾個小時 QQ）

## 作法

以下只記錄簡單的作法

先安裝 node.js，會自帶 npm 管理工具
- 到官網下載安裝
- 或是透過 chocolately 安裝

```bash
choco install node.js
```


在全局安裝 browser-sync

```bash
npm install -g browser-sync
```

監測檔案、開啟網頁、即時重整預覽

```bash
browser-sync start --server --file "*.*"
```

---

參考資料

* [簡化前端測試的利器 – BrowserSync – NewHTML](http://newhtml.net/%E7%AE%80%E5%8C%96%E5%89%8D%E7%AB%AF%E6%B5%8B%E8%AF%95%E7%9A%84%E5%88%A9%E5%99%A8-browsersync/)
* [Browsersync 簡介及使用 – 技術學習小組](http://blog.qiji.tech/archives/2878)
* [Browsersync 中文網 - 省時的瀏覽器同步測試工具](http://www.browsersync.cn/)
* [用 browser-sync 實時刷新 browser 的坑 - 簡書](https://www.jianshu.com/p/480c707cd553)
* [SCSS 開發的 LiveReload 議題 - eddychang.me](http://eddychang.me/blog/others/92-scss-livereload.html)
