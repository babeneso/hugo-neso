---
title           : "佈景主題參數 (單篇文章)"
date            : 2025-10-06T14:53:12+08:00
lastmod         : 2025-10-06T14:53:12+08:00
draft           : false
slug            : "front-matter-params"
isCJKLanguage   : true

description     : "此處列出佈景主題提供的 Front Matter 參數，控制層面為頁面 UI，以及封面圖片等。"
summary         : "此處列出佈景主題提供的 Front Matter 參數，控制層面為頁面 UI，以及封面圖片等。"
keywords        : ["Hugo", "參數", "設定", "客製化", "Theme", "Neso", "hugo-neso"]
tags            : ["Front Matter", "設定"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
      hidden_in_single: true
---

## 關於 Front Matter

準備 Hugo 的各種頁面和文章時，你可以在檔案裡的 Front Matter 區塊提供後設資料、自訂頁面選項。此主題提供的 Front Matter 參數都巢狀歸在 `neso` 命名空間下，例如，以下是寫在 Markdown 檔案開頭的 YAML 格式 Front Matter：

```yaml
---
title         : "貓貓快樂的一天"
date          : 2025-10-06T14:53:12+08:00
description   : "這是貓貓自己寫的日記，絕無鏟屎官干預。"
# 其他略...
# 以上是 Hugo 本身提供的 Front Matter 欄位 (僅舉一部分為例)

params:
  # 以下是本佈景主題提供的 Front Matter 參數欄位 (僅舉一部分為例)
  neso:
    # 都歸在 `neso` 命名空間下
    author    : "朵貓貓"
    show_toc  : false
    cover:
      # 封面圖選項會再巢狀一層
      image   : "selfie.jpg"
      caption : "貓貓自拍照"
      # 其他略...
---

<!-- 以下是主要的文章/頁面內容 -->
ddddddddddd,,,,,,,,,,,,,,,,,,,,,cfvsssssssszzzz
```

> [!TIP]
> 即使完全不使用佈景主題提供的 `neso` 參數，Hugo 也能順利建置文章，有需要再使用即可。

> [!NOTE]
> 作者習慣在全站設定用 TOML 格式、在 Front Matter 用 YAML 格式，所以本篇說明會以 YAML 示範。

---


## 一般設定

直接寫在 `neso` 下 (注意縮排)：

```yaml {hl_lines=["3-4"]}
params:
  neso:
    show_toc: true      # 設定的鍵、值
    toc_expanded: true  # 設定的鍵、值
    # 下略...
```


### 頁首文章資訊 {id="metadata-settings"}

文章頁首區塊用來顯示發表日期、作者、字數統計⋯⋯等等的後設資料。

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| 鍵名 | 類型 | 說明 |
| --- | :---: | --- |
| `author` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} {{< highlight text "hl_inline=true" >}}String[]{{< /highlight >}} | 作者名稱；只有一人的話可直接給字串，例如 {{< highlight toml "hl_inline=true" >}}"李清照"{{< /highlight >}}，需要顯示多人的話可用字串陣列，例如 {{< highlight toml "hl_inline=true" >}}["蘇洵", "蘇軾", "蘇轍"]{{< /highlight >}} |
| `disable_author` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 在此頁面關閉作者資訊 (注意：此選項僅可用來關閉功能，若[全站設定]({{% relref "Params - Site/#single-metadata" %}})已關，這裡無法覆寫為開) |
| `disable_reading_time` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 在此頁面關閉閱讀時間估計 (注意：此選項僅可用來關閉功能，若[全站設定]({{% relref "Params - Site/#single-metadata" %}})已關，這裡無法覆寫為開) |
| `disable_word_count` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 在此頁面關閉字數統計 (注意：此選項僅可用來關閉功能，若[全站設定]({{% relref "Params - Site/#single-metadata" %}})已關，這裡無法覆寫為開) |
| `canonical_url` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 如果你的文章原本是發表於他處，可以在此欄位填寫原文 URL |
| `canonical_link_text` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 顯示 `canonical_url` 連結時，要在開頭加上的預設字串；例如 {{< highlight text "hl_inline=true" >}}原文發表於{{< /highlight >}} |
| `hide_metadata` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 隱藏整個頁首區塊 |

</div>


### 頁尾功能 {id="footer-settings"}

文章頁尾區塊用來顯示文章標籤、分享按鈕、繼續閱讀上/下篇等功能。

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| 鍵名 | 類型 | 說明 |
| --- | :---: | --- |
| `show_prev_next` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 顯示「上/下一篇」文章，供訪客延伸閱讀 |
| `disable_share` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 在此頁面關閉分享按鈕 (注意：此選項僅可用來關閉功能，若[全站設定]({{% relref "Params - Site/#single-footer" %}})已關，這裡無法覆寫為開) |
| `disable_content_footer` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 隱藏整個頁尾區塊 (注意：此選項僅可用來隱藏區塊，若已在[全站設定]({{% relref "Params - Site/#single-footer" %}})設為隱藏，這裡無法覆寫為顯示) |

</div>


### 其他 {id="other-settings"}

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| 鍵名 | 類型 | 說明 |
| --- | :---: | --- |
| `disable_breadcrumbs` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 在此頁面關閉麵包屑導覽列 (注意：此選項僅可用來關閉功能，若[全站設定]({{% relref "Params - Site/#general-settings" %}})已關，這裡無法覆寫為開) |
| `show_toc` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 顯示內文目次 |
| `toc_expanded` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 預先展開內文目次 |
| `disable_comments` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 在此頁面關閉評論/留言區塊 (注意：此選項僅可用來關閉功能，若[全站設定]({{% relref "Params - Site/#single-general" %}})已關，這裡無法覆寫為開) |
| `exclude_from_search` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 在站內搜尋結果中排除此頁面 |
| `block_indexing` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 將此頁面的 {{< highlight html "hl_inline=true" >}}<meta name="robots">{{< /highlight >}} 設為 `noindex`、`nofollow` |

</div>

---


## 封面圖片

將設定縮排寫在 `neso` 內的 `cover` 下：

```yaml {hl_lines=["5-10"]}
params:
  neso:
    show_toc: true
    # 其他設定略...
    cover:
      image            : "meow.png"
      caption          : "可愛喵"
      alt_text         : "一隻黑貓正在喵喵叫"
      hidden_in_list   : false
      hidden_in_single : false
```

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| 鍵名 | 類型 | 說明 |
| --- | :---: | --- |
| `image` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 圖檔 URL；可寫相對於文章檔案的相對路徑、或是絕對路徑 |
| `caption` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 顯示在封面圖片下方的文字敘述 |
| `alt_text` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 封面圖片的替代文字 |
| `hidden_in_list` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 在文章列表隱藏封面圖片 |
| `hidden_in_single` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 在文章頁面本身隱藏封面圖片 |

</div>
