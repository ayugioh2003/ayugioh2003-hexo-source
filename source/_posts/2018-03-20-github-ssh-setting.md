---
title: github_ssh_setting
thumbnail: /images/index.JPG
date: 2018-03-20 16:25:12
categories: 編程
tags:
- git
- github
- ssh
---

## 前言

最近想重新啟用 hexo 的部落格，但太久沒摸，有些設定要重新摸索了 orz。先記錄一些剛剛做的事情


<!-- more -->

## 用 cmd 刪除資料夾的檔案

刪除檔案

`del *`

刪除資料夾

`RD /S *`

* [CMD 删除某文件夾下的所有文件夾和文件_百度經驗](https://jingyan.baidu.com/article/fcb5aff780b456edaa4a711c.html)
* [利用 rd /s/q 命令, 刪除多層資料夾 @ 有ㄉ沒ㄉ... :: 痞客邦 ::](http://october10.pixnet.net/blog/post/4682309-%E5%88%A9%E7%94%A8-rd--s-q-%E5%91%BD%E4%BB%A4%2C%E5%88%AA%E9%99%A4%E5%A4%9A%E5%B1%A4%E8%B3%87%E6%96%99%E5%A4%BE)

## 確認本地端有無 SSH 公鑰，複製貼上到 github 

因為用 SSH clone 的話，之後不用再確認密碼，所以使用 keys 是必要的

先確認有沒有存在 SSH keys

```sh
# 打開 gitbash
ls -al ~/.ssh
# List the files in your .ssh directory, if they exist
```

沒有的話，用 github 註冊的信箱建立一個 SSH keys
`ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`

已經有的話，複製金鑰，貼到 github 去

```sh
clip < ~/.ssh/id_rsa.pub
# Copies the contents of the id_rsa.pub file to your clipboard
```


* [Checking for existing SSH keys - User Documentation](https://help.github.com/articles/checking-for-existing-ssh-keys/)
* [Generating a new SSH key and adding it to the ssh-agent - User Documentation](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)
* [Adding a new SSH key to your GitHub account - User Documentation](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/)

## 修改 vscode 的預設終端機

* [如何修改 Visual Studio Code Terminal 使用程式 | Yowko's Notes](https://blog.yowko.com/2017/11/visual-studio-code-terminal.html?m=1)

## fs.SyncWriteStream is deprecated

在使用時出現奇怪的警告訊息，google 發現可能是 hexo 沒更新，有些語法不被 node.js 支持的關係

```cmd 
# 問題： 
# node 和 hexo 插件的版本帶來的問題：在 node8.x 的版本中，fs.SyncWriteStream 被棄用了。

# 解決： 
# 更新如下插件：

npm install hexo-fs --save
npm install hexo-deployer-git@0.3.1 --save
npm install hexo-renderer-ejs@0.3.1 --save
npm install hexo-server@0.2.2 --save
```

* [hexo（四）DeprecationWarning: fs.SyncWriteStream is deprecated - CSDN 博客](http://blog.csdn.net/liuyongshun2/article/details/79348016)
* [[hexo] 升級與遷移 | Hubery](http://huberyhe.github.io/2017/10/10/hexo-%E5%8D%87%E7%BA%A7%E4%B8%8E%E8%BF%81%E7%A7%BB/)