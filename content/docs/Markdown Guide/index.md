---
title           : "Markdown Guide"
date            : 2025-10-09T13:06:00+08:00
lastmod         : 2025-10-09T13:06:00+08:00
slug            : "markdown-guide"

description     : "Markdown is Hugo’s primary content format. This page lists common syntax and shows how it renders in the Neso theme."
summary         : "Markdown is Hugo’s primary content format. This page lists common syntax and shows how it renders in the Neso theme."
keywords        : ["Hugo", "Markdown", "syntax", "customization", "Theme", "Neso", "hugo-neso"]
tags            : ["Markdown", "Syntax Highlighting"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
---


## About Markdown

Markdown is a lightweight markup language designed for readability and writability. Hugo uses it as the default [content format](https://gohugo.io/content-management/formats/#markdown). This page demonstrates the actual rendered appearance under the Neso theme; it is not intended to be a complete tutorial.

You may also want to read the [Shortcodes]({{% ref "Shortcodes/" %}}) page for Neso’s extended embedding options.

---


## Headings

Avoid using **Heading 1** (`#`) inside Markdown body content; that level should be reserved for the page’s own title.

Markdown:

```text
# Heading 1
## Heading 2
### Example of a Heading 3
#### Heading 4: use sparingly
##### Heading 5 is rarely useful
###### Heading 6 looks like body text
```

Rendered result:

Heading 1
{class="asheading ash1"}

Heading 2
{class="asheading ash2"}

Example of a Heading 3
{class="asheading ash3"}

Heading 4: use sparingly
{class="asheading ash4"}

Heading 5 is rarely useful
{class="asheading ash6"}

Heading 6 looks like body text
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


## Paragraphs

Just type to create paragraphs. Separate paragraphs with a blank line. The following is dummy text for layout demonstration.

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.


---


## Bold and Italic

Wrap with a single asterisk `*` for *italic*, double asterisks `**` for **bold**, and triple for ***bold italic***; you can also use strikethrough with `~~deleted~~`.

Markdown:

```text
This is normal text with *italic*, **bold**, ***bold italic***, and ~~strikethrough~~.
```

Rendered result:

This is normal text with *italic*, **bold**, ***bold italic***, and ~~strikethrough~~.

---


## Blockquotes

Start a line with `>` to create a blockquote; consecutive lines are grouped automatically. Use `>>` (or another `>`) for nested quotes.

Markdown:

```text
> This is a single-level quote.
>
> It can span multiple paragraphs.
>
> > This is a nested quote (second level).
```

Rendered result:

> This is a single-level quote.
>
> It can span multiple paragraphs.
>
> > This is a nested quote (second level).


Neso also adds two enhancements for blockquotes:

### Enhancement: Quote attribution

Enable Markdown [attributes](https://gohugo.io/content-management/markdown-attributes/) in your hugo.toml:

```toml {hl_lines="5"}
[markup]
  [markup.goldmark]
    [markup.goldmark.parser]
      [markup.goldmark.parser.attribute]
        block = true
```

Then place `{author="Name" source="URL"}` on the line immediately after the quote:

```text
> This is a single-level quote.
{author="Neso" source="https://example.com"}
```

This renders an attribution and an optional source link:

> This is a single-level quote.
{author="Neso" source="https://example.com"}


### Enhancement: [GitHub Alerts](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#alerts)

```text
> [!NOTE]
> Useful information that users should know, even when skimming content.

> [!NOTE] Custom Title
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

Rendered result:

> [!NOTE]
> Useful information that users should know, even when skimming content.

> [!NOTE] Custom Title
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


## Lists

Use `-`, `*`, or `+` for **unordered lists**; use numbers with a period for **ordered lists**.

Markdown:

```text
- Unordered item A
- Unordered item B
    + Sub-item B-1
    + Sub-item B-2

1. Ordered item one
2. Ordered item two
3. Ordered item three

```

Rendered result:

- Unordered item A
- Unordered item B
    + Sub-item B-1
    + Sub-item B-2

1. Ordered item one
2. Ordered item two
3. Ordered item three

---


## Code: Block

Markdown: wrap code with three backticks <kbd>\`</kbd> at the beginning and end (each on its own line):

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

Use "[Chroma]({{% ref "Syntax Highlighting" %}})" to enable syntax highlighting:

```go {linenos=true hl_lines=[3,"6-8"] lineNoStart=2 wrapperClass="haha"}
package main

import "fmt"

func main() {
    for i := 0; i < 3; i++ {
        fmt.Println("Value of i:", i)
    }
}
```

Terminal prompt symbol:

```shell {linenos=true data-prompt=true}
hugo server
```

---


## Code: Inline

Wrap text with a single backtick <kbd>\`</kbd> to display inline code:

`const number = 42;`

Use the syntax-highlighting [shortcode]({{% ref "Shortcodes/#chroma" %}}):

{{< highlight javascript "hl_inline=true" >}}const number = 42;{{< /highlight >}}

---


## Horizontal rules

Three or more `-`, `*`, or `_` produce a horizontal rule.

Markdown:

```text
---
***
___
```

Rendered result (three rules):

---
***
___


---


## Links

Use `[text](URL "optional title")` for links.

Markdown:

```md
This is a link: [Hugo website](https://gohugo.io "Go to Hugo official website").
```

Rendered result:

This is a link: [Hugo website](https://gohugo.io "Go to Hugo official website").

---


## Images

Use `![alt text](path "optional title")`. The alt text helps with accessibility (a11y).

Markdown:

```md
![Béton brut residential facade](beton-brut.jpg "Photo by babeneso")
```

Rendered result:

![Béton brut residential facade](beton-brut.jpg "Photo by babeneso")

---


## Footnotes

Use `[^id]` to insert a footnote reference, and define it later in the document with `[^id]: text`.

Markdown:

```text
This sentence has a footnote[^1].

[^1]: This is the footnote text, and it can include **bold** and *italic* formatting.
```

Rendered result:

This sentence has a footnote[^1].

[^1]: This is the footnote text, and it can include **bold** and *italic* formatting.
