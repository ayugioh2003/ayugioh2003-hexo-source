---
title: git push to github without password
date: 2017-09-08 14:29:23
categories: 編程
tags: 
- Git
- Github
---
<!-- thumbnail: /images/index.JPG -->

用 git 這段時間，有一件事情納悶了很久，就是為什麼 git push 的時候會需要輸入密碼呢？結果這件事情在剛剛 google 後終於搞清楚了

- 原因: 可能之前都用到 https 的方式 clone 資料
- 解法: git clone 時採用 ssh 方式，或是重新刪掉遠程 o，然後再新增 ssh 的 o 

```sh
git remote rm origin  
git remote add origin git@github.com:itmyhome2013/blog.git  
```

---

之後想把 hexo 編譯過的檔案 `hexo deploy` 到 gh-page 上，結果失敗。後來把 yaml 中 deploy 的位置從 https 改成 ssh 就好了。我還是不懂為什麼 QQ

參考資料
* [让git push命令不再每次都输入密码 - itmyhome的专栏 - CSDN博客](http://blog.csdn.net/itmyhome1990/article/details/42557817)
* [hexo d 失败： bash: /dev/tty: No such device or address · Issue #2406 · hexojs/hexo](https://github.com/hexojs/hexo/issues/2406)
* [升级到hexo 3.0后deploy type: github选项无效 · Issue #1013 · hexojs/hexo](https://github.com/hexojs/hexo/issues/1013)
* [3.0为什么运行hexo deploy没有反应啊？(Hexo Deploy hanging in 3.0) · Issue #1154 · hexojs/hexo](https://github.com/hexojs/hexo/issues/1154)