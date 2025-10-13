---
title           : "佈景主題參數 (全站)"
date            : 2025-10-04T15:06:02+08:00
lastmod         : 2025-10-06T14:52:35+08:00
draft           : false
slug            : "site-params"
isCJKLanguage   : true

description     : "此處列出佈景主題內建的全站參數，控制層面為網站首頁、整體 UI，以及 SEO 等。"
summary         : "此處列出佈景主題內建的全站參數，控制層面為網站首頁、整體 UI，以及 SEO 等。"
keywords        : ["Hugo", "參數", "設定", "客製化", "Theme", "Neso", "hugo-neso"]
tags            : ["hugo.toml", "設定", "Favicon"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
      hidden_in_single: true
---

> [!TIP]
> 主題本身可開箱即用，自帶合理預設值，你一開始可以完全不碰這些設定，等需要的時候再添加。


## 關於全站設定檔

此主題提供的全站參數都巢狀歸在 `params.neso` 命名空間下，也就是說，你在專案根目錄下的 hugo.toml 內應該像這樣寫：

```toml
[params]
  [params.neso]                  # 表頭
    support_theme_author = true  # 設定鍵、值
    [params.neso.home]
      display_mode = "profile"
      # 下略...
```

你也可以依照自己的需求，將設定擋拆分成多個檔案，詳見 [Hugo 官方文件](https://gohugo.io/configuration/introduction/)。

> [!NOTE]
> Hugo 本身也接受 YAML 或 JSON 格式的設定檔，有需要的話，請自行尋找格式轉換工具。

---


## 頂層設定 {id="general-settings"}

表頭：`[params.neso]`。

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| 鍵名 | 類型 | 說明 |
| --- | :---: | --- |
| `time_format` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 用於顯示文章發佈時間的格式，[詳細文件](https://gohugo.io/functions/time/format/) |
| `disable_responsive_menu` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 停用響應式網站主選單 |
| `show_breadcrumbs` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 在頁面上方顯示麵包屑導覽列 (可透過頁面的 [Front Matter]({{% relref "Params - Front Matter/#other-settings" %}}) 單方面關閉) |
| `ext_link_indicator` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 為外連的超連結加上提示 icon |
| `ext_link_no_opener_referrer` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 為外連的超連結 {{< highlight html "hl_inline=true" >}}<a>{{< /highlight >}} 元素加上 `noopener`、`noreferrer` 等 `rel` 屬性值 |
| `ext_link_new_window` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 在新分頁/視窗打開外連的超連結 |
| `show_full_content_in_rss` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 在 [RSS 輸出](https://gohugo.io/configuration/outputs/)內包含內容全文 (預設使用文章 Front Matter 的 `Summary`) |
| `archive_includes_all_sections` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 在 Archives 頁面納入所有 Section 的文章 (預設為 {{< highlight toml "hl_inline=true" >}}false{{< /highlight >}}：僅納入 [`mainSections`](https://gohugo.io/configuration/all/#mainsections)) |
| `disable_scroll_to_top` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 隱藏並停用「回到頁面頂端」按鈕 |
| `footer_text` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 附加在網站頁尾版權聲明後的自訂字串 |
| `hide_copyright` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 隱藏網站頁尾的版權聲明 |
| `support_theme_author` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 在網站頁尾顯示 "Powered by" 字樣，鼓勵此佈景主題的作者 (謝謝 🥹) |
| `hide_footer` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 隱藏整個頁尾區塊 (版權、自訂文字、"Powered by" 字樣) |
| `force_color_scheme` | {{< highlight toml "hl_inline=true" >}}false{{< /highlight >}}<br>{{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 設為 {{< highlight toml "hl_inline=true" >}}false{{< /highlight >}}時，在網站頁尾顯示色彩切換 UI 供讀者切換；若設為字串 {{< highlight toml "hl_inline=true" >}}"system"{{< /highlight >}} (跟隨使用者系統設定)、{{< highlight toml "hl_inline=true" >}}"light"{{< /highlight >}}、{{< highlight toml "hl_inline=true" >}}"dark"{{< /highlight >}} 則隱藏色彩切換 UI，並指定網站的色彩模式 |
| `display_short_lang_name` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 若網站提供多語內容，頂部導航列顯示的語言名稱使用 "EN"、"ZH" 等縮寫，而非 "English"、"中文" 等語言全稱 |

</div>

---


## 品牌 {id="branding"}

表頭：`[params.neso.branding]`。

> [!IMPORTANT]
> 以下設定涉及的圖檔眾多繁雜，但其實只要 `og_image`、`favicon_ico`、`favicon_svg` 基本三者就可取得良好的顯示和連結預覽效果，其餘圖檔用於確保在特定環境下的完美呈現，對多數人來說可忽略不設。

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| 鍵名 | 類型 | 說明 |
| --- | :---: | --- |
| `logo_text` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 自訂頂部導航列 logo 字樣 (此字串僅於導航列用作 logo 顯示，其他需要用到站名的地方都是取全站設定的 `Title` 值) |
| `hide_logo_text` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 隱藏頂部導航列 logo 字樣 |
| `logo_image` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 設定頂部導航列的 logo 圖像 [URL](#assets_url) |
| `logo_image_dark` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 設定頂部導航列的 Dark Mode 版 logo 圖像 [URL](#assets_url) (網站外觀處於深色模式下才會顯現) |
| `logo_image_width` | {{< highlight text "hl_inline=true" >}}Integer{{< /highlight >}} | 設定頂部導航列的 logo 圖像寬度 (單位為 `px`，填寫時*勿*帶單位) |
| `logo_image_height` | {{< highlight text "hl_inline=true" >}}Integer{{< /highlight >}} | 設定頂部導航列的 logo 圖像高度 (單位為 `px`，填寫時*勿*帶單位) |
| `og_image` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 設定全站預設的 `og:image` 圖像 [URL](#assets_url)；建議尺寸為 1200×630 px |
| `favicon_ico` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 設定網站的 favicon 圖像 URL (副檔名 {{< highlight text "hl_inline=true" >}}ICO{{< /highlight >}})；出於支援性、SEO 的考量，除非有特殊需求，否則強烈建議檔名使用 {{< highlight text "hl_inline=true" >}}favicon.ico{{< /highlight >}}、直接放在 Hugo 專案根目錄下的 {{< highlight text "hl_inline=true" >}}static/{{< /highlight >}} 頂層，並將此設定留空 |
| `favicon_svg` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 設定網站的 favicon 圖像 [URL](#assets_url) (副檔名 {{< highlight text "hl_inline=true" >}}SVG{{< /highlight >}})；SVG favicon 在現今環境已有良好支援，顯示效果較佳 |
| `apple_touch_icon` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 設定網站的 `apple-touch-icon` 圖像 [URL](#assets_url) (副檔名 {{< highlight text "hl_inline=true" >}}PNG{{< /highlight >}}) |
| `pwa_short_title` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 設定行動設備將網站加入主畫面時，所顯示的名稱 (可用較簡短的字詞來取得良好顯示效果) |
| `pwa_theme_color_light` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 設定網站的 16 進位主題色碼 (如 `#bada55`)，支援的瀏覽器會將 UI 染色，以提供更沈浸的瀏覽體驗；建議以網站背景色為設定依據 |
| `pwa_theme_color_dark` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 設定網站的 16 進位主題色碼 (如 `#bada55`)，支援的瀏覽器會將 UI 染色，以提供更沈浸的瀏覽體驗；建議以網站背景色為設定依據，此設定專用於深色模式的瀏覽環境 |
| `pwa_icon_svg` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 設定網站的 PWA icon [URL](#assets_url) (副檔名 {{< highlight text "hl_inline=true" >}}SVG{{< /highlight >}}) |
| `pwa_icon_192` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 設定網站的 PWA icon [URL](#assets_url) (副檔名 {{< highlight text "hl_inline=true" >}}PNG{{< /highlight >}}，尺寸 192×192 px) |
| `pwa_icon_512` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 設定網站的 PWA icon [URL](#assets_url) (副檔名 {{< highlight text "hl_inline=true" >}}PNG{{< /highlight >}}，尺寸 512×512 px) |
| `pwa_icon_maskable_svg` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 設定網站的遮罩版 PWA icon [URL](#assets_url) (副檔名 {{< highlight text "hl_inline=true" >}}SVG{{< /highlight >}}) |
| `pwa_icon_maskable_192` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 設定網站的遮罩版 PWA icon [URL](#assets_url) (副檔名 {{< highlight text "hl_inline=true" >}}PNG{{< /highlight >}}，尺寸 192×192 px) |
| `pwa_icon_maskable_512` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 設定網站的遮罩版 PWA icon [URL](#assets_url) (副檔名 {{< highlight text "hl_inline=true" >}}PNG{{< /highlight >}}，尺寸 512×512 px) |

</div>

> [!NOTE]
> 帶有 `pwa_` 前綴的設定，本佈景主題將依 [W3C](https://www.w3.org/TR/appmanifest/) 規格，幫你打包生成 manifest.json 檔案，詳見 [web.dev](https://web.dev/learn/pwa/web-app-manifest?hl=zh-tw) 與 [MDN](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Manifest) 說明。
> 
> 關於 PWA icon 各種版本的適用情境和詳細製圖規格，可查閱 [web.dev](https://web.dev/learn/pwa/web-app-manifest?hl=zh-tw#icons)。

---


## 社交平台連結

表頭：`[params.neso.social]`。

此處的設定用來在網站首頁顯示你的社交平台連結，在 TOML 以「Array of Tables」形式編寫，範例如下：

```toml {hl_lines=["4-10"]}
[params]
  [params.neso]
    # 其他設定略...
    [params.neso.social]
      [[params.neso.social.links]]
        name = "Github"
        url  = "https://github.com/babeneso"
      [[params.neso.social.links]]
        name = "X"
        url  = "https://x.com/babeneso"
    [params.neso.home]
    # 其他設定略...
```

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| 鍵名 | 類型 | 說明 |
| --- | :---: | --- |
| `name` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 平台名稱；大小寫無關緊要，但拼字務必正確 (英文)，以確保能顯示正確的 icon |
| `url` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 你在該平台的個人頁面 URL |

</div>

---


## 首頁 {id="homepage"}

以下是首頁設定的詳細說明。

1. ### 準備 Index 檔案
    
    在 Hugo 專案根目錄下的 {{< highlight text "hl_inline=true" >}}content/{{< /highlight >}} 頂層建立一個 {{< highlight text "hl_inline=true" >}}_index.md{{< /highlight >}} 檔案 (注意開頭底線)，在裡面編寫以下內容：
    
    ```yaml
    ---
    # 首頁用的 Front Matter 只需要以下這兩條：
    title       : "奶獸喵喵之家"
    description : "喜歡做菜、弄些小點心，夢想是每天抱著貓貓，睡到太陽曬屁股！"
    ---
    
    # 主要內容區域，`display_mode` 設為 "profile" 以外的模式才會用到。
    # 如果檔案是 "_index.md"，你可以在這裡寫 Markdown 語法充實內容；
    # 如果檔案是 "_index.html"，你可以在這裡寫 HTML 語法，自行實現更複雜的內容。
    ```
    

2. ### 選擇排版設計

    在 hugo.toml 全站設定檔內的 `[params.neso.home]` 表頭下設定排版模式：

    ```toml {hl_lines=["4-5"]}
    [params]
      [params.neso]
        # 其他設定略...
        [params.neso.home]
          display_mode = "profile"
        # 其他設定略...
    ```
    
    <dl>
        <dt>{{< highlight toml "hl_inline=true" >}}display_mode = "profile"{{< /highlight >}}</dt>
        <dd>
            {{< figure src="home-profile.png" >}}
            <p>顯示大頭照、標題、自介文字、以及社群連結和自訂連結按鈕，置中排版。此模式較簡潔，不會採用 Index 檔的主要內容。</p>
        </dd>
        <dt>{{< highlight toml "hl_inline=true" >}}display_mode = "intro"{{< /highlight >}}</dt>
        <dd>
            {{< figure src="home-intro.png" >}}
            <p>顯示標題、社群連結、Index 檔的主要內容，依語系書寫方向排版。</p>
        </dd>
        <dt>{{< highlight toml "hl_inline=true" >}}display_mode = "<其他任何字串>"{{< /highlight >}}</dt>
        <dd>
            <p>高度自訂模式，僅顯示 Index 檔的主要內容。</p>
            <p>在此模式下，推薦採用 {{< highlight text "hl_inline=true" >}}_index.html{{< /highlight >}} 檔名，然後直接在裡面寫 HTML 原始碼——這些原始碼會被包在一個響應式寬度容器內，所以你不需要從頭寫 {{< highlight html "hl_inline=true" >}}<html>{{< /highlight >}}、{{< highlight html "hl_inline=true" >}}<body>{{< /highlight >}} 等標籤，直接寫內容就好。</p>
            <p>佈景主題內已佈下 Tailwind CSS 處理管線，你可以搭配使用各種 utility class。</p>
        </dd>
    </dl>


### 細部設定：{{% highlight toml "hl_inline=true" %}}"profile"{{% /highlight %}} 模式

子表頭：`[params.neso.home.profile]`。

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| 鍵名 | 類型 | 說明 |
| --- | :---: | --- |
| `avatar_image` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 設定大頭貼圖像 [URL](#assets_url) |
| `avatar_image_alt_text` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 設定大頭貼圖像的替代文字 |
| `avatar_image_size` | {{< highlight text "hl_inline=true" >}}Integer{{< /highlight >}} | 設定大頭貼圖像的尺寸，一個正整數即可，大頭貼長寬相同 (單位為 `px`，填寫時*勿*帶單位) |
| `avatar_image_size_sm` | {{< highlight text "hl_inline=true" >}}Integer{{< /highlight >}} | 設定大頭貼圖像在行動裝置 (小螢幕) 的尺寸，一個正整數即可，大頭貼長寬相同 (單位為 `px`，填寫時*勿*帶單位) |

</div>

你還可以額外設定一些連結按鈕，顯示在自介下方，在 TOML 以 [Array of Tables](https://toml.io/en/v1.0.0#array-of-tables) 形式編寫，範例如下：

```toml {hl_lines=["4","7-12"]}
[params]
  [params.neso]
    # 其他設定略...
    [params.neso.home.profile]
      avatar_image = "img/profile-photo.jpg"
      # 其他設定略...
      [[params.neso.home.profile.link_btns]]
        label = "下載我的履歷"
        url   = "https://example.com/resume"
      [[params.neso.home.profile.link_btns]]
        label = "經手專案"
        url   = "https://github.com/babeneso"
    [params.neso.home.list]
    # 其他設定略...
```

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| 鍵名 | 類型 | 說明 |
| --- | :---: | --- |
| `label` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 按鈕文字 |
| `url` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 按鈕連結 URL |

</div>


### 細部設定：近期文章

子表頭：`[params.neso.home.list]`。

無論你為首頁選擇何種排版模式，都可以額外在下面附加近期文章清單。

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| 鍵名 | 類型 | 說明 |
| --- | :---: | --- |
| `featured_entries_limit` | {{< highlight text "hl_inline=true" >}}Integer{{< /highlight >}} | 要在首頁顯示的近期文章數量，設為 {{< highlight toml "hl_inline=true" >}}0{{< /highlight >}} 則不顯示 |
| `includes_all_sections` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 納入所有 Section 的文章 (預設為 {{< highlight toml "hl_inline=true" >}}false{{< /highlight >}}：僅納入 [mainSections](https://gohugo.io/configuration/all/#mainsections)) |
| `hide_view_archives_cta` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 隱藏近期文章清單下的「查閱過往文章」按鈕 (該按鈕通往 archives 頁面) |

</div>

---


## 文章清單頁 {id="list-settings"}

表頭：`[params.neso.list]`。

網站內會在各處出現文章清單頁面，例如某個 Section 的文章列表、含有某個 Tag 的文章列表⋯⋯等，以下參數用來設定它們的顯示方式。

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| 鍵名 | 類型 | 說明 |
| --- | :---: | --- |
| `prominent_first_entry` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 將列表的第一則文章稍微突出顯示 (純粹外觀點綴) |
| `provide_rss_for_each_list` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 除了網站首頁外，在所有清單頁面都顯示它們各自的 RSS 按鈕 |
| `hide_page_nums` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 若文章數量多、產生了分頁，此選項可隱藏分頁頁碼 |
| `hide_summary` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 隱藏列表裡文章的內文預覽 |
| `hide_cover_image` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 隱藏列表裡文章的封面圖 |
| `disable_responsive_cover_image` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 列表裡文章的封面圖預設會產生多個圖檔 (透過 Hugo Pipes 於建置期間自動縮圖)，讓瀏覽器依照螢幕尺寸顯示適當的圖檔 `src`，此選項可關閉這個機制、縮短建置時間，但可能犧牲一點瀏覽體驗 |

</div>

---


## 單篇文章頁

表頭：`[params.neso.page]`。

此處參數控制所有單篇文章頁的「整體預設」。部分設定可透過頁面的 [Front Matter]({{% relref "Params - Front Matter/#other-settings" %}}) 覆寫。

> [!TIP]
> 舉例來說，如果在這裡透過 {{< highlight toml "hl_inline=true" >}}show_toc = "false"{{< /highlight >}} 把顯示內文目次的功能關了，你仍然可以在某篇文章的 Front Matter 單獨為該篇文章重新啟用目次區塊。對於此類狀況，下方說明會另行附註。

### 一般設定 {id="single-general"}

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| 鍵名 | 類型 | 說明 |
| --- | :---: | --- |
| `ext_link_indicator` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 為文內外連的超連結加上提示 icon |
| `ext_link_no_opener_referrer` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 為文內外連的超連結 {{< highlight html "hl_inline=true" >}}<a>{{< /highlight >}} 元素加上 `noopener`、`noreferrer` 等 `rel` 屬性值 |
| `ext_link_new_window` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 在新分頁/視窗打開外連的超連結 |
| `hide_description_in_single` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 寫文章時若有填寫 Front Matter 的 `description` 欄位，它除了被拿去用在 SEO 以外 (例如 {{< highlight html "hl_inline=true" >}}<meta>{{< /highlight >}} 標籤)，也會顯示在文章頂部作為前言。此參數可隱藏這類前言區塊，僅作為後設資料供 SEO 使用。 |
| `full_size_cover_image_link` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 寫文章時若有在 Front Matter 設定封面圖，此參數可為封面圖加上連往全尺寸原圖的連結 |
| `show_toc` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 顯示內文目次 (可在頁面的 Front Matter 覆寫此設定) |
| `toc_expanded` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 預先展開內文目次 (可在頁面的 Front Matter 覆寫此設定) |
| `disable_heading_links` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 不要為 Markdown 內文的 {{< highlight markdown "hl_inline=true" >}}## 這類標題{{< /highlight >}} 添加錨點 {{< highlight html "hl_inline=true" >}}<a>{{< /highlight >}} 元素 (類似 GitHub 的 [Section links](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#section-links)，詳見 [Hugo 官方文件](https://gohugo.io/configuration/markup/#parserautoheadingid)) |
| `enable_comments` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 啟用評論/留言區塊；詳見評論區設定說明 (可透過頁面的 Front Matter 單方面關閉) |
| `hide_copy_code_button` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 隱藏程式碼區塊的「拷貝」按鈕 |

</div>


### 頁首文章資訊 {id="single-metadata"}

文章頁首區塊用來顯示發表日期、作者、字數統計⋯⋯等等的後設資料。部分設定可透過頁面的 [Front Matter]({{% relref "Params - Front Matter/#metadata-settings" %}}) 覆寫。

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| 鍵名 | 類型 | 說明 |
| --- | :---: | --- |
| `show_reading_time` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 顯示閱讀時間估計 |
| `show_word_count` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 顯示字數統計 |
| `show_author` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 顯示作者 (作者資訊可在全站參數設定、或是在 Front Matter 為單篇文章個別設定) |
| `show_canonical_link` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 如果文章的 Front Matter 有填寫 `canonical_url` 欄位，則將該欄位提供的連結顯示出來 |
| `canonical_link_text` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 顯示 `canonical_url` 連結時，要在開頭加上的預設字串；例如 {{< highlight text "hl_inline=true" >}}原文發表於{{< /highlight >}} (可在頁面的 Front Matter 覆寫此設定) |
| `hide_metadata` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 隱藏整個頁首區塊 (可在頁面的 Front Matter 覆寫此設定) |

</div>


### 頁尾功能 {id="single-footer"}

文章頁尾區塊用來顯示文章標籤、分享按鈕、繼續閱讀上/下篇等功能。部分設定可透過頁面的 [Front Matter]({{% relref "Params - Front Matter/#footer-settings" %}}) 覆寫。

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| 鍵名 | 類型 | 說明 |
| --- | :---: | --- |
| `show_content_footer` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 顯示頁尾區塊 (可透過頁面的 Front Matter 單方面關閉) |
| `show_share` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 顯示分享按鈕 (可透過頁面的 Front Matter 單方面關閉) |
| `share_providers` | {{< highlight text "hl_inline=true" >}}String[]{{< /highlight >}} | 設定分享目標平台；如果有設定，就只會顯示你選用的平台，例如 {{< highlight toml "hl_inline=true" >}}["facebook", "line"]{{< /highlight >}}；沒設定的話預設顯示所有平台，即：{{< highlight toml "hl_inline=true" >}}["facebook", "line", "linkedin", "messenger", "reddit", "telegram", "whatsapp", "x"]{{< /highlight >}} |
| `show_prev_next` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 顯示「上/下一篇」文章，供訪客延伸閱讀 (可在頁面的 Front Matter 覆寫此設定) |

</div>


> [!NOTE]
> 這裡的「單篇文章頁」指的實際上是 Hugo 所 render 出來的 HTML 頁面，其中大部分設定是針對 [page kind](https://gohugo.io/quick-reference/glossary/#page-kind) 為 `page` 的頁面——對大多數使用情境來說，通常就是部落格的某篇文章頁面，只是 Hugo 的命名比較抽象，所以姑且稱為單篇文章頁。

---


## SEO

表頭：`[params.neso.seo]`。

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| 鍵名 | 類型 | 說明 |
| --- | :---: | --- |
| `block_indexing` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 將全站所有頁面的 {{< highlight html "hl_inline=true" >}}<meta name="robots">{{< /highlight >}} 設為 `noindex`、`nofollow` (可在頁面的 Front Matter 覆寫此設定) |
| `site_description` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 網站整體的簡介/描述 |
| `site_keywords` | {{< highlight text "hl_inline=true" >}}String[]{{< /highlight >}} | 網站整體的關鍵字清單，例如 {{< highlight toml "hl_inline=true" >}}["貓咪", "可愛"]{{< /highlight >}} |
| `site_author` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} {{< highlight text "hl_inline=true" >}}String[]{{< /highlight >}} | 網站擁有者/作者名稱；只有一人的話可直接給字串，例如 {{< highlight toml "hl_inline=true" >}}"李清照"{{< /highlight >}}，需要顯示多人的話可用字串陣列，例如 {{< highlight toml "hl_inline=true" >}}["蘇洵", "蘇軾", "蘇轍"]{{< /highlight >}} |

</div>


### 細部設定：結構化資料

子表頭：`[params.neso.seo.schema]`。

佈景主題會自動幫你生成 JSON-LD 格式的[結構化資料](https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data?hl=zh-tw)，以加強 SEO 表現，以下是一些你可以額外補充的資訊。

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| 鍵名 | 類型 | 說明 |
| --- | :---: | --- |
| `publisher_type` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 網站發布者類型，值可為 `Person` 或 `Organization`；更多資訊見 [Google 搜尋中心文件](https://developers.google.com/search/docs/appearance/structured-data/article?hl=zh-tw#author-bp)，或 [Schema.org](https://schema.org/publisher) |
| `same_as` | {{< highlight text "hl_inline=true" >}}String[]{{< /highlight >}} | 其他能代表你的 URL，例如社交平台個人資料頁面、粉絲頁等；更多資訊見 [Google 搜尋中心文件](https://developers.google.com/search/docs/appearance/structured-data/profile-page?hl=zh-tw#profile-target-specification)，或 [Schema.org](https://schema.org/sameAs) |

</div>


### 細部設定：搜尋引擎認證

子表頭：`[params.neso.seo.verification]`。

進行 SEO 成效管理的時候，你可能會需要向搜尋引擎驗證你對網站的擁有權。

搜尋引擎通常會提供多種驗證方式，在 HTML 裡插入 {{< highlight html "hl_inline=true" >}}<meta>{{< /highlight >}} 標籤是其中一種，以 [Google](https://support.google.com/webmasters/answer/9008080?hl=zh-Hant&sjid=2229782392232590920-NC#meta_tag_verification&zippy=%2Chtml-標記) 為例，它會提供像這樣的代碼給你：

```html
<meta name="google-site-verification" content="...">
```

其他搜尋引擎大多也有提供類似機制——總而言之，你取得如上述的驗證原始碼以後，找尋 `content` 裡面的那串代碼，然後把它貼到下面提供的設定欄位，佈景主題就會自動幫你在網頁原始碼的適當位置插入 {{< highlight html "hl_inline=true" >}}<meta>{{< /highlight >}} 驗證標籤。

以下是目前可供設定的搜尋引擎：

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| 鍵名 | 類型 | 說明 |
| --- | :---: | --- |
| `google` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | [Google](https://support.google.com/webmasters/answer/9008080?hl=zh-Hant#meta_tag_verification) |
| `bing` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | [Bing](https://www.bing.com/webmasters/help/add-and-verify-site-12184f8b) |
| `yandex` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | [Yandex](https://yandex.com/dev/webmaster/doc/en/concepts/verification) |
| `naver` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | [Naver](https://searchadvisor.naver.com/guide/faq-start-register) |

</div>

---


## 站內搜尋

表頭：`[params.neso.search]`。

你需要先將站內搜尋頁面[設定妥當]({{% ref "Pages and Menu Setup/#search" %}})，下列設定才有意義；如果你不需要站內搜尋功能，可忽略此處的參數。

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| 鍵名 | 類型 | 說明 |
| --- | :---: | --- |
| `input_placeholder` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 顯示在搜尋框的提示字樣 |

</div>

---


## Hugo Pipes 資產管線

表頭：`[params.neso.assets]`。

佈景主題所用到的一些資源會經過 [Hugo Pipes](https://gohugo.io/hugo-pipes/introduction/) 處理，例如 CSS、JavaScript、部分圖檔等，有時候是為了壓縮轉檔、有時候是為了加上「[Fingerprint](https://gohugo.io/functions/resources/fingerprint/)」以達到 cache busting 的效果，以下提供相關設定選項。

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| 鍵名 | 類型 | 說明 |
| --- | :---: | --- |
| `output_dir` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | 設定 Hugo Pipes 要將輸出的資源放到[發佈目錄](https://gohugo.io/configuration/all/#publishdir)下的哪個子目錄 (名稱)，預設為 {{< highlight toml "hl_inline=true" >}}"assets"{{< /highlight >}} |
| `disable_fingerprinting` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | 關閉 Fingerprinting |

</div>

---


## 其餘說明

### 圖像放置處與 URL {id="assets_url"}

上述需要提供圖像 URL 位址的設定皆為以下邏輯：

絕對路徑
: 直接使用該 URL 指向的圖檔，可為站內根目錄起算、也可外連。
: 例如：{{< highlight toml "hl_inline=true" >}}"/special/stuff.png"{{< /highlight >}}、{{< highlight toml "hl_inline=true" >}}"https://example.com/image.png"{{< /highlight >}}。

相對路徑
: 建議將圖檔放在 Hugo 專案根目錄下的 {{< highlight text "hl_inline=true" >}}assets/{{< /highlight >}} 或 {{< highlight text "hl_inline=true" >}}static/{{< /highlight >}} 內 (擇一)，不管你挑哪裡放置，兩者相對路徑寫法都是從它們內部頂層起算。
: 舉例來說，將圖檔放在 {{< highlight text "hl_inline=true" >}}assets/img/example.png{{< /highlight >}} 或 {{< highlight text "hl_inline=true" >}}static/img/example.png{{< /highlight >}}，最後在設定都是寫 {{< highlight toml "hl_inline=true" >}}"img/example.png"{{< /highlight >}}，佈景主題會自行找到正確位置。惟須注意開頭不要有斜線，否則意義會變成根目錄絕對路徑。
: 放在 {{< highlight text "hl_inline=true" >}}assets/{{< /highlight >}} 內的話，可支援 fingerprinting。
