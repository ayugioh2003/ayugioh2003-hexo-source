---
title: 重新嘗試 win 底下的 SubLinux 環境
date: 2019-11-25 01:01:52
categories: 
tags: 
  - linux
  - wsl
---

因為今天是接案的暫時空閒日子，就把時間拿來研究之前沒搞得很懂的 Windows Sub Linux 惹。以下先列出自己的嘗試步驟

<!-- more -->

## 一、移除舊的 legacy 版本
好像去年還前年時，為了嚐鮮，有先用了 beta 版本 wsl，所以要先移除掉
```bash
wsl --unregister Legacy
```
* [安裝或移除 Windows 10 年度更新版或建立者更新 | Microsoft Docs](https://docs.microsoft.com/zh-tw/windows/wsl/install-legacy)

## 二、安裝 ubuntu 18 版本
* [介紹好用工具：WSL (Windows Subsystem for Linux) | The Will Will Web](https://blog.miniasp.com/post/2019/02/01/Useful-tool-WSL-Windows-Subsystem-for-Linux)
* [Windows Subsystem for Linux (WSL) 環境設定 - HackMD](https://hackmd.io/@tf-z1zFMTIC8ADhxEcGJEA/BJByCIUHf)
* [Windows Subsystem for Linux (WSL) Tutorial & How To - YouTube](https://www.youtube.com/watch?v=av0UQy6g2FA)
* [Windows 10 Bash & Linux Subsystem Setup - YouTube](https://www.youtube.com/watch?v=Cvrqmq9A3tA)
* [【WSL】Windows Subsystem for Linux 安裝及基本配置！ – 台灣微軟學生大使](https://blogs.msdn.microsoft.com/microsoft_student_partners_in_taiwan/2017/10/03/wsltune/)

## 三、更新 apt 
```bash
sudo apt update
```
本來安裝完 ubuntu 後，想直接安裝 nodejs，結果一直跳出錯誤訊息 `unable to locate package nodejs` orz。後來 google 後，有人說要先更新 apt 這個 linux 世界用來下載套件用的方便工具（對應到 win 世界，相當於 chocolatey）
* [ubuntu - apt-get install is not working in WSL - Super User](https://superuser.com/questions/1359633/apt-get-install-is-not-working-in-wsl/1359995)
* [apt - Bash (on Windows 10) doesn't locate any package - Ask Ubuntu](https://askubuntu.com/questions/759678/bash-on-windows-10-doesnt-locate-any-package)

## 四、安裝 nvm 
本來想直接安裝 nodejs，後來想說沒用過 nodejs 版本切換工具，所以就跑去下載 nvm 惹。
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash

nvm install 12.13.1 #目前 node 穩定版本
nvm list #列出已安裝版本
nvm use 版本號 #切換版本
```
* [nvm：快速安裝、切換不同版本的 Node.js](https://noob.tw/nvm/)
* [[Node.JS] 在 Windows 下使用 nvm 切換 Node 版本](https://oranwind.org/nvm-windows/)
* [Node.js](https://nodejs.org/en/)


## 在 Linux 跑 VSCode
無聊在 terminal 敲了 `code .` 指令，這在 cmd 中會直接呼叫出 VSCode，並以目前路徑開啟。沒想到，在 wsl 中敲 `code .`，竟然跳出提示 `Installing VS Code Server` @@。後來研究後，好像是在 wsl 開啟一個 sever，讓 server 跟 win 溝通資料，這樣就能使用到 win 中的 VSCode 了。真是黑科技 R
* [Run Visual Studio Code in Windows Subsystem for Linux](https://code.visualstudio.com/remote-tutorials/wsl/run-in-wsl)

## zsh, oh my zsh
* [Windows Subsystem for Linux (WSL) 環境設定 - HackMD](https://hackmd.io/@tf-z1zFMTIC8ADhxEcGJEA/BJByCIUHf)
* [Windows Subsystem for Linux 環境配置 (最新 1709 版) - Hungys.blog() - Medium](https://medium.com/hungys-blog/windows-subsystem-for-linux-configuration-caf2f47d0dfb)
* [Linux 查詢與更改登入 shell 設定，chsh 指令用法教學與範例 - G. T. Wang](https://blog.gtwang.org/linux/linux-chsh-command-change-login-shell-tutorial/)


---

## 之後考慮研究

Linux 桌面系統，直接在 windows 玩 Ubuntu GUI 界面
* [Windows Subsystem for Linux (WSL) 使用 Linux 桌面軟體與中文字型 - 石頭閒語](http://rocksaying.tw/archives/2018/wsl-run-linux-desktop-software.html)

中文輸入
* 目前無法輸入。issue 說已經修復好，但還沒在 window store 上架，可能要再等等吧
* [Version: 0.3.2171.0无法使用中文输入法 · Issue #2459 · microsoft/terminal](https://github.com/microsoft/terminal/issues/2459)

查看其他語系的評論
* 在網頁版查看
* [Get Windows Terminal (Preview) - Microsoft Store](https://www.microsoft.com/en-us/p/windows-terminal-preview/9n0dx20hk701?activetab=pivot:reviewstab)