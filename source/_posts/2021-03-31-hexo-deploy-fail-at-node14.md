---
title: hexo deploy 失敗，版本 node14，訊息：The "mode" argument must be integer…
date: 2021-03-31 23:55:45
thumbnail:
categories:
tags:
---

## 前言
最近為了徵文活動，想重新啟用 hexo 部落格。結果發現使用 `hexo deploy` 指令時出錯了 orz。

## 原因
使用錯誤訊息關鍵字找了一下，好像是 hexo-cli 2.0.0 不支援 node14+ 的樣子。悲劇。

文章提供了兩個解決方案
1. 降低 node 版本
2. 升級到 hexo@4.2.1+

因為我的新筆電有安裝 nvm，切換 node 環境很方便，我就採用方案一，將 node 版本切換到穩定板 node 12 了。
```bash
nvm use 12.18.3
```

## 小結

覺得自己除錯的功力有一點進步了呢。想當初第一次用 hexo 時，完全看不懂該怎麼用，現在竟然一個指令就能解決錯誤訊息了，真是令人感慨呢（？）。


## 參考資料
- [node14+版本下hexo部署失败 | EVE | 暴风雨前夕](https://evestorm.github.io/posts/430/)