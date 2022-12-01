---
title: Hexo Debug 01：Hexo 文章 title 含特殊或功能字元引發錯誤
date: 2022-11-29 12:29:00
tags:
- Hexo
- Error
categories:
- [Hexo, Error]
---



## 前言

想要在文章標題開頭用些分類性標記，第一時間想到的是用 `[]` 包裹關鍵字，沒想到陸續發生了以下兩種錯誤，還好都還算是能繞開，不影響其他使用體驗。

<!-- more -->



## 情境一

### 流程

1. 修改文章 title，使其包含 `[` 與 `]` 字元

2. 使用本地預覽指令：

   ```sh
$ hexo server
   ```

3. 無法正常顯示頁面

### log

```sh
INFO  Validating config
INFO  Start processing
ERROR Process failed: _posts/[Hexo]-常用-Hexo-指令.md
YAMLException: bad indentation of a mapping entry (1:15)

 1 | title: [Hexo] 常用 Hexo 指令
-------------------^
 2 | date: 2022-11-29 10:26:27
 3 | tags:
    at generateError (D:\blog\node_modules\js-yaml\lib\loader.js:183:10)
    at throwError (D:\blog\node_modules\js-yaml\lib\loader.js:187:9)
    at readBlockMapping (D:\blog\node_modules\js-yaml\lib\loader.js:1182:7)
    at composeNode (D:\blog\node_modules\js-yaml\lib\loader.js:1441:12)
    at readDocument (D:\blog\node_modules\js-yaml\lib\loader.js:1625:3)
    at loadDocuments (D:\blog\node_modules\js-yaml\lib\loader.js:1688:5)
    at Object.load (D:\blog\node_modules\js-yaml\lib\loader.js:1714:19)
    at parseYAML (D:\blog\node_modules\hexo-front-matter\lib\front_matter.js:69:23)
    at parse (D:\blog\node_modules\hexo-front-matter\lib\front_matter.js:50:12)
    at D:\blog\node_modules\hexo\lib\plugins\processor\post.js:93:18
    at tryCatcher (D:\blog\node_modules\bluebird\js\release\util.js:16:23)
    at Promise._settlePromiseFromHandler (D:\blog\node_modules\bluebird\js\release\promise.js:544:35)
    at Promise._settlePromise (D:\blog\node_modules\bluebird\js\release\promise.js:604:18)
    at Promise._settlePromise0 (D:\blog\node_modules\bluebird\js\release\promise.js:649:10)
    at Promise._settlePromises (D:\blog\node_modules\bluebird\js\release\promise.js:729:18)
    at Promise._fulfill (D:\blog\node_modules\bluebird\js\release\promise.js:673:18)
    at PromiseArray._resolve (D:\blog\node_modules\bluebird\js\release\promise_array.js:127:19)
    at PromiseArray._promiseFulfilled (D:\blog\node_modules\bluebird\js\release\promise_array.js:145:14)
    at PromiseArray._iterate (D:\blog\node_modules\bluebird\js\release\promise_array.js:115:31)
    at PromiseArray.init [as _init] (D:\blog\node_modules\bluebird\js\release\promise_array.js:79:10)
    at Promise._settlePromise (D:\blog\node_modules\bluebird\js\release\promise.js:601:21)
    at Promise._settlePromise0 (D:\blog\node_modules\bluebird\js\release\promise.js:649:10)
```

### 解決方法

將 md. 檔案最上方 front_matter 中 title 的內容以引號包裹可避免發生此錯誤：

```markdown
title: '[Hexo] title 包含特殊字元引發錯誤'
```



## 情境二

### 流程

1. 使用建立新文章指令建立 title 包含 `[` 與 `]` 字元的文章：

   ```sh
$ hexo new '[Hexo] title 包含特殊字元引發錯誤'
   ```

2. 文章建立失敗

### log

```sh
INFO  Validating config
FATAL Something's wrong. Maybe you can find the solution here: https://hexo.io/docs/troubleshooting.html
YAMLException: bad indentation of a mapping entry (1:15)

 1 | title: [Hexo] title 包含特殊字元引發錯誤
-------------------^
 2 | date: 2022-11-29 04:11:40
 3 | tags:
    at generateError (D:\blog\node_modules\js-yaml\lib\loader.js:183:10)
    at throwError (D:\blog\node_modules\js-yaml\lib\loader.js:187:9)
    at readBlockMapping (D:\blog\node_modules\js-yaml\lib\loader.js:1182:7)
    at composeNode (D:\blog\node_modules\js-yaml\lib\loader.js:1441:12)
    at readDocument (D:\blog\node_modules\js-yaml\lib\loader.js:1625:3)
    at loadDocuments (D:\blog\node_modules\js-yaml\lib\loader.js:1688:5)
    at load (D:\blog\node_modules\js-yaml\lib\loader.js:1714:19)
    at D:\blog\node_modules\hexo\lib\hexo\post.js:282:63
    at tryCatcher (D:\blog\node_modules\bluebird\js\release\util.js:16:23)
    at Promise._settlePromiseFromHandler (D:\blog\node_modules\bluebird\js\release\promise.js:547:31)
    at Promise._settlePromise (D:\blog\node_modules\bluebird\js\release\promise.js:604:18)
    at Promise._settlePromise0 (D:\blog\node_modules\bluebird\js\release\promise.js:649:10)
    at Promise._settlePromises (D:\blog\node_modules\bluebird\js\release\promise.js:729:18)
    at Promise._fulfill (D:\blog\node_modules\bluebird\js\release\promise.js:673:18)
    at Promise._settlePromise (D:\blog\node_modules\bluebird\js\release\promise.js:617:21)
    at Promise._settlePromise0 (D:\blog\node_modules\bluebird\js\release\promise.js:649:10)
    at Promise._settlePromises (D:\blog\node_modules\bluebird\js\release\promise.js:729:18)
    at Promise._fulfill (D:\blog\node_modules\bluebird\js\release\promise.js:673:18)
    at D:\blog\node_modules\bluebird\js\release\nodeback.js:42:21
    at D:\blog\node_modules\nunjucks\src\environment.js:41:5
    at RawTask.call (D:\blog\node_modules\asap\asap.js:40:19)
    at flush (D:\blog\node_modules\asap\raw.js:50:29)
```

### 解決方法

我目前只能手動建立新 .md 檔案，並貼上模板，md. 檔案中 title 的內容依然需要以引號包裹才可避免發生其他錯誤。



## 結語

推測是 Hexo 在解析文章 front_matter 時是視為 yaml，遇到語法相關字元會有其預設的規範。遇到類似問題時都先試試用引號包裹，程式應該會將引號包裹內容當成字串處理。

不過最後我是選擇不使用特殊字元了，畢竟也不是很美觀 XD。



## 參考資料

自己試的，看 log 猜的
