---
title           : "Theme Parameters (Front Matter)"
date            : 2025-10-06T14:53:12+08:00
lastmod         : 2025-10-06T14:53:12+08:00
draft           : false
slug            : "front-matter-params"

description     : "This page lists the theme's Front Matter parameters for per-page UI, cover images, and related options."
summary         : "This page lists the theme's Front Matter parameters for per-page UI, cover images, and related options."
keywords        : ["Hugo", "Parameters", "Settings", "Configuration", "Customization", "Theme", "Neso", "hugo-neso"]
tags            : ["Front Matter", "Configuration"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
      hidden_in_single: true
---

## About Front Matter

When preparing pages and posts in Hugo, you can provide metadata and per‑page options in the file’s Front Matter block. The theme’s Front Matter parameters are all nested under the `neso` namespace. For example, the following is a YAML Front Matter placed at the top of a Markdown file:

```yaml
---
title         : "A Cat’s Happy Day"
date          : 2025-10-06T14:53:12+08:00
description   : "This diary is written by the cat — no human interference."
# other fields omitted...
# The above are Hugo’s built‑in Front Matter fields (partial list)

params:
  # The following are this theme’s Front Matter parameters (partial list)
  neso:
    # all nested under the `neso` namespace
    author    : "Mochi"
    show_toc  : false
    cover:
      # Cover image options are nested one level deeper
      image   : "selfie.jpg"
      caption : "Cat selfie"
      # other fields omitted...
---

<!-- Main article/page content goes below -->
ddddddddddd,,,,,,,,,,,,,,,,,,,,,cfvsssssssszzzz
```

> [!TIP]
> The theme builds and works even if you do not use any of the `neso` parameters. Add them only when you need them.

> [!NOTE]
> The author prefers TOML for site‑wide config and YAML for Front Matter, so examples on this page use YAML.

---


## General settings

Write directly under `neso` (mind the indentation):

```yaml {hl_lines=["3-4"]}
params:
  neso:
    show_toc: true      # key / value
    toc_expanded: true  # key / value
    # omitted...
```


### Header metadata {id="metadata-settings"}

The header block displays metadata such as publish date, author(s), word count, and more.

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| Key | Type | Description |
| --- | :---: | --- |
| `author` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} {{< highlight text "hl_inline=true" >}}String[]{{< /highlight >}} | Author name. For a single person, provide a string (e.g., {{< highlight toml "hl_inline=true" >}}"Ada Lovelace"{{< /highlight >}}); for multiple people, provide an array of strings (e.g., {{< highlight toml "hl_inline=true" >}}["Alice", "Bob", "Carol"]{{< /highlight >}}). |
| `disable_author` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Turn off author info on this page (Note: this option can only turn the feature off. If the [site‑wide setting]({{% relref "Params - Site/#single-metadata" %}}) is already off, you cannot force it on here.) |
| `disable_reading_time` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Turn off reading‑time estimation on this page (Note: opt‑out only; if the [site‑wide setting]({{% relref "Params - Site/#single-metadata" %}}) is off, you cannot force it on.) |
| `disable_word_count` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Turn off word count on this page (Note: opt‑out only; if the [site‑wide setting]({{% relref "Params - Site/#single-metadata" %}}) is off, you cannot force it on.) |
| `canonical_url` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | If the post was originally published elsewhere, put the original URL here |
| `canonical_link_text` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | When showing the `canonical_url` link, prefix it with this default text; e.g., {{< highlight text "hl_inline=true" >}}Originally published on{{< /highlight >}} |
| `hide_metadata` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Hide the entire header block |

</div>


### Footer features {id="footer-settings"}

The footer block shows post tags, share buttons, and Previous/Next links for further reading.

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| Key | Type | Description |
| --- | :---: | --- |
| `show_prev_next` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Show "Previous / Next" links for further reading |
| `disable_share` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Turn off share buttons on this page (Note: opt‑out only; if the [site‑wide setting]({{% relref "Params - Site/#single-footer" %}}) is off, you cannot force it on here.) |
| `disable_content_footer` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Hide the entire footer block (Note: opt‑out only; if it is already hidden in the [site‑wide settings]({{% relref "Params - Site/#single-footer" %}}), you cannot force it to show here.) |

</div>


### Other settings {id="other-settings"}

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| Key | Type | Description |
| --- | :---: | --- |
| `disable_breadcrumbs` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Turn off the breadcrumb trail on this page (Note: opt‑out only; if the [site‑wide setting]({{% relref "Params - Site/#general-settings" %}}) is off, you cannot force it on here.) |
| `show_toc` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Show the Table of Contents |
| `toc_expanded` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Expand the Table of Contents by default |
| `disable_comments` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Turn off the comments block on this page (Note: opt‑out only; if the [site‑wide setting]({{% relref "Params - Site/#single-general" %}}) is off, you cannot force it on.) |
| `exclude_from_search` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Exclude this page from site search results |
| `block_indexing` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Set this page’s {{< highlight html "hl_inline=true" >}}<meta name="robots">{{< /highlight >}} to `noindex`, `nofollow` |

</div>

---


## Cover image

Write these settings under `neso` → `cover` (mind the indentation):

```yaml {hl_lines=["5-10"]}
params:
  neso:
    show_toc: true
    # other settings omitted...
    cover:
      image            : "meow.png"
      caption          : "Cute meow"
      alt_text         : "A black cat meowing"
      hidden_in_list   : false
      hidden_in_single : false
```

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| Key | Type | Description |
| --- | :---: | --- |
| `image` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Image URL; you can write a path relative to this content file, or an absolute path (root‑relative or full URL) |
| `caption` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Text shown below the cover image |
| `alt_text` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Alternative text for the cover image |
| `hidden_in_list` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Hide the cover image on post list pages |
| `hidden_in_single` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Hide the cover image on the single post page |

</div>
