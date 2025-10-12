---
title           : "基本設定"
date            : 2025-10-10T13:30:10+08:00
lastmod         : 2025-10-10T13:30:10+08:00
slug            : "basic-config"
isCJKLanguage   : true

description     : "本文將說明安裝好 Neso 佈景主題後，接下來需要準備的一些基本設定。"
summary         : "本文將說明安裝好 Neso 佈景主題後，接下來需要準備的一些基本設定。"
keywords        : ["設定教學", "hugo.toml", "favicon", "Tailwind", "Hugo", "Markdown", "Theme", "佈景主題", "Neso", "hugo-neso"]
tags            : ["hugo.toml", "設定", "Favicon"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
      hidden_in_single: true

---


如果你的 Hugo 專案是全新狀態 (剛透過 {{< highlight shell "hl_inline=true" >}}hugo new site{{< /highlight >}} 指令製作出來)，一開始它為你準備的 hugo.toml 全站設定檔只會含有以下內容：

```toml
baseURL = 'https://example.org/'
languageCode = 'en-us'
title = 'My New Hugo Site'
```

如果你的 Hugo 專案已經設定過、使用一段時間，那麼裡面可能會有其他你自行添加的設定。

無論如何，有些設定是 Neso 佈景主題**必備**的，請閱讀以下的說明，在 hugo.toml 內補上或修改所提到的設定參數。


---

## 必要 (與推薦的) 設定

以下的設定確保佈景主題的正確運作 (有些你可能已經在安裝佈景主題時設定過了)：

```toml
# 一般
# --------------------------------

# 必要：你的網站頂層 URL
baseURL = "https://example.org/"
# 必要：你的網站主要語系
languageCode = "zh-tw"
# 必要：你的網站名稱
title = "我的 Hugo 網站"

# 必要：選擇佈景主題
# 如果是透過 Hugo Module 安裝佈景主題，此項可移除
theme = "hugo-neso"


# 建置
# --------------------------------

[minify]
  # 推薦：壓縮輸出的原始碼，有助於頁面載入速度
  minifyOutput = true

# 必要：Tailwind 整合 – 開始
[build]
  [build.buildStats]
    enable = true
  [[build.cachebusters]]
    source = 'assets/notwatching/hugo_stats\.json'
    target = 'css'
  [[build.cachebusters]]
    source = '(postcss|tailwind)\.config\.js'
    target = 'css'
[module]
  [[module.mounts]]
    source = 'assets'
    target = 'assets'
  [[module.mounts]]
    disableWatch = true
    source = 'hugo_stats.json'
    target = 'assets/notwatching/hugo_stats.json'
# 必要：Tailwind 整合 – 結束
  
  # 必要 (如果是透過 Hugo Module 安裝佈景主題)：引入佈景主題
  # 如果是透過其他方式安裝佈景主題，請移除此項
  [[module.imports]]
    path = "github.com/babeneso/hugo-neso"


# Markdown
# --------------------------------

[markup]
  [markup.goldmark]
    [markup.goldmark.parser]
      # 推薦：不要把 <img> 包在 <p> 裡面 (佈景主題已設好適當邊距)
      wrapStandAloneImageWithinParagraph = false

      [markup.goldmark.parser.attribute]
        # 必要：解析區塊元素的屬性選項
        block = true

    [markup.goldmark.renderer]
      # 推薦：可在 Markdown 內使用 HTML
      unsafe = true

  [markup.highlight]
    # 必要：讓程式碼區塊使用 CSS class，以便語法上色
    noClasses = false

  # 推薦：目次層級設定
  [markup.tableOfContents]
    startLevel = 2
    endLevel = 3
```


---

## 其他重要設定

以下列出的是你接下來進一步自訂佈景主題時將碰到的設定，可以不用立刻處理，但此處列出相關的說明。


### Favicon

在下列位置放置 {{< highlight text "hl_inline=true" >}}ICO{{< /highlight >}} 和 {{< highlight text "hl_inline=true" >}}SVG{{< /highlight >}} 版本的 favicon：

- {{< highlight text "hl_inline=true" >}}static/favicon.ico{{< /highlight >}} (推薦 64×64)
- {{< highlight text "hl_inline=true" >}}assets/favicon.svg{{< /highlight >}}

如果你放置的位置、檔名、副檔名都完全如上所示，它們將立即生效、並自動幫你嵌入網頁的 {{< highlight html "hl_inline=true" >}}<head>{{< /highlight >}} 標籤內。

如果你想使用其他檔名、或放置在其他位置當然也可以，請參閱[品牌設定]({{% ref "Params - Site/#branding" %}})。


### 輸出

如果你打算提供 RSS 供訪客訂閱 (Hugo 預設開啟，相關[設定 1]({{% ref "Params - Site/#general-settings" %}})、相關[設定 2]({{% ref "Params - Site/#list-settings" %}}))、使用[站內搜尋]({{% ref "Pages and Menu Setup/#search" %}})功能，那麼你將需要修改下列設定：

```toml
# 輸出
# --------------------------------

[outputs]
  home = ["html", "rss", "json"]
  # 其他輸出設定...
```


### 主選單

設定網站導航列的[主選單]({{% ref "Pages and Menu Setup/#menu-setup" %}})時，你將碰到這些設定：

```toml
# 主選單
# --------------------------------

[menus]
  [[menus.main]]
    identifier = 'posts'
    name       = '文章'
    pageRef    = '/posts'
    weight     = 10
  [[menus.main]]
    identifier = 'tags'
    name       = '標籤'
    pageRef    = '/tags'
    weight     = 20
  # 其他主選單項目...
```


### 其他佈景主題選項

Neso 佈景主題提供許多[額外選項]({{% ref "Params - Site" %}})，它們將來都會集中列在 `[params.neso]` 表頭下：

```toml
# 參數
# --------------------------------

[params]
  [params.neso]
  # Neso 佈景主題設定...
```
