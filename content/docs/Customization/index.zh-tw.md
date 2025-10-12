---
title           : "客製化佈景主題"
date            : 2025-10-09T16:29:04+08:00
lastmod         : 2025-10-09T16:29:04+08:00
slug            : "customization"
isCJKLanguage   : true

description     : "得益於 Hugo 本身的覆寫機制，客製化相當簡單且乾淨；Neso 佈景主題也留有多處入口方便你修改，本文由簡單到進階，說明如何進行佈景主題客製化。"
summary         : "得益於 Hugo 本身的覆寫機制，客製化相當簡單且乾淨；Neso 佈景主題也留有多處入口方便你修改，本文由簡單到進階，說明如何進行佈景主題客製化。"
keywords        : ["Hugo", "客製化", "CSS", "Tailwind", "模板", "Template", "Theme", "Neso", "hugo-neso"]
tags            : ["客製化", "Tailwind", "CSS"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
      hidden_in_single: true
---


## 直接覆寫 CSS

在你 Hugo 專案目錄下列位置建立一個空的 {{< highlight text "hl_inline=true" >}}custom.css{{< /highlight >}} (必須是這個檔名)：

{{< highlight text "hl_inline=true" >}}assets/css/custom.css{{< /highlight >}}

未見該目錄的話請自行建立。

接著在裡面直接寫你要的 CSS 即可 (雖然不是最佳做法，但簡單有效)，Neso 的 CSS 都盡可能採取低權重寫法以便你覆蓋。

你當然也可以依照 Tailwind 官方的[建議](https://tailwindcss.com/docs/adding-custom-styles)，將 CSS 寫在適當的 layer、定義你的 utility class——如果你想這樣做的話，我已建立好[小抄](https://github.com/babeneso/hugo-neso/blob/main/assets/css/custom.css)供你使用。

> [!NOTE]
> 由於我製作這個佈景主題時，主要是使用 Tailwind 的 utility class，因此 HTML 內現成可供你 "target" 的 class name 可能不多，我會在後續更新適當添加。


---

## 客製化程式碼語法上色

請閱讀[此處]({{% ref "Syntax Highlighting/#customize-the-highlighting-theme" %}})的說明。


---

## Tailwind CSS

到 Neso 的 GitHub Repo 下載 [palette.css](https://github.com/babeneso/hugo-neso/blob/main/assets/css/palette.css)。

你將會在該 CSS 檔案裡看到佈景主題所使用的變數。接著依照 Tailwind [建議的方式](https://tailwindcss.com/docs/theme#customizing-your-theme) 修改、自訂樣式變數即可。

編寫完你要的內容後，放到你 Hugo 專案目錄下的：{{< highlight text "hl_inline=true" >}}assets/css/palette.css{{< /highlight >}}。

未見該目錄的話請自行建立。


---

## 插入自訂原始碼

到 Neso 的 GitHub Repo 下載[這四個檔案](https://github.com/babeneso/hugo-neso/tree/main/layouts/_partials/include) (不必全部，看下面說明挑選你需要的即可)：

{{< highlight text "hl_inline=true" >}}head_start.html{{< /highlight >}}
: 寫在這裡面的 HTML、CSS、JavaScript、[Go html/template](https://gohugo.io/templates/introduction/) 語法將會被插入到所有網頁的 {{< highlight html "hl_inline=true" >}}<head>{{< /highlight >}} 標籤**內部最一開始**的地方。
: 適合：Google Tag Manager 容器代碼、JavaScript (避免 FOUC)

{{< highlight text "hl_inline=true" >}}head_end.html{{< /highlight >}}
: 寫在這裡面的語法將會被插入到所有網頁的 {{< highlight html "hl_inline=true" >}}<head>{{< /highlight >}} 標籤**內部最末端**的地方。
: 適合：自訂 CSS

{{< highlight text "hl_inline=true" >}}body_start.html{{< /highlight >}}
: 寫在這裡面的語法將會被插入到所有網頁的 {{< highlight html "hl_inline=true" >}}<body>{{< /highlight >}} 標籤**內部最一開始**的地方。
: 適合：Google Tag Manager 容器代碼

{{< highlight text "hl_inline=true" >}}body_end.html{{< /highlight >}}
: 寫在這裡面的語法將會被插入到所有網頁的 {{< highlight html "hl_inline=true" >}}<body>{{< /highlight >}} 標籤**內部最末端**的地方。
: 適合：JavaScript

在檔案裡編寫你要的內容後，放到你 Hugo 專案目錄下的：{{< highlight text "hl_inline=true" >}}layouts/_partials/include/<這裡>{{< /highlight >}}。

未見該目錄的話請自行建立。

> [!TIP]
> Neso 佈景主題已佈下 Tailwind CSS 的處理管線，你可以在 HTML template 裡自由使用 utility class。


---

## 覆寫 Template (進階)

觀察 Neso 佈景主題的目錄結構 ([GitHub Repo](https://github.com/babeneso/hugo-neso))：

```text
hugo-neso/
├── assets
├── i18n
└── layouts
```

你在你的 Hugo 專案下應該也會看到類似的目錄結構、一些同名的資料夾，你可以到 Hugo [官方文件](https://gohugo.io/getting-started/directory-structure/#directories) 查閱這些目錄的具體用途。

簡單來說，你可以複製某個佈景主題的原始碼檔案 (可到 Neso 佈景主題的 [GitHub Repo](https://github.com/babeneso/hugo-neso) 下載)、進行你想要的修改，然後放置在你 Hugo 專案下對應的資料夾，Hugo 在建置時便會優先採用你的版本。

> [!TIP]
> Neso 佈景主題已佈下 Tailwind CSS 的處理管線，你可以在 HTML template 裡自由使用 utility class。

> [!WARNING]
> 如果你安裝佈景主題的方式有安放一份 {{< highlight text "hl_inline=true" >}}hugo-neso/{{< /highlight >}} 佈景主題原始檔在你的 {{< highlight text "hl_inline=true" >}}themes/{{< /highlight >}} 目錄下，**請勿直接修改**裡面的原始檔，而是該採取上述的覆寫方式，否則將來佈景主題有更新可用時，你將需要自行追蹤變更了哪些部分。
