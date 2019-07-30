---
title: 從github上clone到coding
date: 2016-10-22 17:23:22
categories: 編程
tags:
  - Hexo
  - Git
  - Github
---

![來源：https://coding.net/about](/images/20161022coding.png)

自從知道有 webIDE 這種東西存在後，一直肖想著一件事情，就在只要在有網路的地方，就可以在 github 上的 hexo or jekyll 寫部落格。先前是用 cloud9，但好像不支援 ssh 上傳了，最近則找到了中國產的服務：https://coding.net/ 、https://ide.coding.net 。

以下將介紹怎麼把 github 上的項目 clone 到 coding 上。

<!-- more -->

---

<!-- toc -->

- [當時的環境](#當時的環境)
- [步驟](#步驟)
	- [在 coding 的 webIDE 安裝 hexo](#在-coding-的-webide-安裝-hexo)
	- [在 coding 的 webIDE 添加 git 配置訊息](#在-coding-的-webide-添加-git-配置訊息)
	- [在 coding 的 webIDE 生成密鑰、查看密鑰](#在-coding-的-webide-生成密鑰-查看密鑰)
	- [將密鑰貼到 coding 的 ssh 設定](#將密鑰貼到-coding-的-ssh-設定)
	- [從 github 上 clone 到 coding 上](#從-github-上-clone-到-coding-上)

<!-- tocstop -->

---

# 當時的環境

- 已經有 github 帳號，上面有 blog_hexo 的項目
- 已經有 coding 帳號，已經開好 blog_hexo 項目

---

# 步驟

## 在 coding 的 webIDE 安裝 hexo

```
sudo npm install -g hexo-cli
```

* [Hexo 在两台电脑间的操作流程 | sufaith](http://sufaith.com/2016/02/27/Hexo%E8%BF%81%E7%A7%BB/)


## 在 coding 的 webIDE 添加 git 配置訊息

```
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```


## 在 coding 的 webIDE 生成密鑰、查看密鑰

生成密鑰

```ssh
ssh-keygen -C "xxxxxxxxx@gmail.com"
```

查看 .ssh 底下檔案

```
ls -al ~/.ssh
```
* [Checking for existing SSH keys - User Documentation](https://help.github.com/articles/checking-for-existing-ssh-keys/)x

查看密鑰

```ssh
cat /home/coding/.ssh/id.pub
```
gedit 可能也可以看

- [上传本地代码到 github 上 - 简书](http://www.jianshu.com/p/3c8629ca00eb)

## 將密鑰貼到 coding 的 ssh 設定


- https://coding.net/user/account/setting/keys

## 從 github 上 clone 到 coding 上

```git
git clone git@github.com:ayugioh2003/hexo_blog.git
```
