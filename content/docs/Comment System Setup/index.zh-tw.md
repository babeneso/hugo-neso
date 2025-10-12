---
title           : "加入留言 / 評論功能"
date            : 2025-10-09T19:57:51+08:00
lastmod         : 2025-10-09T19:57:51+08:00
slug            : "comment-setup"
isCJKLanguage   : true

description     : "Hugo 雖是靜態網站生成器，但還是能透過各種供應商、免費服務來讓你的網站具備留言 / 評論系統。"
summary         : "Hugo 雖是靜態網站生成器，但還是能透過各種供應商、免費服務來讓你的網站具備留言 / 評論系統。"
keywords        : ["Hugo", "評論區", "留言", "迴響", "Disqus", "Theme", "Neso", "hugo-neso"]
tags            : ["hugo.toml", "評論區", "設定"]

params:
  neso:
    cover:
      image           : "cover.png"
      hidden_in_single: true
---

## 設定

請先參閱 Hugo [官方文件](https://gohugo.io/content-management/comments/)，了解如何整合評論系統 (官方目前支援 Disqus 快速設定，但也有列出其他主流選擇，可方便查閱)。

當你準備好插入評論系統所需的 template 原始碼時，到 Neso 的 GitHub Repo 下載 [comments.html](https://github.com/babeneso/hugo-neso/blob/main/layouts/_partials/content/comments.html)：

在裡面安插好你要的原始碼後，放到你 Hugo 專案目錄下的：{{< highlight text "hl_inline=true" >}}layouts/_partials/content/comments.html{{< /highlight >}}。

未見該目錄的話請自行建立。
