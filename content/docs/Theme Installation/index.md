---
title           : "Theme Installation"
date            : 2025-10-11T04:00:00+08:00
lastmod         : 2025-10-12T15:08:00+08:00
slug            : "installation"

description     : "This page shows how to install the Neso theme."
summary         : "This page shows how to install the Neso theme."
keywords        : ["setup guide", "hugo.toml", "Tailwind", "Hugo", "Markdown", "Theme", "Neso", "hugo-neso"]
tags            : ["hugo.toml", "Installation", "Tailwind"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
      hidden_in_single: true
---


## Prepare Hugo

If you already have Hugo installed — and perhaps a site running — feel free to skip to [**Install the theme**](#install-theme) below.

If you have not used Hugo yet, the following is a brief walkthrough to get your first Hugo site ready.


### Install Hugo {id="install-hugo"}

Follow the official installation [guide](https://gohugo.io/installation/) to install Hugo.

> [!IMPORTANT] Read this first
> 1. Before installing Hugo, you **must** install the prerequisites listed on that page: **Git** and **Go**.
> 2. Hugo ships in three variants (not operating systems): *standard*, *extended*, and *extended/deploy*. Please install the **extended** variant.
> 3. Hugo offers multiple installation methods. On macOS, it is recommended to use [Homebrew](https://gohugo.io/installation/macos/#homebrew). (The author is not familiar with Windows; please consult the official docs.)
> 4. The Neso theme requires Hugo **v0.150.0 or newer**.

After installing **Git**, **Go**, and **Hugo (extended)** in that order, verify in your terminal:

```shell {linenos=true data-prompt=true}
hugo version
```

If you see Hugo’s version information, your environment is good to go.


### Create a Hugo site {id="new-site"}

Run the following commands in your terminal.

Move ({{< highlight shell "hl_inline=true" >}}cd{{< /highlight >}}) to your working directory, then run:

```shell {linenos=true data-prompt=true}
hugo new site mysite
```

This creates a folder named {{< highlight text "hl_inline=true" >}}mysite{{< /highlight >}} (you can choose any name; we will call it the “Hugo project directory” below) and populates it with the basic files for a site.

Then {{< highlight shell "hl_inline=true" >}}cd{{< /highlight >}} into that directory:

```shell {linenos=true data-prompt=true}
cd mysite
```

Initialize a Git repository in the project directory:

```shell {linenos=true data-prompt=true}
git init
```

At this point, create a {{< highlight text "hl_inline=true" >}}.gitignore{{< /highlight >}} at the project root. If you are unsure what to include, the following is a good starting point for Hugo projects:

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

> [!TIP] Prefer a GUI over the terminal for Git?
> 1. If you are not comfortable with the terminal, install [GitHub Desktop](https://docs.github.com/en/desktop/overview/about-github-desktop). Then [add](https://docs.github.com/en/desktop/adding-and-cloning-repositories/adding-a-repository-from-your-local-computer-to-github-desktop) your working directory (which you already ran {{< highlight shell "hl_inline=true" >}}git init{{< /highlight >}} on) into GitHub Desktop and proceed with a visual workflow.
> 2. In GitHub Desktop, confirm the repo from **Current Repository** at the [top left](https://docs.github.com/en/desktop/overview/creating-your-first-repository-using-github-desktop#the-github-desktop-repository-bar) of the window. Then choose **Repository → Repository Settings…** from the menu; you can edit {{< highlight text "hl_inline=true" >}}.gitignore{{< /highlight >}} in the left sidebar of the dialog and paste the above rules.
> 3. Using GitHub Desktop is fine for Git operations. However, some Hugo tasks still require the terminal.

Your Hugo project directory is now ready to install the theme.


---

## Install the theme {id="install-theme"}


There are multiple ways to install a Hugo theme. Because this theme integrates Tailwind CSS, please install Tailwind via {{< highlight text "hl_inline=true" >}}npm{{< /highlight >}} first.

> [!NOTE]
> The following steps come from Hugo’s official [docs](https://gohugo.io/functions/css/tailwindcss/#setup). If anything changes, the official docs take precedence.

1. In your terminal, {{< highlight shell "hl_inline=true" >}}cd{{< /highlight >}} into the Hugo project directory and run:

    ```shell {linenos=true data-prompt=true}
    npm install --save-dev tailwindcss @tailwindcss/cli
    ```

    This installs Tailwind packages inside your project directory.

2. Open `hugo.toml` in your Hugo project directory and add the following:

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

    This tells Hugo how to work with Tailwind.

Tailwind is now configured. Next, install the Neso theme itself using one of two methods: [Hugo Modules](#install-via-modules) (recommended) or [Manual installation](#install-manually).


### Install via Hugo Modules (recommended) {id="install-via-modules"}

This approach keeps your project clean and makes updates easy: Hugo fetches the theme source directly from GitHub so you do not have to manage it yourself.

> [!IMPORTANT]
> The Neso theme requires Hugo **v0.150.0 or newer**.

1. In your terminal, {{< highlight shell "hl_inline=true" >}}cd{{< /highlight >}} into the Hugo project directory and initialize your project as a Hugo module:

    ```shell {linenos=true data-prompt=true}
    hugo mod init github.com/<your GitHub username>/<your repo name>
    ```

    For example, if your repo name is `mysite` and your GitHub username is `ghuser-blah`, you can run:

    ```shell {linenos=true data-prompt=true}
    hugo mod init github.com/ghuser-blah/mysite
    ```

    This step is harmless and serves as preparation. If you prefer not to use your GitHub info yet, you can use any placeholder name (letters/digits, no spaces):

    ```shell {linenos=true data-prompt=true}
    hugo mod init mysite
    ```

2. Edit `hugo.toml` in your project directory:

    Under the {{< highlight toml "hl_inline=true" >}}[module]{{< /highlight >}} table you added for Tailwind, add a {{< highlight toml "hl_inline=true" >}}[[module.imports]]{{< /highlight >}} entry with the following path:

    ```toml {hl_lines="5-7"}
      # other settings...
      [[build.cachebusters]]
        source = '(postcss|tailwind)\.config\.js'
        target = 'css'
    [module]
      [[module.imports]]
        path = "github.com/babeneso/hugo-neso" # must be this path
      [[module.mounts]]
        source = 'assets'
        # other settings...
    ```

3. Run the following command in your project to fetch the latest theme sources from GitHub:

    ```shell {linenos=true data-prompt=true}
    hugo mod get -u github.com/babeneso/hugo-neso
    ```

    (Use this same command later when you want to update.)

    If you prefer to pin or update to a [specific release](https://github.com/babeneso/hugo-neso/releases) (example pins to `v0.1.2`):

    ```shell {linenos=true data-prompt=true}
    hugo mod get github.com/babeneso/hugo-neso@v0.1.2
    ```

4. It’s a good idea to run the next command to clean up unused entries in go.mod and go.sum:

    ```shell {linenos=true data-prompt=true}
    hugo mod tidy
    ```

5. Finally start the local server to preview your site:

    ```shell {linenos=true data-prompt=true}
    hugo server
    ```

    If everything is correct, Hugo prints a `http://localhost:xxxx/` URL. If you have not published any content yet, you will see an empty page, that means the setup succeeded.



### Manual installation {id="install-manually"}

> [!IMPORTANT]
> The Neso theme requires Hugo **v0.150.0 or newer**.

1. Download the theme ZIP from [here](https://github.com/babeneso/hugo-neso/releases) and extract it.

    Rename the folder containing the theme source to {{< highlight text "hl_inline=true" >}}hugo-neso{{< /highlight >}} and place it under {{< highlight text "hl_inline=true" >}}themes/{{< /highlight >}} in your project:

    ```text
    mysite/   <- your Hugo project directory
    ├── ...
    ├── themes/
    │   └── hugo-neso/    <- the Neso theme
    │       ├── assets/
    │       ├── i18n/
    │       ├── layouts/
    │       ├── hugo.toml
    │       └── ...
    └── ...
    ```

2. Edit the same `hugo.toml` where you configured Tailwind earlier (☝️ **not** the one inside {{< highlight text "hl_inline=true" >}}hugo-neso/{{< /highlight >}}) and add {{< highlight toml "hl_inline=true" >}}theme = "hugo-neso"{{< /highlight >}}:

    ```toml {hl_lines="7"}
    baseURL = 'https://example.org/'
    languageCode = 'en-us'
    title = 'My New Hugo Site'
    # The above lines are generated by Hugo

    # Safer to place it here—putting it lower can cause errors
    theme = "hugo-neso"

    # Tailwind settings from earlier
    [build]
      [build.buildStats]
        enable = true
      [[build.cachebusters]]
        source = 'assets/notwatching/hugo_stats\.json'
        target = 'css'
        # other settings...
    ```

3. Finally start the local server to preview your site:

    ```shell {linenos=true data-prompt=true}
    hugo server
    ```

    If everything is correct, Hugo prints a `http://localhost:xxxx/` URL. If you have not published any content yet, you will see an empty page, that means the setup succeeded.
