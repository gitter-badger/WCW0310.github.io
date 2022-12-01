---
title: Hexo Note 01：常用 Hexo 指令
date: 2022-11-29 10:26:27
tags:
- Hexo
- Learning
categories:
- [Hexo, Learning]
---

## 前言

單純記錄我真的有用到的 Hexo 指令，並無其他厲害的延伸用法，真要查指令 [官方文件](https://hexo.io/zh-tw/docs/) 永遠是最好的選擇。



## 初始化 blog 專案

```sh
$ hexo init <folder>
$ cd <folder>
$ npm install
```

1. hexo 建立專案 (一個新的網站)

2. 進入專案資料夾

3. npm 安裝必要的依賴檔案 (從 git clone 時也要記得這步)



## 建立新文章

```sh
$ hexo new [layout] <title>
```



## 本地預覽

```sh
$ hexo server
```

啟動伺服器，[預設網址](http://localhost:4000/)：`http://localhost:4000/`。

啟動後 command line 會提示需要按 Ctrl + C 結束 Server 才能繼續使用：

```sh
INFO  Start processing
INFO  Hexo is running at http://localhost:4000/ . Press Ctrl+C to stop.
```

**註：**我在 Windows 11 使用 Git Bash 都無法用 Ctrl + C 來結束 Server，都要用工作管理員把 Node.js JavaScript Runtime 強制結束工作...



## 快速部署

```sh
$ hexo clean && hexo deploy
```

clean：清除快取檔案 (db.json) 和已產生的靜態檔案 (public)

deploy：部署 Blog 網站。



## 結語

我真的只會用到這四種功能的最基礎指令...
