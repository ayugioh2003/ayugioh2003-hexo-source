---
title: Hexo 安裝過程
date: 2016-10-18 17:13:05
categories: 編程
tags:
  - Blog
  - Hexo
---

![來源：https://wsgzao.github.io/post/hexo-guide/](/images/20161018HexoAndHexo.png)

本來想用 jekyll 來當架在 Github 上的部落格系統，但安裝過程太坑爹了，一氣之下就換成用 Hexo 來架設。雖然過程中也有點鬼打牆 ... 但真的有比較好設定。以下稍微紀錄安裝的過程。

<!-- more -->

---

<!-- toc -->

- [安裝過程](#安裝過程)
	- [安裝 node.js](#安裝-nodejs)
	- [安裝 git](#安裝-git)
	- [註冊 github](#註冊-github)
	- [安裝hexo](#安裝hexo)
- [問題解決](#問題解決)
- [預定的除錯](#預定的除錯)

<!-- tocstop -->

---

# 安裝過程

## 安裝 node.js

```=
// 確認 node 安裝成功
node -v

// 確認 npm 安裝成功
npm -v
```

## 安裝 git

```=
// 確認 git 安裝成功
git --version

```

## 註冊 github

- 開啟 gh-pages 功能（若 repo 用 name.github.com，就不用）
- 設置 SSH

## 安裝hexo

在本機上的使用

```=
// 安裝hexo，用全局
npm install -g hexo
npm install hexo --save // 選一個裝吧，我不太懂差異 ...

// 初始化 hexo 架構
hexo init
npm install // 有人說這會自動幫妳安裝需要的組件

//建立新文章
hexo new "title"

// 產生 public 檔，就是 html 檔
hexo generate

// 在本機 sever 觀看
hexo sever
```

就會在本機端 http://localhost:4000/ 看到網站

如果要放到 github 上，在 `_config.yml` 加入這串

```=
deploy:
  type: git
  repo: https://github.com/ayugioh2003/ayugioh2003.github.com.git
  branch: master
```

就能在 ayugioh2003.github.com 看到

接著輸入

```=
// push 到 github 上
hexo deploy
```

# 問題解決

- Yaml

我他媽卡在這裡幾個小時啊！！！

```=
deploy:
  type: git
  repo: https://github.com/ayugioh2003/ayugioh2003.github.com.git
  branch: master
```

- SSH

兩個 RSA 檔案都點開來看，有開頭、密鑰、信箱的那個才是正確的


# 預定的除錯

- 標籤
- 類別
- YY/MM/DD 檔名

---

* [史上最详细的 Hexo 博客搭建图文教程 | Xuanwo's Blog](https://xuanwo.org/2015/03/26/hexo-intor/)
* [Hexo](https://hexo.io/zh-tw/)
* [hexo 架 blog 初體驗 | kpman | code](http://code.kpman.cc/2013/04/26/hexo%E6%9E%B6blog%E5%88%9D%E9%AB%94%E9%A9%97/)
* [2016 年最新的 hexo 教程 | Rudy-Yuan 的博客](http://www.rudy-yuan.net/archives/2016-newest-hexo-guide/)
