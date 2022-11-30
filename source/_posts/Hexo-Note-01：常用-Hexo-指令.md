---
title: Hexo Note 01：常用 Hexo 指令
date: 2022-11-29 10:26:27
tags:
- Hexo
- Learning
categories:
- [Hexo, Learning]
---

## 初始化 blog 專案

```sh
$ hexo init <folder>
$ cd <folder>
$ npm install
```

hexo 建立專案 (一個新的網站)

進入專案資料夾

npm 安裝必要檔案 (從 git clone 時也要記得這步)



## 建立新文章

```sh
$ hexo new [layout] <title>
```



## 本地預覽

```sh
$ hexo server
```

啟動伺服器，[預設網址](http://localhost:4000/)：`http://localhost:4000/`。



## 快速部署

```sh
$ hexo clean && hexo deploy
```

清除快取檔案 (db.json) 和已產生的靜態檔案 (public)，並部署網站。
