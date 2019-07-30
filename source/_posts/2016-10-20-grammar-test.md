---
title: 語法測試
date: 2016-10-20 17:36:37
categories: 編程
tags:
  - Markdown
  - JavaScript
---

![來源：http://kirkstrobeck.github.io/whatismarkdown.com/](/images/20161020markdown.png)

想測試一下 markdown 語法和 js 語法在 hexo 上呈現的效果

<!-- more -->

---

<!-- toc -->

- [Markdown 語法測試](#markdown-語法測試)
	- [標題](#標題)
	- [清單](#清單)
	- [引言](#引言)
	- [表格](#表格)
	- [程式碼](#程式碼)
	- [連結](#連結)
	- [強調](#強調)
	- [分隔線](#分隔線)
- [Javascript 語法測試](#javascript-語法測試)
- [參考資料](#參考資料)

<!-- tocstop -->

---

# Markdown 語法測試

## 標題

```
// 標題語法

# 標題一
## 標題二
### 標題三

標題一
================

標題二
----------------

```

（怕打亂目錄結構，就不做標題的實際呈現了）

## 清單

```
// 無序清單

- 項目A
- 項目B
- 項目C

// 有序清單

1. 項目一
2. 項目二
3. 項目三
```

無序清單

- 項目A
- 項目B
- 項目C

有序清單

1. 項目一
2. 項目二
3. 項目三



## 引言

```
// 引言語法

> 今天天氣真好
```

> 今天天氣真好


## 表格

| Header One | Header Two |
|:-----------|:-----------|
| Item One   | Item Two   |

## 程式碼

```
// 程式碼格式

測試測試 `我是在句子內的程式碼` 測試測試

` ` `
我是有獨立區塊的程式碼
` ` `
↑ 要把三個 ` 接在一起

```

測試測試 `我是在句子內的程式碼` 測試測試

```
我是有獨立區塊的程式碼
```

## 連結

```
我是李[連結](https://ayugioh2003.github.io/)
```
我是李[連結](https://ayugioh2003.github.io/)

## 強調

```
我要*強調*
```
我要*強調*

## 分隔線

```
// 分隔線語法

---
```

---

# Javascript 語法測試

```javascript
// js 程式碼

<script type="text/javascript">
  function disp_alert(){
    alert("我是警告框！！")
  }
</script>

<input type="button" onclick="disp_alert()" value="显示警告框" />
```

<script type="text/javascript">
function disp_alert(){
  alert("我是警告框！！")
}
</script>


<div>
  點擊按鈕看看 <input type="button" onclick="disp_alert()" value="顯示警告框" />
</div>

---

# 參考資料

* [Markdown | GitBook 中文解說 - 2.4](https://wastemobile.gitbooks.io/gitbook-chinese/content/format/markdown.html)
* [Markdown 語法說明](http://markdown.tw/)
