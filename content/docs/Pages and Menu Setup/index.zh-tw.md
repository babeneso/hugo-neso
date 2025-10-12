---
title           : "準備主要頁面、主選單"
date            : 2025-10-09T20:49:00+08:00
lastmod         : 2025-10-09T20:49:00+08:00
slug            : "pages-menu-setup"
isCJKLanguage   : true

description     : "Neso 佈景主題提供標籤與分類頁、內容彙整功能 (Archives)，也整合了搜尋機制，參閱本頁說明，以了解如何設定這些頁面及網站主選單。"
summary         : "Neso 佈景主題提供標籤與分類頁、內容彙整功能 (Archives)，也整合了搜尋機制，參閱本頁說明，以了解如何設定這些頁面及網站主選單。"
keywords        : ["Hugo", "設定教學", "主選單", "分類", "標籤", "Tag", "搜尋", "Archives", "Theme", "Neso", "hugo-neso"]
tags            : ["hugo.toml", "主選單", "分類功能", "標籤功能", "搜尋頁", "內容彙整頁", "設定"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
      hidden_in_single: true
---

> [!TIP]
> 網站首頁的設置方法另有詳細說明，請[見此]({{% ref "Params - Site/#homepage" %}})。

> [!NOTE]
> 作者習慣在全站設定用 **TOML** 格式、在 Front Matter 用 **YAML** 格式，請留意，並視需要自行使用格式轉換工具。

---

## 搜尋功能 {id="search"}

在你的全站設定檔 hugo.toml 內，於 {{< highlight toml "hl_inline=true" >}}[outputs]{{< /highlight >}} 表頭下的 {{< highlight toml "hl_inline=true" >}}home = [...]{{< /highlight >}} 字串陣列裡加入 {{< highlight toml "hl_inline=true" >}}"json"{{< /highlight >}} 項：

```toml
[outputs]  #`outputs` 表頭位在 toml 頂層
  home = ["html", "rss", "json"]  # 讓 Hugo 輸出 JSON 格式
```

這個設定會讓 Hugo 以 JSON 格式在根目錄輸出你網站的內容，以便讓搜尋功能的 JavaScript 使用。關於輸出格式的詳情，見 Hugo [官方文件](https://gohugo.io/configuration/outputs/)。

接著在你的 Hugo 專案裡，於 {{< highlight text "hl_inline=true" >}}content/{{< /highlight >}} 目錄下建立 {{< highlight text "hl_inline=true" >}}search.md{{< /highlight >}}，並加入下列 Front Matter：

```yaml {hl_lines="2"}
---
layout          : "search"  # 此為必要
title           : "搜尋"
description     : "用鍵盤上/下鍵選定搜尋結果、Enter 鍵前往閱讀。"
---

<!-- 雖然可能顯得多餘，但有需要的話，你可以在此正文區域寫 Markdown -->
```

> [!IMPORTANT]
> 檔案位置必須是 {{< highlight text "hl_inline=true" >}}content/search.md{{< /highlight >}} (位於頂層)。

> [!TIP]
> 如果你需要多語系搜尋頁，可為每個語言分別建立：
> 
> ```text
> content/
> ├── search.md     # 預設語言
> ├── search.ja.md  # 其他語系
> └── ...
> ```


---

## 內容彙整頁 (Archives)

在你的 Hugo 專案裡，於 {{< highlight text "hl_inline=true" >}}content/{{< /highlight >}} 目錄下建立 {{< highlight text "hl_inline=true" >}}archives.md{{< /highlight >}}，並加入下列 Front Matter：

```yaml {hl_lines="2"}
---
layout          : "archives"  # 此為必要
title           : "內容彙整"
description     : "你可以在這裡找到過往的所有內容。"
---

<!-- 雖然可能顯得多餘，但有需要的話，你可以在此正文區域寫 Markdown -->
```

> [!TIP]
> 如果你需要多語系搜尋頁，可為每個語言分別建立：
> 
> ```text
> content/
> ├── archives.md     # 預設語言
> ├── archives.ja.md  # 其他語系
> └── ...
> ```


---

## 文章分類、標籤

寫文章時，在你的 Front Matter 內使用 {{< highlight yaml "hl_inline=true" >}}categories = [...]{{< /highlight >}} 與 {{< highlight yaml "hl_inline=true" >}}tags = [...]{{< /highlight >}}，即可為文章分類和打標籤：

```yaml {hl_lines="6-7"}
---
title           : "文章標題"
date            : 2025-08-14T01:01:00+08:00
description     : "SEO 描述"
summary         : "內容摘要或總結"
categories      : ["某文章分類", "另一個分類"]
tags            : ["標籤a", "標籤b"]

params:
  neso:
  # 其他設定略...
---
```

接著參閱下面的「[設定主選單](#menu-setup)」，將分類頁或標籤頁加入主選單即可 (你也可以不要加)。

> [!NOTE]
> `tags` 和 `categories` 只是 Hugo 為你預設好的兩個「taxonomies」，你還能自訂其他內容的分類方式，這個機制在 Hugo 就稱為 [Taxonomy](https://gohugo.io/configuration/taxonomies/)。


---

## 設定主選單 {id="menu-setup"}

你可以在 Hugo 官方文件的 [Menu 說明](https://gohugo.io/configuration/menus/)了解關於選單設定的細節，以下示範如何在主選單內加入上面提到的標籤與分類頁、搜尋頁、內容彙整頁。

在你的全站設定檔 hugo.toml 內加入下列設定：

```toml
[menus]  #`menus` 表頭位在 toml 頂層
  [[menus.main]]
    identifier = "posts"   # 識別符
    name       = "文章"     # 顯示在選單的名稱
    pageRef    = "/posts"  # 你的內容 Section
    weight     = 10        # 排序 (越小越前)
  [[menus.main]]
    identifier = "tags"
    name       = "標籤"
    pageRef    = "/tags"  # 你的 Taxonomy：tags、categories 等
    weight     = 20
  [[menus.main]]
    identifier = "categories"
    name       = "分類"
    pageRef    = "/categories"  # 你的 Taxonomy：tags、categories 等
    weight     = 30
  [[menus.main]]
    identifier = "archives"
    name       = "內容彙整"
    pageRef    = "/archives"  # 內容彙整頁
    weight     = 40
  [[menus.main]]
    identifier = "search"
    name       = "搜尋"
    pageRef    = "/search"  # 搜尋頁
    weight     = 50
  [[menus.main]]
    identifier = "github"
    name       = "GitHub"
    url        = "https://github.com/babeneso"  # 站外連結
    weight     = 60
```

> [!IMPORTANT]
> 雖然 `name` 就足以讓 Hugo 辨識選單項目，仍*強烈建議*設置 [`identifier`](https://gohugo.io/configuration/menus/#identifier) 識別符。
> 
> **站內連結**請用 [`pageRef`](https://gohugo.io/configuration/menus/#pageref)，並指向頁面的[邏輯路徑](https://gohugo.io/quick-reference/glossary/#logical-path)，避免使用 `url`。
> 
> **站外連結**才適合使用 `url`，而非 `pageRef`。

> [!NOTE]
> 如果需要設置多語系的主選單，請參閱 Hugo 官方文件的[說明](https://gohugo.io/content-management/multilingual/#menus)，或是參考此 Demo 網站的 [hugo.toml](https://github.com/babeneso/hugo-neso/blob/demo/hugo.toml) 作為範例。

> [!WARNING] 🚧 TODO
> 我可能需要解釋一下為什麼 /tags 和 /categories 明明沒有建立對應的 MD 檔，Hugo 卻能正常 render 出頁面的原因，日後補上。
