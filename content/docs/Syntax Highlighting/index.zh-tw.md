---
title           : "使用程式碼上色功能"
date            : 2025-10-09T09:31:00+08:00
lastmod         : 2025-10-09T09:31:00+08:00
slug            : "syntax-highlighting"
isCJKLanguage   : true

description     : "Hugo 內建程式碼語法上色功能「Chroma」，不需要引入第三方套件即可使用，Neso 佈景主題對此做了外觀呈現的最佳化、並加入了一些小改進。"
summary         : "Hugo 內建程式碼語法上色功能「Chroma」，不需要引入第三方套件即可使用，本佈景主題對此做了外觀呈現的最佳化、並加入了一些小改進，請依照本頁面的說明進行設置。"
keywords        : ["Hugo", "Markdown", "程式碼", "Chroma", "Syntax Highlighting", "語法上色", "客製化", "Theme", "Neso", "hugo-neso"]
tags            : ["hugo.toml", "Chroma", "語法上色", "Markdown", "設定"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
      hidden_in_single: true
---


## 關於程式碼語法上色

懂得使用 Hugo 架站的你，想必有很多程式編寫上的真知灼見必須與全世界分享。Hugo 已內建程式碼語法上色功能「[Chroma](https://github.com/alecthomas/chroma)」，不需要引入第三方套件即可使用，本佈景主題對此做了外觀呈現的最佳化、並加入了一些小改進，請依照本頁面的說明進行設置。


## 設定

確保你的全站設定檔 hugo.toml 內含有下列設定：

```toml {hl_lines=[3]}
[markup]               # `markup` 表頭位在 toml 頂層
  [markup.highlight]   # `highlight` 子表頭
    noClasses = false
```

基本上這樣就可以了！如果你好奇的話：

- **{{< highlight toml "hl_inline=true" >}}noClasses = false{{< /highlight >}} 此為必須項。**

    Hugo 預設會使用 inline CSS 來為網頁中的語法區塊上色，這樣不利於客製化調整，因此要透過這個選項，改成使用 class 來控制樣式。

- **Hugo [官方文件](https://gohugo.io/configuration/markup/#highlight)有提到其他設定選項，請務必保持預設**
    
    亦即不要在你的 hugo.toml {{< highlight toml "hl_inline=true" >}}[markup.highlight]{{< /highlight >}} 下添加其他設定項，它們比較適合在文章內實際嵌入程式碼區塊時另行設定。


## 開始使用

在 Markdown 內有數種方法來展示程式碼。

### 區塊展示

用三個重音符號 <kbd>\`</kbd> 包圍住程式碼的頭尾 (各占據一行)，像這樣：

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

顯示效果：

```
package main

import "fmt"

func main() {
    for i := 0; i < 3; i++ {
        fmt.Println("Value of i:", i)
    }
}
```

如你所見，上面並沒有語法上色的效果，因為這是 Markdown 原生的樣式，若要啟用語法上色，需要在第一行的重音符號後加上一些選項：

{{< highlight text "hl_lines=1" >}}
```go {linenos=true hl_lines=[3,"6-8"] lineNoStart=2}
package main

import "fmt"

func main() {
    for i := 0; i < 3; i++ {
        fmt.Println("Value of i:", i)
    }
}
```
{{< /highlight >}}

開頭的 `go` 為[語言代號](https://gohugo.io/content-management/syntax-highlighting/#languages)，你可以在後面加上一對大括號 `{}` 來設定額外樣式 (都為 optional)，其中選項有：

`linenos=true`
: 顯示行號。

`hl_lines=[3,"6-8"]`
: 要突顯 (劃重點) 的行。

`lineNoStart=2`
: 起始行號，未設定則從 1 開始 (這個不影響前面的行號凸顯計算)。

設定後，顯示效果如下：

```go {linenos=true hl_lines=[3,"6-8"] lineNoStart=2 wrapperClass="haha"}
package main

import "fmt"

func main() {
    for i := 0; i < 3; i++ {
        fmt.Println("Value of i:", i)
    }
}
```

> [!WARNING]
> 其他 Hugo 官方文件提到的[選項](https://gohugo.io/content-management/syntax-highlighting/#options-1)不建議你使用，因為它們是基於 inline CSS 運作，在這邊用了會導致外觀錯誤。

> [!IMPORTANT]
> 透過縮排在 Markdown 展示程式碼的話，無法使用語法上色。

Neso 佈景主題另外提供了 `data-prompt` 選項，搭配 `linenos=true` 可以把行號換成終端機 prompt 符號，這樣使用者拷貝程式碼時就不會連帶拷貝到 prompt 符號。

{{< highlight text "hl_lines=1" >}}
```shell {linenos=true data-prompt=true}
hugo server
```
{{< /highlight >}}

```shell {linenos=true data-prompt=true}
hugo server
```

事實上，`data-prompt` 可以是任何你指定的符號：

{{< highlight text "hl_lines=1" >}}
```shell {linenos=true data-prompt="🔥"}
hugo server
```
{{< /highlight >}}

```shell {linenos=true data-prompt="🔥"}
hugo server
```


### 行內展示

用一對重音符號 <kbd>\`</kbd> 包圍文字來展示行內程式碼，像這樣：`const number = 42;`，但這原生的做法是沒有語法上色的，如果要做到像這樣 {{< highlight javascript "hl_inline=true" >}}const number = 42;{{< /highlight >}} 的效果，請參閱[這裡]({{% ref "Shortcodes/#chroma" %}})的說明。

---


## 自訂上色風格

本佈景主題已內建了淺色模式和深色模式的上色風格，但你可以改成其他風格包。

1. **生成風格包 CSS 檔**

    打開終端機，並執行 [`hugo gen chromastyles`](https://gohugo.io/commands/hugo_gen_chromastyles/#hugo-gen-chromastyles) 指令：

    ```shell {linenos=true data-prompt=true}
    hugo gen chromastyles --style=monokai > syntax.css
    ```
    
    `--style` 選項填入你要的[風格包代碼](https://gohugo.io/quick-reference/syntax-highlighting-styles/)，它就會在你終端機當下所在目錄產出 syntax.css 檔案。

2. **覆寫佈景主題 CSS**
   
    佈景主題支援淺色模式 (預設) 和深色模式，所使用的語法上色風格包分別名為 **syntax-light.css** 和 **syntax-dark.css**。
    
    你在上一步生成 CSS 檔以後，請改成這兩檔名，然後放置到你 Hugo 專案的 **assets/css/chroma/** 目錄下 (未見 css 等資料夾的話請自行建立)，即：

    - assets/css/chroma/syntax-light.css
    - assets/css/chroma/syntax-dark.css

    這樣 Hugo 會以你的檔案為優先，而非佈景主題的 CSS 檔。
