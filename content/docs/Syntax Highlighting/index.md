---
title           : "Using the Syntax Highlighter"
date            : 2025-10-09T09:31:00+08:00
lastmod         : 2025-10-09T09:31:00+08:00
slug            : "syntax-highlighting"

description     : "Hugo ships with the built-in code syntax highlighter “Chroma”, which works without third‑party libraries. The Neso theme optimizes its presentation and adds a few small improvements."
summary         : "Hugo includes the Chroma syntax highlighter; no third‑party library is required. This theme optimizes its presentation and adds a few small improvements. Please configure it as described on this page."
keywords        : ["Hugo", "Markdown", "Code", "Chroma", "Syntax Highlighting", "Customization", "Theme", "Neso", "hugo-neso"]
tags            : ["hugo.toml", "Chroma", "Syntax Highlighting", "Markdown", "Configuration"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
      hidden_in_single: true
---


## About syntax highlighting

If you are using Hugo to build your site, you likely have plenty of code knowledge to share with the world. Hugo ships with a built-in syntax highlighter, [Chroma](https://github.com/alecthomas/chroma), so you do not need any third‑party libraries. This theme optimizes its presentation and adds a few small improvements. Please configure it as described on this page.


## Configuration

Make sure your site config hugo.toml includes the following:

```toml {hl_lines=[3]}
[markup]               # The `markup` table lives at the top level of TOML
  [markup.highlight]   # The `highlight` sub-table
    noClasses = false
```

Basically, that is all you need. For the curious:

- **{{< highlight toml "hl_inline=true" >}}noClasses = false{{< /highlight >}} is required.**

    By default, Hugo uses inline CSS to colorize code blocks. That approach makes customization difficult. Set this option so styles are applied via classes instead.

- **Hugo’s [official docs](https://gohugo.io/configuration/markup/#highlight) list other options; please keep the defaults.**
    
    In other words, do not add additional options under {{< highlight toml "hl_inline=true" >}}[markup.highlight]{{< /highlight >}} in your site hugo.toml. Those options are better specified per code block within your content.


## Getting started

There are several ways to display code in Markdown.

### Block code (fenced code blocks)

Wrap your code with three backticks <kbd>\`</kbd> at the beginning and end (each on its own line), like this:

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

Rendered result:

```
package main

import "fmt"

func main() {
    for i := 0; i < 3; i++ {
        fmt.Println("Value of i:", i)
    }
}
```

As you can see, there is no syntax highlighting yet, because this is native Markdown. To enable highlighting, add parameters after the first set of backticks:

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

The `go` after the opening backticks is the [language identifier](https://gohugo.io/content-management/syntax-highlighting/#languages). You can follow it with a pair of braces `{}` to set additional, optional parameters:

`linenos=true`
: Show line numbers.

`hl_lines=[3,"6-8"]`
: Lines to highlight (emphasize).

`lineNoStart=2`
: Starting line number; if omitted, numbering begins at 1 (this does not affect the highlighting ranges above).

After adding these, the rendered result looks like this:

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
> Other options mentioned in Hugo’s [docs](https://gohugo.io/content-management/syntax-highlighting/#options-1) are not recommended here because they rely on inline CSS and will cause display issues in this theme.

> [!IMPORTANT]
> Syntax highlighting does not work for code shown via indentation in Markdown.

The Neso theme additionally provides a `data-prompt` option. Together with `linenos=true`, it replaces line numbers with a terminal prompt symbol so that users will not accidentally copy the prompt when copying code.

{{< highlight text "hl_lines=1" >}}
```shell {linenos=true data-prompt=true}
hugo server
```
{{< /highlight >}}

```shell {linenos=true data-prompt=true}
hugo server
```

In fact, `data-prompt` can be any symbol you specify:

{{< highlight text "hl_lines=1" >}}
```shell {linenos=true data-prompt="🔥"}
hugo server
```
{{< /highlight >}}

```shell {linenos=true data-prompt="🔥"}
hugo server
```


### Inline code

Use a pair of backticks <kbd>\`</kbd> to show inline code, like this: `const number = 42;`. However, the native approach does not apply syntax highlighting. If you want an effect like this {{< highlight javascript "hl_inline=true" >}}const number = 42;{{< /highlight >}}, see the instructions [here]({{% ref "Shortcodes/#chroma" %}}).

---


## Customize the highlighting theme

The theme ships with built‑in styles for both light and dark modes, but you can switch to other style packs.

1. **Generate the style pack CSS file**

    Open your terminal and run the [`hugo gen chromastyles`](https://gohugo.io/commands/hugo_gen_chromastyles/#hugo-gen-chromastyles) command:

    ```shell {linenos=true data-prompt=true}
    hugo gen chromastyles --style=monokai > syntax.css
    ```
    
    Set the `--style` option to any [style identifier](https://gohugo.io/quick-reference/syntax-highlighting-styles/). The command will create `syntax.css` in your terminal’s current working directory.

2. **Override the theme’s CSS**
   
    The theme supports both light mode (default) and dark mode. The syntax highlighting style sheets it uses are named **syntax-light.css** and **syntax-dark.css**.
    
    After you generate your CSS in the previous step, rename it to these two filenames and place them under your Hugo project’s **assets/css/chroma/** directory (create the `css` and `chroma` folders if they do not exist), i.e.,

    - assets/css/chroma/syntax-light.css
    - assets/css/chroma/syntax-dark.css

    Hugo will then prefer your files over the theme’s built‑in CSS.
