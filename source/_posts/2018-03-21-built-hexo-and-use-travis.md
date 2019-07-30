---
title: 建立 Hexo 部落格，並與 Travis 整合
thumbnail: /images/index.JPG
date: 2018-03-21 02:43:55
categories: 編程
tags:
- Hexo
- Travis
---

## 前言

一直以來都覺得用 Hexo 寫 blog 有點辛苦，除了要 commit 文件檔外，還要 hexo generate, hexo deploy。雖然我寫成腳本了，可以一鍵執行，但總覺得很臃腫。最近一直聽到持續整合這個東西，想說有空的話來試看看好了。

<!-- more -->

# 先 build Hexo

可參考 卡斯伯 的教學影片

* [(3) High翻天啊 - 2017最HOT丢回.... Follow us for more funny movement at...](https://www.facebook.com/WccCasper/videos/486603828402512/)

git 建立與備份流程

```bash
git init # 初始化
git add. # 把新增的項目加入
git commit -m "git init" # 記錄訊息
git remote add origin git@github.com:xxx.git # 新增遠方的 origin，如果是 clone 下來的 repo 就不用這行惹
git push -u origin master # 遠端路徑：push 原始檔，not hexo-demo project
```

建立 Hexo 與發文流程
```bash
# 安裝 CLI command 介面
npm install -g hexo-cli

# 快速雛型
hexo init <folder>
cd <folder>
npm install 

# 啟動(本地端預覽)
hexo s # s=server, localhost:4000

# 建立靜態網站
hexo g # g=generate, public 資料夾生成

# 佈署(push 站點)
# 先填寫部屬路徑，修改 _config.yml
deploy:         # _config.yml
    type:git
    repo:xxx.git
    branch:gh-pages

# 佈署
hexo g 
npm install hexo-deployer-git --save # 要先下載，不然不能 hexo g
hexo d # push public to branch:gh-pages

# 一個 site 佈署兩個站點
# 改成相對路徑，修改 _config.yml
relative_link: true
```

Themes 安裝版型

```
ex Anodyne 
   example - ▇ 範例畫面
   link - Anodyne 專案頁面

1.安裝themes： template/installation
2.套用themes：
_config.yml  //置換themes
  theme:landscape anodyne

themes/anodyne/_config.yml  //細部修改
  Disqus comments 留言板
  comments:
    disqus_shortname:
  GA
  google_analytics:
     
3.客製化themes：
layout 資料夾，template language 熟悉與了解邏輯。
```

---

## Travis

待用

參考
* [使用 Travis CI 自動部署 Hexo - 簡書](https://www.jianshu.com/p/5e74046e7a0f)
* [Hexo使用Travis CI自动化部署 - 简书](https://www.jianshu.com/p/93918de6fa2c)
* [手把手教你使用Travis CI自动部署你的Hexo博客到Github上 - 简书](https://www.jianshu.com/p/e22c13d85659)
* [使用 Travis CI 自動部署 Hexo 博客 | IT 範兒](http://www.itfanr.cc/2017/08/09/using-travis-ci-automatic-deploy-hexo-blogs/)
* [Hexo - 使用 Travis CI 自動佈署 Blog | 天空的垃圾場](https://skychang.github.io/2017/01/01/Hexo-Use_Travis_CI_Auto_Deploy_Blog/)
* [Hexo 自动部署到 Github | 三点水](http://lotabout.me/2016/Hexo-Auto-Deploy-to-Github/)
* [使用 Travis CI 自動發布 Hexo 內容到 Github｜SoarLin's blog](https://soarlin.github.io/2017/03/29/use-travis-ci-auto-deploy-to-github/)
* [用 Travis CI 自動部署 Hexo 博客 | Karl's Notes](https://www.karlzhou.com/2016/05/28/travis-ci-deploy-blog/)
* [使用 Travis CI 自動更新 GitHub Pages | IIssNan's Notes](http://notes.iissnan.com/2016/publishing-github-pages-with-travis-ci/#comments)
* [用 Travis CI 自動部屬 hexo 到 GitHub | SSARCandy's Blog](https://ssarcandy.tw/2016/07/29/hexo-auto-deploy/)
* [使用 Travis CI 自動更新 Hexo Blog · Pupa](http://xwartz.xyz/pupa/2016/06/auto-update-with-travis-ci/)
* [使用 Travis 自動部署 Hexo 到 Github 與 自己的服務器 - 我的兒子叫酸奶 - SegmentFault 思否](https://segmentfault.com/a/1190000009054888)
* [持續集成服務 Travis CI 教程 - 阮一峰的網絡日志](http://www.ruanyifeng.com/blog/2017/12/travis_ci_tutorial.html)
* [steveklabnik/automatically_update_github_pages_with_travis_example: An example of automatically updating GitHub Pages when you're using Travis CI.](https://github.com/steveklabnik/automatically_update_github_pages_with_travis_example)