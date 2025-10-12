---
title           : "建立文章"
date            : 2025-10-10T19:01:49+08:00
lastmod         : 2025-10-10T19:01:49+08:00
slug            : "create-post"
isCJKLanguage   : true

description     : "本文將說明建立文章時，推薦的整理方式、建議使用的 Front Matter，以及範本。"
summary         : "本文將說明建立文章時，推薦的整理方式、建議使用的 Front Matter，以及範本。"
keywords        : ["設定教學", "hugo.toml", "Front Matter", "Hugo", "Markdown", "Theme", "佈景主題", "Neso", "hugo-neso"]
tags            : ["hugo.toml", "Front Matter"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
      hidden_in_single: true
---


## Page Bundle

建立文章時，建議為每篇文章都準備一單獨的資料夾，然後將文章本體的 Markdown 檔 (須命名為 `index.md`)、該篇文章所用到的圖片、封面等素材全包在該資料夾內。

這樣的一個「文章包」就稱為一個「[Leaf Bundle](https://gohugo.io/content-management/page-bundles/#leaf-bundle)」。

```text
mysite/    <- Hugo 專案目錄
├── ...
├── content/       <- 內容目錄
│   ├── _index.md      <- 內容目錄頂層的 _index.md 為首頁
│   │
│   └── posts/         <- 這叫 Section，可看作是一種大分類 (也叫 branch bundle)
│       │
│       ├── foo/           <- 這是一個 leaf bundle (文章包)、代表一篇文章及它的素材
│       │   ├── index.md   <- bundle 內的 index.md 為文章本體
│       │   └── cover.jpg  <- 跟隨著文章被打包的素材
│       │
│       └── bar/           <- 這是另一個 leaf bundle (另一篇文章)
│           └── index.md
├── data/
├── i18n/
└── ...
```


## 建立文章

需要建立文章時，在終端機內 `cd` 至 Hugo 專案目錄，然後執行下列指令：

```shell {linenos=true data-prompt=true}
hugo new <section 名稱>/'<文章標題>'/index.md
```

例如：

```shell {linenos=true data-prompt=true}
hugo new posts/'貓貓快樂的一天'/index.md
```

這樣 Hugo 就會幫你建好 `貓貓快樂的一天/` leaf bundle 資料夾、裡面放好 `index.md`，並且在 Markdown 的開頭自動填寫好文章標題等 Front Matter。

用終端機只是一個選項，Hugo 當然不會阻止你手動為文章建立資料夾結構。

至於 Front Matter 有哪些參數欄位可填，請參考：

- [Hugo 原生提供的參數](https://gohugo.io/content-management/front-matter/#fields)
- [Neso 佈景主題提供的參數]({{% ref "Params - Front Matter" %}})


## Archetype

前面提到的建立文章指令，其方便之處在於，你可以為文章的 Markdown 檔案設計一個「範本」，把常用的 Front Matter 寫進去，就不需要每次發文都要查找設定參數、複製貼上。

此處說明再多都不如一次實驗來得直觀，請將以下內容複製後，**覆蓋掉**你現在 Hugo 專案目錄 `archetypes/` 下的 `default.md` 內容。

```yaml
---
title           : "{{ .File.ContentBaseName | humanize | replaceRE `\s+` " " | title }}"
date            : {{ .Date }}
slug            : "{{ .File.ContentBaseName | urlize }}"  # 文章的網址字樣
isCJKLanguage   : true  # 此文章含中/日/韓文 (用於字數統計等功能)

description     : "填入文章描述 (適合 SEO 的簡短介紹)"
summary         : "填入文章大意 (適合在列表預覽文章內容)"
keywords        : ["SEO關鍵字1", "SEO關鍵字2", "SEO關鍵字3"]
tags            : ["tag a", "tag b", "tag c"]

params:
  neso:
    show_toc   : false  # 顯示目次
    cover:     # 封面圖設定 (無封面請連同下面設定整段刪去)
      image    : "<封面圖URL>"  # 若封面圖和 md 檔一起在 bundle 內，直接寫檔名即可
      caption  : "<封面圖標題>"  # optional，會顯示在封面圖下
      alt_text : "<封面圖描述>"  # optional，無障礙替代文字
---

Markdown 正文由此開始
```

完成後，在 Hugo 專案目錄試著執行下列指令：

```shell {linenos=true data-prompt=true}
hugo new posts/'貓貓敲鍵盤'/index.md
```

你將發現 Hugo 幫你建出來的文章 Markdown 已將重要資料帶入，並且一些設定也都列在裡面了。

`archetypes/` 裡面的 `default.md` 就是範本檔，`hugo new` 建文章指令就是拿範本檔給你用 (裡面的 `{{ ... }}` 則是指示 Hugo 填入資料)。
