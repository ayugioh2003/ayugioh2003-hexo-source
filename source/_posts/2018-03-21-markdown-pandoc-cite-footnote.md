---
title: 如何用 markdown 寫論文
thumbnail: /images/index.JPG
date: 2018-03-21 16:55:11
categories: 編程
tags:
- Markdown
- Pandoc

---

## 前言

一直有在想說，如果當時寫論文時，是用 Markdown 來寫的話，撰寫速度會不會變得更快。我想應該是不會的，而且可能還會因為摸設定摸到死掉 XD。以下記錄目前蒐集到的，如何用 Markdown 寫論文的方式

<!-- more -->

## 一、下載 Pandoc

Pandoc 是 Markdown 的一種擴充。Markdown 不能解決的，就交給 Pandoc 吧

1. 到官網下載 Pandoc，順便用 Anaconda 下載 Python，然後在終端機輸入 `pip install pandoc-fignos` 插件
2. node.js 也下載比較好的樣子

## 如何引用文獻

1. 需要先有 bibtex 文件。可以用 Zotero 或 Endnote 來產生管理。
2. 把 bibtex 檔放在目錄底下 
3. bibtex 內容大概是這樣

```bib
@article{yangzhiping2003,
    title = {試評卡尼曼經濟心理學研究及其影響 [J]},
    volume = {26},
    number = {4},
    urldate = {2013-05-27},
    journal = {心理科學},
    author = {陽志平},
    year = {2003},
    pages = {724–726}
}
```
4. 文中需要這樣引用 
    - `[yangzhiping2003]` 在研究中提到，blabla ...
    看起來
    會像是

## 腳註

在文中用

```
AAA表示[^1]，在BBB的時候[^2]
```

在文末用
```
[^1]:
[^2]:
```

還是有點複雜，先到這裡打住好了

---

參考資料

* [raytaylorlin/hust-graduation-thesis-pandoc: A tool for rendering HUST graduation thesis(including master and bachelor) using pandoc and latex.](https://github.com/raytaylorlin/hust-graduation-thesis-pandoc)
* [Markx](http://alfred-sun.github.io/markx-pandoc/)
* [Pandoc’s Markdown 語法中文翻譯](http://pages.tzengyuxio.me/pandoc/#%E8%85%B3%E8%A8%BB)
* [Markdown 寫作進階：Pandoc 入門淺談 - 陽志平的網志](http://www.yangzhiping.com/tech/pandoc.html)
* [科學網—如何用 Markdown 寫論文？ - 王樹義的博文](http://blog.sciencenet.cn/blog-377709-1088215.html)