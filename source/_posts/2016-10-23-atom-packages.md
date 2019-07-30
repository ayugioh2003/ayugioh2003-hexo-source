---
title: 目前所安裝的atom套件
date: 2016-10-23 19:59:37
categories: 編程
tags:
- Atom
- Markdown
- 整理
---

![來源:https://goo.gl/LGBVzh](/images/20161023atom.png)

想記錄一下目前在 atom 安裝的 package 有哪些，未來有空的話再介紹一下大略的功能。先記錄 markdown 相關 package，其他的放到 others XD

<!-- more -->

---

<!-- toc -->

- [Package: 讓 atom 成為 Markdown 編輯器](#package-讓-atom-成為-markdown-編輯器)
	- [expose｜預覽已開啟檔案](#expose預覽已開啟檔案)
	- [markdown-img-paste｜速貼md圖檔語法](#markdown-img-paste速貼md圖檔語法)
	- [markdwon-preview-enhanced｜md預覽](#markdwon-preview-enhancedmd預覽)
	- [markdown-table-formatter｜調整md表格](#markdown-table-formatter調整md表格)
	- [markdown-writer｜支援md編輯](#markdown-writer支援md編輯)
	- [platformio-ide-terminal｜內置terminal](#platformio-ide-terminal內置terminal)
	- [script｜執行當前腳本](#script執行當前腳本)
	- [vim-mode｜vim語法操作](#vim-modevim語法操作)
	- [wordcount｜算字](#wordcount算字)
	- [Zen｜免除分心](#zen免除分心)
- [其他](#其他)
	- [activate-power-mode｜打字特效](#activate-power-mode打字特效)
	- [emmet｜快速生成語法標籤](#emmet快速生成語法標籤)
	- [color-picker｜取色相關](#color-picker取色相關)
	- [file-icons｜美化檔案圖標](#file-icons美化檔案圖標)
	- [jumpy｜快速跳到某段落](#jumpy快速跳到某段落)
	- [linter｜語法偵錯](#linter語法偵錯)
	- [linter-jshint｜js 靜態語法偵錯](#linter-jshintjs-靜態語法偵錯)
	- [minimap｜程式碼縮圖](#minimap程式碼縮圖)
	- [open_in_cmd｜在該目錄開啟 cmd](#open_in_cmd在該目錄開啟-cmd)
	- [pigments｜取色相關](#pigments取色相關)
	- [symbols-tree-view｜目錄樹](#symbols-tree-view目錄樹)
	- [sync-settings｜同步 atom package](#sync-settings同步-atom-package)
- [時間快照](#時間快照)
	- [2016.11.05](#20161105)
	- [2016.10.23](#20161023)
- [相關連結](#相關連結)

<!-- tocstop -->

---

先記錄幾個事後方便使用快捷鍵

- `ctrl + alt + R` 可重啟 atom
- `ctrl + ,` 可打開 setting，到 `install` 可搜尋 package 下載
- 打開 terminal，輸入 `apm install package-name` 可直接下載 package
- 打開 terminal，輸入 `apm ls` 可查看當前安裝的 package

暫時將 package 分成 Markdown 和 others 兩類

---

# Package: 讓 atom 成為 Markdown 編輯器

忘記是從什麼時候接觸的 markdown 這個語法了。一開始的時候根本看不懂它在幹麻 XD 但後來就漸漸明白它的好了。身為一個還沒什麼在碼程式的人，裝 atom 當然是拿來打 markdown 啦，不然要幹麻。以下來記錄些我覺得對 atom 變身成 markdown 編輯器有幫助的 package

## expose｜預覽已開啟檔案

* 網址：[expose](https://atom.io/packages/expose)
- 按住 `alt + shift + e` 後，能夠預覽目前開啟的檔案畫面。這在全螢幕的狀態下、想換檔案來編輯時的幫助很大

## markdown-img-paste｜速貼md圖檔語法

- 網址：[cocoakekeyu/markdown-img-paste: 一个可以快速粘贴剪贴板里的照片到markdown的插件，并且可以设置使用七牛存储照片。](https://github.com/cocoakekeyu/markdown-img-paste)
- 在 `hackmd.io` 這個網路服務中，只要將本機端的圖片拖曳到編輯器中，它就能自動幫你上傳圖片到 imgur，並且自動生成 `![](filename)` 的語法，第一次看到的時候覺得很感動（恩？）。現在，`markdown-img-paste` 也能做到這件事情。在 md 文件按下 `ctrl+shft+v`，可以完成兩件事情

	1. 儲存照片到 本地端 / imgur / 七牛上
	2. 在 md 檔貼上 `![](filename)`

- 此外，我在 github 上向作者提問，沒想到才兩天就解決了我的提問（[如何自訂本地端儲存路徑和檔名 · Issue #2 · cocoakekeyu/markdown-img-paste](https://github.com/cocoakekeyu/markdown-img-paste/issues/2)），立馬幫這個項目按 star XD。這 package 還滿好用的，想快速的複製後貼圖的話可以使用。

## markdwon-preview-enhanced｜md預覽

- 網址：[markdown-preview-enhanced/README_CN.md at master · shd101wyy/markdown-preview-enhanced](https://github.com/shd101wyy/markdown-preview-enhanced/blob/master/docs/README_CN.md)
- 其實 md 的原始檔不是重點，被它渲染過後的 html 才是大家想要看到的，因此有個方便的 markdown preview 功能是很重要滴。`markdwon-preview-enhanced` 算是 atom 裡，最好用的 markdown preview 工具。我常在用的有以下功能

	1. 按 `Ctrl + Shift + M` 可渲染 md 成 html
	2. 滑動同步
	3. Toc 自動生成
	4. 支援圖片上傳
		- 按下 `Ctrl + Shift + I`，拖曳圖片到視窗
		- 將圖片放到 本地端/imgur/sm.ms
		- 在 md 檔貼上 `![](filename)` 語法

- 這套件就像是 markdown 的瑞士刀，把一些常用的功能都包進來了。滿推薦這個 package 的，可以把內建的 markdwon preview 給停用了

## markdown-table-formatter｜調整md表格

- markdwon 的表格語法，我覺得是個硬傷，因為用起來實在是很麻煩 ... 。`markdown-table-formatter` 會自動調整 table 的格式，會讓表格自動對齊，讓表格變比較好看

## markdown-writer｜支援md編輯

- 好像有支援快速輸入 markdwon 語法的樣子 ... 對這個 package 不是很熟 orz。目前留著的原因是，無序列表換行的時候，它可以幫忙添加一個 `-` 的符號（聽起來我滿懶惰的 ...）

## platformio-ide-terminal｜內置terminal

- 能在當前工作區目錄下開啟 PowerShell，並內嵌在 atom 裡頭（神 package。PowerShell 本身也很神，可惜好像無法以管理員權限執行）。linux 用戶去安裝 `terminal-plus`，它是原始專案，`platformio-ide-terminal` 是 folk 它改成適合 windows 的版本。

## script｜執行當前腳本

- 能直接執行當前文件的程式，阿阿阿好好用啊，簡直快把 atom 改造成 IDE 了（迷：是誰剛剛說只把 atom 當成 markdown 編輯器在看的）。目前試過 `.sh`、`.bat`、`.js`、`.java`、`.py`、`.r` 都可以

- 阿，補充一下為什麼要安裝 `platformio-ide-terminal` 和 `script` 這兩個 package。因為我目前是用 hexo 在產生部落格的 html 檔案，而我將一些語法整合成數個能包在一起執行的 `.sh` 腳本。這樣以後想執行命令時，就能按快捷鍵，而不用碼字啦 ~

## vim-mode｜vim語法操作

- 能夠用 vim 的操作方式來編輯文件，還在學習中。聽說一個牛B的碼農就要用 vim 的指法來碼字才夠牛B，可是我目前只用 `J`, `K`, `L`, `M` 來讓鼠標上下左右而已 ...

## wordcount｜算字

- 能自動計算字數，不過對中文字不太友善。參考就好

## Zen｜免除分心

- 網址：[zen](https://atom.io/packages/Zen)

- 原本這 package 的想法是，讓 edtidor 能有一個不被分心的編輯環境，而這同樣也適合 markdown 的寫作。按下 `Shift + F11` 就能得到全屏的編輯畫面。再加上 `markdwon-preview-enhanced` 的畫面，atom 就變身成屏佔比超大的 markdwon 編輯器了（樂）

---

# 其他

- 除非我接下來很積極的在學某種程式語言（可能是 `js` 或 `python` 或 `java` 或 `R` 吧），不然其他的 package 應該都會被放到 others XD

## activate-power-mode｜打字特效

- 在打字的時候，能產生視窗在振動、以及火花的特效，覺得很酷炫 XD

## emmet｜快速生成語法標籤

- [[學習] Emmet 簡易教學 - 快速上手包 | PJCHENder 愛分享](https://pjchender.blogspot.tw/2016/07/emmet.html)
- 超好用的 ~ 可以快速生成 `html` 和 `css` 的標籤，聽說在各個編輯器平台都支援這個 package（像是 notepad++, sublime）。強力推薦安裝這個 package。

## color-picker｜取色相關

## file-icons｜美化檔案圖標

## jumpy｜快速跳到某段落

Enter jump mode
- `shift + enter`

Reset first character entered
- `backspace`

Cancel/exit jump mode (any)
- `shift + enter`
- `enter`
- `esc`
- `space`


## linter｜語法偵錯

## linter-jshint｜js 靜態語法偵錯

## minimap｜程式碼縮圖

## open_in_cmd｜在該目錄開啟 cmd

## pigments｜取色相關

## symbols-tree-view｜目錄樹

- 我以為這是 atom 會內建的 package，可是卻跑到社群 packages 的分類 ...。總之，這功能好用，能看到目前工作目錄的目錄樹。按 `ctrl + \` 能切換開啟關閉。

## sync-settings｜同步 atom package

- 能夠同步不同電腦上的相同帳戶的 atom package。但我不確定設置會不會相同、以及 atom 的 sytle 等等會不會也能同步

---

# 時間快照

想到的時候，就執行一下 `apm ls`，貼上目前安裝的 atom packages。

## 2016.11.05

├── activate-power-mode@0.3.2
├── atom-beautify@0.29.13
├── atom-html-preview@0.1.19
├── atom-react-preview@2.0.0
├── atom-terminal@0.8.0
├── atom-terminal-panel@4.4.4
├── atom-ternjs@0.14.2
├── busy@0.5.0
├── color-picker@2.2.2
├── emmet@2.4.3
├── expose@0.12.1
├── file-icons@1.7.22
├── git-plus@5.13.4
├── jumpy@3.0.3
├── linter@1.11.18
├── linter-jshint@3.0.1
├── markdown-img-paste@0.3.2
├── markdown-preview-enhanced@0.8.7
├── markdown-table-formatter@2.8.3
├── markdown-writer@2.3.3
├── minimap@4.25.6
├── open_in_cmd@0.6.1
├── pigments@0.37.0
├── platformio-ide-terminal@2.2.0
├── script@3.9.0
├── symbols-tree-view@0.13.2
├── sync-settings@0.7.2
├── vim-mode@0.65.1
├── wordcount@2.7.0
└── Zen@0.16.4

## 2016.10.23

├── activate-power-mode@0.3.2
├── atom-html-preview@0.1.19
├── atom-terminal@0.8.0
├── atom-ternjs@0.14.2
├── atomic-chrome@0.3.0
├── busy@0.5.0
├── git-plus@5.13.4
├── jumpy@3.0.3
├── markdown-preview-enhanced@0.8.7
├── markdown-table-formatter@2.8.3
├── markdown-writer@2.3.3
├── open_in_cmd@0.6.1
├── script@3.9.0
├── symbols-tree-view@0.13.2
├── sync-settings@0.7.2
├── terminal-plus@0.14.5
└── vim-mode@0.65.1

└── (empty)

---

# 相關連結

- [Atom 使用心得與 Package 推薦 (2016/07/26 更新) « Negai no Sekai](http://negaihoshi.logdown.com/posts/220517-atom-use-ideas-and-recommendations)
- [Github atom IDE Plugin 簡介與使用心得 | Jacky's Notes](http://hungjie19.github.io/hexoblog/2016/05/23/Github-atom-IDE-Plugin-%E7%B0%A1%E4%BB%8B%E8%88%87%E4%BD%BF%E7%94%A8%E5%BF%83%E5%BE%97/)
- [Github 開源編輯器 Atom 常用插件及安裝方法 | AbsentM's Notes](https://git.io/vXacR)
