---
title           : "安裝佈景主題"
date            : 2025-10-11T04:00:00+08:00
lastmod         : 2025-10-12T15:08:00+08:00
slug            : "installation"
isCJKLanguage   : true

description     : "本文將說明如何安裝 Neso 佈景主題。"
summary         : "本文將說明如何安裝 Neso 佈景主題。"
keywords        : ["設定教學", "hugo.toml", "Tailwind", "Hugo", "Markdown", "Theme", "佈景主題", "Neso", "hugo-neso"]
tags            : ["hugo.toml", "安裝", "Tailwind"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
      hidden_in_single: true
---


## 準備 Hugo

瀏覽到這個網頁的你，應該有很高的機率已經安裝好 Hugo、甚至網站已在運行中，如果是這樣的話，請直接跳到下方的：[安裝佈景主題](#install-theme)。

如果你還沒用過 Hugo，以下簡略說明如何準備好你的第一個 Hugo 網站：


### 安裝 Hugo {id="install-hugo"}

依照官網[說明頁面](https://gohugo.io/installation/)，安裝 Hugo。

> [!IMPORTANT] 安裝前先讀我
> 1. 安裝 Hugo 本體前，*必須*先依照說明頁面裡的「Prerequisites」章節，安裝好「**Git**」和「**Go**」。
> 2. Hugo 有三個版本 (不是指作業系統)：standard、extended、extended/deploy 版，請安裝「**extended**」版，其中：
> 3. Hugo 提供多種安裝方式，若你使用 macOS，建議透過 [Homebrew](https://gohugo.io/installation/macos/#homebrew) 安裝 (作者對 Windows 不熟，需要你自行查找資料)。
> 4. Neso 佈景主題需要 Hugo `v0.150.0` 或以上的版本。

依序安裝好 **Git**、**Go**、**Hugo (extended)** 後，最後在終端機確認：

```shell {linenos=true data-prompt=true}
hugo version
```

終端機回應 Hugo 版本資訊的話，即代表運行無誤。


### 建立 Hugo 網站 {id="new-site"}

在終端機內依序執行下列指令。

移動 ({{< highlight shell "hl_inline=true" >}}cd{{< /highlight >}}) 到你的工作目錄後，執行：

```shell {linenos=true data-prompt=true}
hugo new site mysite
```

上面指令將建立一名為 {{< highlight text "hl_inline=true" >}}mysite{{< /highlight >}} 的資料夾 (你可自行取名，之後將稱之為「Hugo 專案目錄」)，並為你在裡面備好網站基本的原始碼檔案。

然後 {{< highlight shell "hl_inline=true" >}}cd{{< /highlight >}} 進入該專案目錄：

```shell {linenos=true data-prompt=true}
cd mysite
```

接著執行這個指令，將專案目錄初始化為 Git Repository (repo)：

```shell {linenos=true data-prompt=true}
git init
```

建議你在此時準備好 {{< highlight text "hl_inline=true" >}}.gitignore{{< /highlight >}} 檔案，並放進專案目錄頂層，如果你不確定 {{< highlight text "hl_inline=true" >}}.gitignore{{< /highlight >}} 檔裡面要寫什麼，以下內容適合 Hugo 專案，供你參考：

```text
# Hugo
/public/
/resources/_gen/
/assets/jsconfig.json
hugo_stats.json
/.hugo_build.lock

hugo.exe
hugo.darwin
hugo.linux

# Node modules
node_modules/
```

> [!TIP] 不習慣用終端機操作 Git？
> 1. 如果你尚未適應終端機，最直觀的方式就是安裝 [GitHug Desktop](https://docs.github.com/zh/desktop/overview/about-github-desktop)，然後將已 {{< highlight shell "hl_inline=true" >}}git init{{< /highlight >}} 的工作目錄[加進](https://docs.github.com/zh/desktop/adding-and-cloning-repositories/adding-a-repository-from-your-local-computer-to-github-desktop) GitHub Desktop，接下來便可透過圖形化介面進行 Git 操作。
> 2. 在 GitHub Desktop 內，從[視窗左上角](https://docs.github.com/zh/desktop/overview/creating-your-first-repository-using-github-desktop#github-desktop-存储库栏)的「Current Repository」確認你正開著專案目錄的 repo，接著從上方工具列選擇「Repository」>「Repository Settings...」，彈出的對話框左側即可選擇編輯 {{< highlight text "hl_inline=true" >}}.gitignore{{< /highlight >}} 檔，此時再將上面提供的文字貼進去即可。
> 3. Git 方面使用 GitHub Desktop 沒有問題，但將來還是會有其他 Hugo 相關的操作無法避開終端機。

此時 Hugo 專案目錄已準備好，可開始安裝佈景主題。


---

## 安裝佈景主題 {id="install-theme"}


安裝 Hugo 佈景主題有多種方式，但由於佈景主題需要 Tailwind CSS，所以請先依照下列步驟，使用 {{< highlight text "hl_inline=true" >}}npm{{< /highlight >}} 安裝 Tailwind。

> [!NOTE]
> 以下操作手續來自 Hugo 官方[文件](https://gohugo.io/functions/css/tailwindcss/#setup)，可放心使用，若有更動以官網資訊為準。

1. 在終端機內，{{< highlight shell "hl_inline=true" >}}cd{{< /highlight >}} 進入 Hugo 專案目錄，並執行：

    ```shell {linenos=true data-prompt=true}
    npm install --save-dev tailwindcss @tailwindcss/cli
    ```

    此指令將在你的專案目錄內安裝 Tailwind 套件。

2. 進入 Hugo 專案目錄，打開裡面的 hugo.toml 檔，並在檔案內添加以下內容：

    ```toml
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
    ```

    這樣做的目的是告訴 Hugo 如何和 Tailwind 合作。

此時 Tailwind 已設定完成，接著要安裝 Neso 佈景主題本身，以下列出其中兩種方法：[Hugo Modules](#install-via-modules)、或[手動安裝](#install-manually)。


### 透過 Hugo Modules 安裝 (推薦) {id="install-via-modules"}

> [!IMPORTANT]
> Neso 佈景主題需要 Hugo `v0.150.0` 或以上的版本。

以此方式安裝佈景主題的好處是更新方便、且能保持專案目錄乾淨，因為 Hugo 會直接從 Neso 的 GitHub 拉取佈景主題的原始檔，你不需要自行管理。

1. 在終端機內，{{< highlight shell "hl_inline=true" >}}cd{{< /highlight >}} 進入 Hugo 專案目錄，執行下列指令，來將你的專案初始化為 Hugo module：

    ```shell {linenos=true data-prompt=true}
    hugo mod init github.com/<你的 GitHub 使用者名稱>/<你的 repo 名稱>
    ```

    舉例來說，假設你的 Hugo 專案將來上傳到 GitHub 的 repo 名稱是 `mysite`、而你的 GitHub 使用者名稱是 `ghuser-blah`，那麼你就可以這樣下指令：

    ```shell {linenos=true data-prompt=true}
    hugo mod init github.com/ghuser-blah/mysite
    ```

    此操作無害，僅僅是一個準備動作，如果你不想輸入上述資訊，也可以隨意取名 (英數不要有空白)：

    ```shell {linenos=true data-prompt=true}
    hugo mod init mysite
    ```

2. 接著編輯專案目錄裡面的 hugo.toml 檔：

    在稍早 Tailwind 設定的 {{< highlight toml "hl_inline=true" >}}[module]{{< /highlight >}} 表頭下新增 {{< highlight toml "hl_inline=true" >}}[[module.imports]]{{< /highlight >}}，並照著輸入下列範例的 {{< highlight toml "hl_inline=true" >}}path = "..."{{< /highlight >}} 參數。

    ```toml {hl_lines="5-7"}
      # 其他設定...
      [[build.cachebusters]]
        source = '(postcss|tailwind)\.config\.js'
        target = 'css'
    [module]
      [[module.imports]]
        path = "github.com/babeneso/hugo-neso" # 必須是這個網址
      [[module.mounts]]
        source = 'assets'
        # 其他設定...
    ```

3. 在專案內執行以下指令，拉取 Github 上的佈景主題的最新版原始檔：

    ```shell {linenos=true data-prompt=true}
    hugo mod get -u github.com/babeneso/hugo-neso
    ```

    (日後要更新也是使用這個指令)

    如果你想鎖定在 / 更新到[特定版本](https://github.com/babeneso/hugo-neso/releases) (範例為鎖定 `v0.1.1`)：

    ```shell {linenos=true data-prompt=true}
    hugo mod get github.com/babeneso/hugo-neso@v0.1.1
    ```

4. 建議再順手執行這個指令，清理不必要的資訊：

    ```shell {linenos=true data-prompt=true}
    hugo mod tidy
    ```

5. 最後執行以下指令，讓 Hugo 啟動本地伺服器 (用來預覽你的網站)：

    ```shell {linenos=true data-prompt=true}
    hugo server
    ```

    沒有問題的話，Hugo 應該會吐給你一個 `http://localhost:xxxx/` 網址，如果你還沒有發表任何內容，連上去會看到空的頁面，這樣就代表完成了。



### 手動安裝 {id="install-manually"}

> [!IMPORTANT]
> Neso 佈景主題需要 Hugo `v0.150.0` 或以上的版本。

1. 從[此處](https://github.com/babeneso/hugo-neso/releases)下載佈景主題的原始檔 ZIP 壓縮包，並解壓縮。

    將含有佈景主題原始檔的資料夾命名為 {{< highlight text "hl_inline=true" >}}hugo-neso{{< /highlight >}}，放到你專案目錄的 {{< highlight text "hl_inline=true" >}}themes/{{< /highlight >}} 裡：

    ```text
    mysite/   <- 你的 Hugo 專案目錄
    ├── ...
    ├── themes/
    │   └── hugo-neso/  <- Neso 佈景主題
    │       ├── assets/
    │       ├── i18n/
    │       ├── layouts/
    │       ├── hugo.toml
    │       └── ...
    └── ...
    ```

2. 編輯你稍早設定 Tailwind 的那個 hugo.toml 檔 (☝️*不是* {{< highlight text "hl_inline=true" >}}hugo-neso/{{< /highlight >}} 裡面那個喔！)，在裡面添加 {{< highlight toml "hl_inline=true" >}}theme = "hugo-neso"{{< /highlight >}}：

    ```toml {hl_lines="7"}
    baseURL = 'https://example.org/'
    languageCode = 'en-us'
    title = 'My New Hugo Site'
    # 以上是 Hugo 為你產生的東西

    # 加在這裡比較安全，放下面容易報錯
    theme = "hugo-neso"

    # 以下是稍早的 Tailwind 設定
    [build]
      [build.buildStats]
        enable = true
      [[build.cachebusters]]
        source = 'assets/notwatching/hugo_stats\.json'
        target = 'css'
        # 其他設定...
    ```

3. 最後執行以下指令，讓 Hugo 啟動本地伺服器 (用來預覽你的網站)：

    ```shell {linenos=true data-prompt=true}
    hugo server
    ```

    沒有問題的話，Hugo 應該會吐給你一個 `http://localhost:xxxx/` 網址，如果你還沒有發表任何內容，連上去會看到空的頁面，這樣就代表完成了。
