---
title: Hexo Blog 01：使用 Hexo 迅速在 GitHub Pages 展開 Blog 旅程
date: 2022/11/23 00:00:00
tags:
- Hexo
- Learning
categories:
- [Hexo, Learning]
---

## 前言

自從成為碼農後已經用 [Markdown](https://markdown.tw) 做了很久的筆記，之前聽朋友說 [Hexo](https://hexo.io/zh-tw/) 能直接把 Markdown 檔案變成 Blog 文章，想想就覺得心動，這樣日常做筆記之餘還能有所產出。感覺做筆記時心態會更認真，不過原本只是重點搬運工，之後還要思考文章的可讀性，以及如何才能幫助到真正需要這些資訊的人等等。



## 目標

* 使用 Hexo Blog 框架將 Markdown 文件輸出成精美 Blog
* 以 [GitHub Pages](https://pages.github.com) 作為 Blog 網站的架設平台



## 建置流程

都是按照以下官方文檔進行操作：

[Hexo 文件](https://hexo.io/zh-tw/docs/)

[在 GitHub Pages 上部署 Hexo](https://hexo.io/zh-tw/docs/github-pages)

不過官方文檔有些步驟或補充說明讓我有點混淆，本文作為筆記會盡量記錄所有必須的操作步驟。



### 前置需求

* 安裝 [git](https://git-scm.com/)

   我的版本：git version 2.24.1.windows.2

* 安裝 [Node.js](https://nodejs.org/en/)

   我的版本：v18.12.1

* 註冊 [GitHub](https://github.com/)

所有安裝操作盡量以最新穩定版本為主。



### 主要操作

1. 安裝 Hexo

   ```sh
   npm install -g hexo-cli
   ```

   我的版本：

   ```
   hexo: 6.3.0
   hexo-cli: 4.3.0
   os: win32 10.0.19045
   node: 18.12.1
   v8: 10.2.154.15-node.12
   uv: 1.43.0
   zlib: 1.2.11
   brotli: 1.0.9
   ares: 1.18.1
   modules: 108
   nghttp2: 1.47.0
   napi: 8
   llhttp: 6.0.10
   openssl: 3.0.7+quic
   cldr: 41.0
   icu: 71.1
   tz: 2022b
   unicode: 14.0
   ngtcp2: 0.8.1
   nghttp3: 0.7.0
   ```



2. 建立 Hexo Blog 專案

   ```sh
   hexo init <folder>
   cd <folder>
   npm install
   ```

   `<folder>` 換成自己想要的 Blog 專案名稱，我是直接學 [官網首頁](https://hexo.io/zh-tw/) 的範例取為 `blog`。



3. 於 GitHub 建立名為 **username.github.io** 的儲存庫

   `username` 為 GitHub 使用者名稱，請自行替換。

   這樣其實是建立了一個 GitHub Pages。



4. 將 Hexo Blog 專案 push 至 GitHub Pages 儲存庫的預設分支

   最好先將 Hexo Blog 專案內的 `.git` 資料夾刪除，這樣就能直接照 GitHub 推薦方式 push，也不會遇到 branch 名稱不同的錯誤：

   ```sh
   git init
   git add .
   git commit -m "first commit"
   git branch -M main
   git remote add origin https://github.com/<username>/<username>.github.io.git
   git push -u origin main
   ```
   
   由於不知何時起 GitHub 要求以 token 執行 push 操作，這裡可能會遇到一些 GitHub 登入問題，在此提供之前踩坑後覺得有用的資訊：
   
   [Creating a personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)
   
   [GitHub - Personal Access Token & SourceTree](https://blog.csdn.net/caroline_wendy/article/details/119736105)



5. 安裝 [hexo-deployer-git](https://github.com/hexojs/hexo-deployer-git)

   ```sh
   npm install hexo-deployer-git --save
   ```

   我的版本：v3.0.0
   
   Hexo 專門用來以 git 部署的工具



6. 更改 Hexo Blog 專案根目錄中 `_config.yml` 的 `deploy:` 部分

   ```yaml
   deploy:
     type: git
     repo: https://github.com/<username>/<project>
     # example, https://github.com/hexojs/hexojs.github.io
     branch: gh-pages
   ```

   這樣 Hexo 生成 Blog 畫面檔案後會 push 至 gh-pages



7. 執行快速部署指令

   ```sh
   hexo clean && hexo deploy
   ```



8. 在 GitHub 專案頁面中設定 blog 畫面部署的 branch

   進入 Settings (頁面上方) > Pages (頁面左方)

   將 Branch 設為 gh-pages，點擊 Sava 儲存設定

   這樣 GitHub Pages 才會將 gh-pages 中的內容作為網頁部署



8. 瀏覽 `<GitHub 用戶名>.github.io` 檢查你的 Blog 能否運作

   可能需要等待一下子



## 阻礙

雖然成功架設了 Blog，不過坑還是很大，在此列出接下來需要解決的問題：

* 改變頁面主題：[Hexo Themes](https://hexo.io/themes/)
* 留言功能
* 讓 Blog 更容易被搜尋：[Google Search Console](https://search.google.com/search-console/welcome)
* 加入廣告 Plugin：[Google Adsense](https://www.google.com/adsense/start/#/?modal_active=none)
* 讓 Blog 可追蹤流量：[Google Analytics](https://analytics.google.com/analytics/web/)



## 結語

2022/11/23 成功建置[本 Blog](https://wcw0310.github.io)

如果你平常也在用 Markdown 做些技術筆記，不妨一起嘗試 Hexo，讓連自己都很少看的筆記成為 Blog 文章來服務網路上遇到同樣問題的人們吧！

願各位付出的精力都能結出甜美的果實。
