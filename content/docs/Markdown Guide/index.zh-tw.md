---
title           : "Markdown 語法"
date            : 2025-10-09T13:06:00+08:00
lastmod         : 2025-10-09T13:06:00+08:00
slug            : "markdown-guide"
isCJKLanguage   : true

description     : "Markdown 是 Hugo 用來生成內容的主要格式，本文將列出一些基本語法，展示它們在 Neso 佈景主題的外觀呈現。"
summary         : "Markdown 是 Hugo 用來生成內容的主要格式，本文將列出一些基本語法，展示它們在 Neso 佈景主題的外觀呈現。"
keywords        : ["Hugo", "Markdown", "語法", "客製化", "Theme", "Neso", "hugo-neso"]
tags            : ["Markdown", "語法上色"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
---


## 關於 Markdown

Markdown 是一種以「可讀可寫」為核心的輕量標記語言。Hugo 以其作為預設的 [內容格式](https://gohugo.io/content-management/formats/#markdown)。本頁旨在示範 Neso 佈景主題下的實際呈現 (render) 外觀，完整語法細節請自行查閱網路上的資料。

另外也建議查看 [Shortcode]({{% ref "Shortcodes/" %}})，了解其他 Neso 支援的擴充語法，可在文章內插入類型更多樣的內容。

---


## 標題

盡可能避免在 Markdown 內文使用「標題一」(`#`)，那應該保留給文章本身的標題使用。

Markdown 語法：

```text
# 標題一
## 標題二
### 標題三範例字樣
#### 標題四：儘量少用
##### 標題五的意義不大
###### 標題六跟內文沒有差別
```

呈現效果：

標題一
{class="asheading ash1"}

標題二
{class="asheading ash2"}

標題三範例字樣
{class="asheading ash3"}

標題四：儘量少用
{class="asheading ash4"}

標題五的意義不大
{class="asheading ash6"}

標題六跟內文沒有差別
{class="asheading ash6"}


<style>

.ash1 {
    color: var(--color-neso-fg1);
    font-weight: 800;
    font-size: 2em;        /* 32/r16 */
    line-height: 1.125;    /* 36/e32 */
    margin-top: 0;
    margin-bottom: .875em; /* 28/e32 */
}

.ash2 {
    color: var(--color-neso-fg1);
    font-weight: 700;
    font-size: 1.5em;      /* 24/r16 */
    line-height: 1.33333;  /* 32/e24 */
    margin-top: 2em;       /* 48/e24 */
    margin-bottom: 1em;    /* 24/e24 */
}

.ash3 {
    color: var(--color-neso-fg1);
    font-weight: 600;
    font-size: 1.25em;     /* 20/r16 */
    line-height: 1.6;      /* 32/e20 */
    margin-top: 1.6em;     /* 32/e20 */
    margin-bottom: .6em;   /* 12/e20 */
}

.ash4 {
    color: var(--color-neso-fg1);
    font-weight: 600;
    line-height: 1.5;      /* 24/r16 */
    margin-top: 1.5em;     /* 24/r16 */
    margin-bottom: .5em;   /*  8/r16 */
}

.ash5, .ash6 {
    margin-top: 0;
    margin-bottom: 0;
}

</style>


---


## 一般文字段落

在 Markdown 內直接打字即可產生一般文字段落，每段間要隔一空行，以下為假文假字。

這也是互私上果地其實這種⋯我現的地也會的房機就是沒最，回來的的特了不知孩子，是多另一消失多人只家一起，傳天都可一般，木指接可以接。知道他還算現，我的管敢現在也，還沒嗚嗚，開我是哪個步可能會耶是只有，其實帥消尤其偶像，您年前他可以。

<small>感謝[中文假文產生器](https://textgen.cqd.tw)。</small>

---


## 粗體、斜體

以一對星號 `*` 包住為斜體，以兩對星號 `**` 包住為粗體；三個星號可形成粗斜體；另外也可加刪除線 `~~被刪的字~~`。

Markdown 語法：

```text
這是一般文字，其中有 *斜體*、**粗體**、***粗斜體***，以及 ~~刪除線~~。
```

呈現效果：

這是一般文字，其中有 *斜體*、**粗體**、***粗斜體***，以及 ~~刪除線~~。

---


## 引言

在行首以 `>` 開頭可建立引言 (blockquote)；連續多行會自動合併；`>>` 或在引言中再加入 `>` 可建立巢狀引言。

Markdown 語法：

```text
> 這是一段單層引言。
>
> 可以有多個段落。
>
> > 這是巢狀引言 (第二層)。
```

呈現效果：

> 這是一段單層引言。
>
> 可以有多個段落。
>
> > 這是巢狀引言 (第二層)。


Neso 佈景主題另有針對引言功能做兩項加強：

### Neso 加強版：引言來源

在 hugo.toml 啟用 Markdown [屬性解析](https://gohugo.io/content-management/markdown-attributes/)：

```toml {hl_lines="5"}
[markup]
  [markup.goldmark]
    [markup.goldmark.parser]
      [markup.goldmark.parser.attribute]
        block = true
```

然後在引言緊接著下一行使用 `{author="Name" source="URL"}`：

```text
> 這是一段單層引言。
{author="Neso" source="https://example.com"}
```

即可附上來源署名與連結 (連結為 optional)：

> 這是一段單層引言。
{author="Neso" source="https://example.com"}


### Neso 加強版：[GitHub Alert](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#alerts)

```text
> [!NOTE]
> Useful information that users should know, even when skimming content.

> [!NOTE] 自訂標題
> Useful information that users should know, even when skimming content.

> [!TIP]
> Helpful advice for doing things better or more easily.

> [!IMPORTANT]
> Key information users need to know to achieve their goal.

> [!WARNING]
> Urgent info that needs immediate user attention to avoid problems.

> [!CAUTION]
> Advises about risks or negative outcomes of certain actions.
```

呈現效果：

> [!NOTE]
> Useful information that users should know, even when skimming content.

> [!NOTE] 自訂標題
> Useful information that users should know, even when skimming content.

> [!TIP]
> Helpful advice for doing things better or more easily.

> [!IMPORTANT]
> Key information users need to know to achieve their goal.

> [!WARNING]
> Urgent info that needs immediate user attention to avoid problems.

> [!CAUTION]
> Advises about risks or negative outcomes of certain actions.




---


## 清單

以 `-`、`*` 或 `+` 建立**無序清單**；以數字加點建立**有序清單**。

Markdown 語法：

```text
- 無序清單項目 A
- 無序清單項目 B
    + 子項目 B-1
    + 子項目 B-2

1. 有序清單項目一
2. 有序清單項目二
3. 有序清單項目三

```

呈現效果：

- 無序清單項目 A
- 無序清單項目 B
    + 子項目 B-1
    + 子項目 B-2

1. 有序清單項目一
2. 有序清單項目二
3. 有序清單項目三

---


## 程式碼展示：區塊

Markdown 語法：用三個重音符號 <kbd>\`</kbd> 包圍住程式碼的頭尾 (各占據一行)：

{{< highlight markdown "hl_lines=1 11" >}}
```
package main

import "fmt"

func main() {
    for i := 0; i < 3; i++ {
        fmt.Println("Value of i:", i)
    }
}
```
{{< /highlight >}}

呈現效果：

```
package main

import "fmt"

func main() {
    for i := 0; i < 3; i++ {
        fmt.Println("Value of i:", i)
    }
}
```

使用「[Chroma]({{% ref "Syntax Highlighting" %}})」進行語法上色：

```go {linenos=true hl_lines=[3,"6-8"] lineNoStart=2 wrapperClass="haha"}
package main

import "fmt"

func main() {
    for i := 0; i < 3; i++ {
        fmt.Println("Value of i:", i)
    }
}
```

終端機 prompt 符號：

```shell {linenos=true data-prompt=true}
hugo server
```

---


## 程式碼展示：行內

用一對重音符號 <kbd>\`</kbd> 包圍文字來展示行內程式碼：

`const number = 42;`

使用語法上色 [Shortcode]({{% ref "Shortcodes/#chroma" %}})：

{{< highlight javascript "hl_inline=true" >}}const number = 42;{{< /highlight >}}

---


## 分隔線

連續三個以上的 `-`、`*` 或 `_` 會產生分隔線 (horizontal rule)。

Markdown 語法：

```text
---
***
___
```

呈現效果 (以下會出現 3 條分隔線)：

---
***
___


---


## 超連結

超連結使用 `[文字](URL "可選的標題")`。

Markdown 語法：

```md
這是超連結：[Hugo 官方網站](https://gohugo.io "前往 Hugo 官方網站")。
```

呈現效果：

這是超連結：[Hugo 官方網站](https://gohugo.io "前往 Hugo 官方網站")。

---


## 圖片

圖片語法為 `![替代文字](路徑 "可選的標題")`；替代文字 (alt) 有助於無障礙瀏覽 (a11y)。

Markdown 語法：

```md
![清水混凝土風格的住宅大樓立面](beton-brut.jpg "Photo by babeneso")
```

呈現效果：

![清水混凝土風格的住宅大樓立面](beton-brut.jpg "Photo by babeneso")

---


## 註腳

使用 `[^id]` 建立註腳參照，並在文末以 `[^id]: 說明` 定義內容。

Markdown 語法：

```text
這是有註腳的句子[^1]。

[^1]: 這是註腳說明，可以包含 **粗體** 與 *斜體* 等格式。
```

呈現效果：

這是有註腳的句子[^1]。

[^1]: 這是註腳說明，可以包含 **粗體** 與 *斜體* 等格式。

