---
title: 將 Github 上的 repo 轉讓給別人
date: 2020-01-16 22:39:27
categories: 前端工程
tags:
  - Github
---

## 前言

這陣子有在處理一個專案。剛開始這個專案是開在我的帳號上，大部分的時間也是我在開發。不過，由於 Github 的私人 repo 只能有三個協作者，而後續可能會再加入新的協作帳號進來，所以就在想該怎麼辦。

後來有人提到「诶我 Github 帳號是付費的，應該可以轉給我喔」，於是我就開始研究該怎麼轉換 repo 的 owner 了。

<!-- more -->

## 官方的說明

官方其實說明滿清楚的。先附上簡體中文與英文說明
* [轉讓倉庫 - GitHub 幫助](https://help.github.com/cn/github/administering-a-repository/transferring-a-repository)
* [Transferring a repository - GitHub Help](https://help.github.com/en/github/administering-a-repository/transferring-a-repository)

以我的狀況，是「一般用戶」轉給「一般用戶」。轉讓步驟大概如下：
1. 在 GitHub 上，導航到倉庫的主頁面。
2. 在倉庫名稱下，單擊  Settings（設置）。
![Image](https://i.imgur.com/unxMWDK.png)
3. 在 “Danger Zone（危險區域）” 下，單擊 Transfer（轉讓）。
![Image](https://i.imgur.com/Nu2GSoJ.png)
4. 閱讀有關轉讓倉庫的信息，然后輸入您要將倉庫所有權轉讓至的用戶或組織的名稱。
![Image](https://i.imgur.com/kD7k0RP.png)
5. 根據新所有者的訂閱，閱讀有關可能失去功能的警告。
![Image](https://i.imgur.com/BwXnb7R.png)
6. 輸入您要轉讓的倉庫的名稱，然后單擊 I understand, transfer this repository（我了解，轉讓此倉庫）。
![Image](https://i.imgur.com/gA4RLic.png)

最後 Github 會寄信給被轉讓者，等他確認後，repo 就會轉給他惹


## 小結

滿新鮮的，原來 Github 有轉讓 repo 的功能，而且操作起來還滿方便的，滑鼠點幾下就好惹 ~

