---
title           : "快速開始"
date            : 2025-10-11T06:21:30+08:00
lastmod         : 2025-10-11T06:21:30+08:00
slug            : "get-started"
isCJKLanguage   : true

description     : "教你如何在幾個步驟內完成安裝 Neso 佈景主題、並立即使用，同時了解 Hugo 的基本運作方式。"
summary         : "教你如何在幾個步驟內完成安裝 Neso 佈景主題、並立即使用：先認識 hugo.toml 與 Front Matter，再依序完成安裝、發表文章與基本設定。"
keywords        : ["設定教學", "hugo.toml", "Front Matter", "Hugo", "Markdown", "Theme", "佈景主題", "Neso", "hugo-neso"]
tags            : ["hugo.toml", "Front Matter", "設定", "安裝"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
      hidden_in_single: true
---

## 歡迎！

本頁將幫助你：
1. 了解 **hugo.toml** 與 **Front Matter**：它們會在 Hugo 內頻繁被提及、使用。
2. 掌握本文件的**格式慣例**：全站設定用 TOML，Front Matter 用 YAML。
3. 依序完成**安裝佈景主題** → **發表文章** → **基本與細部設定**三步驟。


---

## 什麼是 hugo.toml

1. hugo.toml 是**全站層級的設定檔**，涵蓋語系、導覽選單、佈景主題、進階功能等。
2. Hugo [內建的選項](https://gohugo.io/configuration/all/)多是架構相關 (而非外觀)，為此 Neso 佈景主題擴充了許多選項供你自訂 (例如 Tailwind 整合、語法上色、選單⋯⋯等等)。
3. 早期常見的檔名是 config，如 config.toml；現在建議在專案根目錄使用單一檔案 **hugo.toml**。
4. [TOML](https://zh.wikipedia.org/zh-tw/TOML) 是一種常用在設定檔的書寫格式，本文件涉及**全站設定**一律採 **TOML** 示範說明。

TOML 長這樣：

```toml
baseURL = "https://example.org/"
languageCode = "zh-tw"
title = "我的網站標題"

# 例：選用主題
theme = "hugo-neso"
```

> [!NOTE]
> 關於更完整的必填與建議設定，文件後續都會提供詳細說明與連結。


---

## 什麼是 Front Matter

1. Front Matter 是每篇內容 (Markdown) **檔頭的中繼資料**，位於檔案最上方，用來描述標題、日期、分類、摘要等。
2. Hugo [內建的選項](https://gohugo.io/content-management/front-matter/#fields)較為基本，為此 Neso 佈景主題擴充了許多選項供你自訂 (例如 封面圖、目次、分享功能⋯⋯等等)。
3. Hugo 支援 **TOML**、**YAML**、**JSON** 三種語法。
4. 如同前面提到的 TOML，[YAML](https://zh.wikipedia.org/zh-tw/YAML) 只是另一種書寫格式，本文件涉及 **Front Matter** 一律採 **YAML** 示範說明。

YAML Front Matter 長這樣：

```yaml
---
title       : "文章標題"
date        : 2025-10-11T12:00:00+08:00
description : "這是一段適合 SEO 的簡短描述"
summary     : "列表頁會顯示的摘要"
tags        : ["隨筆", "心得"]
---
```

> [!NOTE]
> 關於其他 Neso 額外擴充、讓你的內容更豐富的 Front Matter 選項，文件後續都會提供詳細說明與連結。


---

## 從這裡開始

請依下列順序完成設定；每一步都有對應的教學頁面。

1. **安裝佈景主題**  
    前往：**[安裝佈景主題]({{% ref "Theme Installation" %}})**  
    目的：將 Neso 與 Tailwind CSS 正確接入你的 Hugo 專案。

2. **發表第一篇文章**  
    前往：**[建立文章]({{% ref "Create a Post" %}})**  
    目的：學會以「文章包 (leaf bundle)」管理文章與素材、並套用建議的 Front Matter。

3. **完成基本設定**  
    前往：**[基本設定]({{% ref "Basic Config" %}})**  
    目的：調整必要與推薦的 hugo.toml 參數，使網站行為與樣式正確。


---

## 接下來你可以……

- 瀏覽其他主題文件以細部調整：例如**頁面與選單設定**、**短碼 (Shortcodes)**、**程式碼語法上色**、**客製化樣式**、**評論區**等。  
- 主選單的「[使用說明]({{% ref "/docs" %}})」可看到完整文件清單，你也可以善用 [Tag]({{% ref "/tags" %}}) 查找、[搜尋]({{% ref "/search" %}})功能等。
- 若需要完整的設定清單，請參考：**[全站參數總表]({{% ref "Params - Site" %}})** 與 **[Front Matter 參數總表]({{% ref "Params - Front Matter" %}})**。
