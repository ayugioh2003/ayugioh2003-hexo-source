---
title: 將 map、filter、reduce 的運作結果用 emoji 表示
date: 2019-08-29 18:17:49
categories:
  - 前端開發
tags: 
  - JavaScript
  - EcmaScript
  - ES5
---

忘記在爬什麼文的時候，發現一張來自 [五倍紅寶石的 Elixir installation party 的簡報照片](https://www.facebook.com/photo.php?fbid=2207033829313801&set=a.227844993899371&type=3&theater)，上面用了各種 Emoji、以及食材料理前與料理後的譬喻，來說明陣列方法：map、filter、reduce 該怎麼理解。

```python
# 簡報上的程式碼
map(['🐮', '🥔', '🐔', '🌽'], cook) # => ["🍔", "🍟", "🍗", "🍿"]
filter(['🍔', '🍟', '🍗', '🍿'], isVegetarian) # => ["🥔", "🌽"]
reduce(['🍔', '🍟', '🍗', '🍿'], eat) # => "💩"
```

因為覺得滿有趣的，所以決定改寫成 JavaScript 的版本玩看看 XD

<!-- more -->

## 食材間的對應關係與資料設定

在照片中，有用到了九種 Emoji。其中四種是料理前的食材：🐮🥔🐔🌽，四種是料理後的…料理：🍔🍟🍗🍿，剩下一種是消化後的大便 💩。

此外，由於後續會需要判別哪些食物是給素食者吃的，所以也需要對食物貼上是否是素食的標籤。像🍟🍿這兩個食物就需要貼上。以下是我部份的食物資料設定：

```js
const foodData = {
  '🐮': {
    name: 'cow',
    before: '🐮',
    after: '🍔',
    vegetable: false
  },
  '🥔': {
    name: 'potato',
    before: '🥔',
    after: '🍟',
    vegetable: true
  },
  ...
  ,
  '🍔': {
    name: 'hamburger',
    before: '🍔',
    after: '',
    vegetable: false
  },
  '🍟': {
    name: 'fries',
    before: '🍟',
    after: '',
    vegetable: true
  },
  ...
}
```

用 Emoji 來當物件的 key 還滿新鮮的 XD

## map

在 EcmaScript 5.1 中，Array.prototype 已經有內建 map、filter、reduce 方法了，所以可以直接拿來用。

而使用 [map](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Array/map) 的目的則是：經過烹煮後，`['🐮', '🥔', '🐔', '🌽']` 這四個食材，就會變成 `["🍔", "🍟", "🍗", "🍿"]` 惹。yummy

```js
// map
function cook(item, index, array) {
  return foodData[item].after
}

['🐮', '🥔', '🐔', '🌽'].map(cook) // => ["🍔", "🍟", "🍗", "🍿"]
```

## filter

使用 [filter](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)，就可以將素食的料理挑出來，其他不是素食的料理就當作沒看見。

```js
// filter
function isVegetarian(item, index, array) {
  return foodData[item].vegetable
}

['🍔', '🍟', '🍗', '🍿'].filter(isVegetarian) // => ["🥔", "🌽"]
```


## reduce

經過 [reduce](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce) 的消化作用後，吃下去的料理就會變成 💩 惹

```js
// reduce
function eat(item, index, array) {
  return '💩'   
}

['🍔', '🍟', '🍗', '🍿'].reduce(eat) // => "💩"
```

## 小結

以下是完整程式碼

```js
/*
 * 用 Emoji 表示 map、filter、reduce 的概念
 */
var foodData = {
  '🐮': {
    name: 'cow',
    before: '🐮',
    after: '🍔',
    vegetable: false
  },
  '🥔': {
    name: 'potato',
    before: '🥔',
    after: '🍟',
    vegetable: true
  },
  '🐔': {
    name: 'chicken',
    before: '🐔',
    after: '🍗',
    vegetable: false
  },
  '🌽': {
    name: 'corn',
    before: '🌽',
    after: '🍿',
    vegetable: true
  },
  '🍔': {
    name: 'hamburger',
    before: '🍔',
    after: '',
    vegetable: false
  },
  '🍟': {
    name: 'fries',
    before: '🍟',
    after: '',
    vegetable: true
  },
  '🍗': {
    name: 'drumstick',
    before: '🍗',
    after: '',
    vegetable: false
  },
  '🍿': {
    name: 'popcorn',
    before: '🍿',
    after: '',
    vegetable: true
  },
}
　

function cook(item, index, array) {
  return foodData[item].after
}
['🐮', '🥔', '🐔', '🌽'].map(cook) // => ["🍔", "🍟", "🍗", "🍿"]

function isVegetarian(item, index, array) {
  return foodData[item].vegetable
}
['🍔', '🍟', '🍗', '🍿'].filter(isVegetarian) // => ["🥔", "🌽"]

function eat(item, index, array) {
  return '💩' 
}
['🍔', '🍟', '🍗', '🍿'].reduce(eat) // => "💩"
```