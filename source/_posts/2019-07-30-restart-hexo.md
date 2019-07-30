---
title: 砍掉重練部落格：架設 Hexo 在 gh-pages 
date: 2019-07-30 14:07:52
categories: 部落格設定
tags:
  - Hexo
  - Next
---

最近因為當了六角的遠端助教，讓我想重新寫部落格。雖然幾年前就有用 Hexo 架好部落格，但因為當時還不太懂程式語言與套件的相關概念，導致很多功能是硬湊出來的（像是用 bash 寫自製功能 =_=）。以下將記錄從上一版過度到目前版本的過程。

<!-- more -->

## 砍舊的專案
本來我的部落格架在 ayugioh2003.github.io 上，而我也想繼續沿用。因此我就把原本的 repo 砍了，再重新開一個空白的 repo。

## 初始設定

重新設定過程主要參考 Ray 的[ Hexo 系列文](https://hsiangfeng.github.io/categories/hexo/)。先安裝 hexo-cli 命令列工具，並初始化 hexo 設定，安裝 npm 相依套件，最後啟動 server 在本地端預覽部落格，就完成了初始設定。

```bash
# clone
git@github.com:ayugioh2003/ayugioh2003.github.com.git

# 安裝
npm install hexo-cli -g 
hexo init ayugioh2003
npm install

# 啟動 hexo
hexo server
```

## 主題安裝

Hexo 預設的主題滿簡潔的，在 banner 處會有一顆大月亮，我上一版的主題就是預設的。因為 Ray 的教學中有提到 NeXT 的主題替換，而我也想換換口味，所以也將主題換成 NeXT 了。除了 Ray 的教學文，NeXT 官方網站也有提到替換的方式
* [开始使用 - NexT 使用文档](https://theme-next.iissnan.com/getting-started.html)

## Hexo 基礎設定

基礎設定會在專案資料夾底下的 _config.yml 檔案中。因為我過去有架設 Hexo 的經驗，所以有再修改了 Ray 的一些設定

```yml
# Site
title: 小麥前端 blog # 網站標題
subtitle: 一個心理人跑來學前端的記錄 # 網站附標題
description: # 網站敘述
keywords: # 關鍵字
author: 小麥 # 網站作者名
language: zh-TW # 網站語系
timezone:

# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: https://ayugioh2003.github.io # 網站的 URL
root: /blog/ # 根目錄。所以首頁會是 ayugioh2003.github.io/blog
permalink: :year/:month/:title/ #:year/:month/:day/:title/ # 文章路徑設定
permalink_defaults:
```

## 佈署到 gh-pages 的設定
總共需要三個步驟。一、先用 npm 安裝 hexo-deployer-git 套件。二、在 _config.yml 中調整佈署的相關設定。三、每次寫完文章後，要佈署到 gh-pages 的指令。

```yml
# 命令列指令
npn install hexo-deployer-git --save

# _config.yml。將 example 換成自己的 github 帳號
deploy:
  type: git
  repo: https://github.com/example/example.github.io.git
  branch: master

# 命令列指令。d for deploy，g for generate
hexo d g
```

話說在佈署到 Github 的過程中，我遇到一個神秘的錯誤。後來 Google 後發現，當 Repo 的名稱是 `<username>.github.io` 的形式時，gh-pages 就只能以 master 的形式發布。我本來想將 branch:gh-pages 當靜態網站分支，branch:master 當文章管理的說，結果這個夢想就滅了 QQ
* [Configuring a publishing source for GitHub Pages - GitHub Help](https://help.github.com/en/articles/configuring-a-publishing-source-for-github-pages)

## 建立、發布文章相關指令

環境建好了，就該發篇文來試看看效果。以下參考 Ray 的文章內容，以及 Hexo 官方文件
* [架設Hexo+GitHub | Welcome.Web.World](https://hsiangfeng.github.io/hexo/20190411/932826160/)
* [指令 | Hexo](https://hexo.io/zh-tw/docs/commands)

```bash
hexo new [title] # 新建文章

hexo s # server 啟動伺服器
hexo g # generate 生成靜態頁面
hexo d # deploy 將靜態頁面佈署到 github

# 簡寫
hexo g -d # 生成靜態頁面，立即佈署網站
hexo d -g # 在佈署網站前，先生成靜態網頁

hexo clean # 清除快取檔案與已產生的靜態頁面
```

## 小結

感謝 Ray 的教學系列文，讓我不再將重練 Hexo 視為畏途。日後應該會再根據系列文新增功能到部落格中，像是 GA、搜尋功能等等。