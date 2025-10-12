---
title           : "短碼 (Shortcode)"
date            : 2025-10-08T05:07:00+08:00
lastmod         : 2025-10-08T14:07:00+08:00
draft           : false
slug            : "shortcodes"
isCJKLanguage   : true

description     : "Neso 佈景主題為 Hugo 的 Shortcode 做了最佳化調整，讓你的文章生動有美感。"
summary         : "Hugo 有內建一些 Markdown 本身不支援的快速語法，稱作「Shortcode」，方便你在文章中添加/嵌入更豐富的素材，本佈景主題已針對這些 Shortcode 的外觀做了最佳化調整。"
keywords        : ["Hugo", "Shortcode", "Markdown", "HTML", "語法", "Chroma", "客製化", "Theme", "Neso", "hugo-neso"]
tags            : ["Shortcode", "Chroma", "語法上色", "Markdown", "短碼"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
      hidden_in_single: true
---


## 關於短碼

Hugo 有內建一些 Markdown 本身不支援的快速語法，稱作「Shortcode」，方便你在文章中添加/嵌入更豐富的素材。

本佈景主題已針對這些 Shortcode 的外觀做了最佳化調整，以下展示它們實際運作的樣子，詳細使用方式請參閱 Hugo [官方文件](https://gohugo.io/shortcodes/)。

---

## HTML {{% highlight html "hl_inline=true" %}}<details>{{% /highlight %}} (折疊區塊)

在 Markdown 裡插入短碼：

```go-html-template
{{</* details summary="Details 短碼示範" */>}}
這是展開後會看到的內容，你也可以在這裡寫 **Markdown** 語法。
{{</* /details */>}}
```

實際呈現效果：

{{< details summary="Details 短碼示範" >}}
這是展開後會看到的內容，你也可以在這裡寫 **Markdown** 語法。
{{< /details >}}

---

## HTML {{% highlight html "hl_inline=true" %}}<figure>{{% /highlight %}} (插圖)

在 Markdown 裡插入短碼：

```go-html-template
{{</* figure
  src="img_demo.jpg"
  alt="午後的陽光映照在大樓的玻璃帷幕"
  loading="lazy"
  title="HDR 圖片測試"
  caption="看到閃閃發光的照片嗎？恭喜你～你的瀏覽器支援 HDR 圖片！ – Photo by "
  attr="babeneso"
  attrlink="https://instagram.com/babeneso"
*/>}}
{{/* 有些屬性是 optional，不一定要全寫 */}}
```

實際呈現效果：

{{< figure
  src="img_demo.jpg"
  alt="午後的陽光映照在大樓的玻璃帷幕"
  loading="lazy"
  title="HDR 圖片測試"
  caption="看到閃閃發光的照片嗎？恭喜你～你的瀏覽器支援 HDR 圖片！ – Photo by "
  attr="babeneso"
  attrlink="https://instagram.com/babeneso"
>}}

---

## 行內程式碼語法上色 (加強版) {#chroma}

你原本就可以在 Markdown 用一對重音符號 <kbd>\`</kbd> 包圍文字來展示行內程式碼，像這樣：`const number = 42;`，但這原生的做法是沒有語法上色的，此時可以改用這個短碼：

```go-html-template
{{</* highlight javascript "hl_inline=true" */>}}const number = 42;{{</* /highlight */>}}
```

實際呈現效果：

{{< highlight javascript "hl_inline=true" >}}const number = 42;{{< /highlight >}}

所謂的行內程式碼就是它可以和文字一起書寫，像這樣：{{< highlight javascript "hl_inline=true" >}}const number = 42;{{< /highlight >}}，而不需要獨立成一個區塊⋯⋯糟糕，這個常數是不是一直在被我重複宣告？

> [!WARNING]
> 使用這個短碼之前，必須先依照[這裡]({{% ref "Syntax Highlighting" %}})的說明，設定好 Chroma 上色工具，語法上色才能正確顯示。

---

## YouTube 影片

在 Markdown 裡插入短碼：

```go-html-template
{{</* youtube jVhlJNJopOQ */>}}
```

實際呈現效果：

{{< youtube jVhlJNJopOQ >}}

---

## Instagram 貼文

在 Markdown 裡插入短碼：

```go-html-template
{{</* instagram DNYXvbczqGL */>}}
```

實際呈現效果：

{{< instagram DNYXvbczqGL >}}

---

## X 貼文

在 Markdown 裡插入短碼：

```go-html-template
{{</* x user="Kurz_Gesagt" id="1889702410852925900" */>}}
```

實際呈現效果：

{{< x user="Kurz_Gesagt" id="1889702410852925900" >}}
