---
title: Hexo Blog 02：更換 Hexo 主題，初探 NexT
date: 2022-11-29 15:31:18
tags:
- Hexo
- Learning
categories:
- [Hexo, Learning]
---

## 前言

{% post_link Hexo-Blog-01：使用-Hexo-迅速在-GitHub-Pages-展開-Blog-旅程 先前的文章 %}  最後列了一些使用 Hexo Blog 要解決的問題，最重要的應該就是更換主題了，因為要擴充功能什麼的都是透過更改主題的設定實踐。

人工在網上繞了圈後，發現最多人拿來作練習的主題是 [NexT](https://theme-next.js.org/) ，為了少走彎路，我首次換的主題也決定是它了，然而我發現 NexT 官方有新的推薦用法，先人的文章卻都還沒採用，因此我決定照官方推薦方式實踐。



## 目標

* 將預設的 landscape 主題換成 NexT
* 依照官方推薦的 [Alternate Theme Config](https://theme-next.js.org/docs/getting-started/configuration.html) 方式來設定 NexT 的 config

<!-- more -->



## 建置流程

1. 在 Hexo Blog 專案內安裝 NexT 主題：

   ```sh
   $ npm install hexo-theme-next
   ```
   
   我的版本：v8.13.2



2. 設置 Hexo Blog 專案根目錄中的 `_config.yml` 檔案：

   將 `theme:` 的值由原先的 `landscape` 改成 `next`：

   ```yaml
   # Extensions
   ## Plugins: https://hexo.io/plugins/
   ## Themes: https://hexo.io/themes/
   theme: next #landscape
   ```



3. 複製 NexT 原始 config 的內容至專案根目錄：

   在 Hexo Blog 專案內執行：

   ```sh
   $ cp node_modules/hexo-theme-next/_config.yml _config.next.yml
   ```

   **註：**會生成 `_config.next.yml` 檔案，它將作為本專案中 NexT 主題的 config，Hexo 會優先讀取此檔案中的設定。
   
   **註：**之後要自定義主題設定只會修改 `_config.next.yml`，而不會直接改動任何 NexT 的檔案，這就是目前官方推薦的使用方式，這樣 NexT 之後做版本升級時，使用者的改動才不會影響程序，或是自定義的內容被覆蓋而遺失。



4. 重新部署 Blog：

   ```sh
   $ hexo clean && hexo deploy
   ```



5. 瀏覽 Blog 檢查主題是否更新



## 結語

就是基本的下載跟修改設定檔，不過看到更新後的 Blog 還是有些發現：

* 缺了各文章瀏覽次數
* 缺了文章字數統計

關卡還是滿多的，繼續加油吧！
