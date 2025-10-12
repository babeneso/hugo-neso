---
title           : "Basic Configuration"
date            : 2025-10-10T13:30:10+08:00
lastmod         : 2025-10-10T13:30:10+08:00
slug            : "basic-config"

description     : "This page describes the basic configuration you should prepare after installing the Neso theme."
summary         : "This page describes the basic configuration you should prepare after installing the Neso theme."
keywords        : ["setup guide", "hugo.toml", "favicon", "Tailwind", "Hugo", "Markdown", "Theme", "Neso", "hugo-neso"]
tags            : ["hugo.toml", "Configuration", "Favicon"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
      hidden_in_single: true

---


If your Hugo project is brand new (just created with {{< highlight shell "hl_inline=true" >}}hugo new site{{< /highlight >}}), the initial site config hugo.toml only contains:

```toml
baseURL = 'https://example.org/'
languageCode = 'en-us'
title = 'My New Hugo Site'
```

If your project has been in use for a while, it may already include other custom settings.

In all cases, several settings are **required** by the Neso theme. Please read the notes below and add or adjust these parameters in your hugo.toml accordingly.


---

## Required (and recommended) settings

The following settings ensure the theme works correctly (some may have been added during installation).

```toml
# General
# --------------------------------

# Required: your site’s base URL
baseURL = "https://example.org/"
# Required: your site’s primary language code
languageCode = "en-us"
# Required: your site title
title = "My New Hugo Site"

# Required: select the theme
# If you installed the theme via Hugo Modules, you may remove this key
theme = "hugo-neso"


# Build
# --------------------------------

[minify]
  # Recommended: minify the generated output to improve page load time
  minifyOutput = true

# Required: Tailwind integration — start
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
# Required: Tailwind integration — end
  
  # Required (when installing the theme via Hugo Modules): import the theme
  # If you installed the theme by other means, remove this block
  [[module.imports]]
    path = "github.com/babeneso/hugo-neso"


# Markdown
# --------------------------------

[markup]
  [markup.goldmark]
    [markup.goldmark.parser]
      # Recommended: do not wrap <img> in <p> (the theme provides proper spacing)
      wrapStandAloneImageWithinParagraph = false

      [markup.goldmark.parser.attribute]
        # Required: enable attributes on block elements
        block = true

    [markup.goldmark.renderer]
      # Recommended: allow raw HTML in Markdown
      unsafe = true

  [markup.highlight]
    # Required: use CSS classes for code blocks so syntax highlighting works
    noClasses = false

  # Recommended: table of contents levels
  [markup.tableOfContents]
    startLevel = 2
    endLevel = 3
```


---

## Other important settings

Below are settings you will encounter as you further customize the theme. You do not need to configure them immediately; this section provides context for when you get there.


### Favicon

Place your favicon in the following locations (provide both {{< highlight text "hl_inline=true" >}}ICO{{< /highlight >}} and {{< highlight text "hl_inline=true" >}}SVG{{< /highlight >}}):

- {{< highlight text "hl_inline=true" >}}static/favicon.ico{{< /highlight >}} (recommended 64×64)
- {{< highlight text "hl_inline=true" >}}assets/favicon.svg{{< /highlight >}}

If you use these exact paths and filenames, the icons will take effect immediately and will be automatically injected into the page {{< highlight html "hl_inline=true" >}}<head>{{< /highlight >}} element.

If you prefer other filenames or locations, that is also fine; see the [branding settings]({{% ref "Params - Site/#branding" %}}).


### Outputs

If you plan to provide RSS for readers (Hugo enables it by default; see [setting 1]({{% ref "Params - Site/#general-settings" %}}) and [setting 2]({{% ref "Params - Site/#list-settings" %}})), or use the built‑in [site search]({{% ref "Pages and Menu Setup/#search" %}}), you need to adjust the following:

```toml
# Outputs
# --------------------------------

[outputs]
  home = ["html", "rss", "json"]
  # other outputs...
```


### Main menu

When configuring your site’s navigation [main menu]({{% ref "Pages and Menu Setup/#menu-setup" %}}), you will encounter settings like:

```toml
# Main menu
# --------------------------------

[menus]
  [[menus.main]]
    identifier = 'posts'
    name       = 'Posts'   # text shown in the menu
    pageRef    = '/posts'  # your content section
    weight     = 10        # smaller appears earlier
  [[menus.main]]
    identifier = 'tags'
    name       = 'Tags'
    pageRef    = '/tags'
    weight     = 20
  # other main menu items...
```


### Other theme options

The Neso theme provides many [additional options]({{% ref "Params - Site" %}}). They live under the `[params.neso]` table:

```toml
# Parameters
# --------------------------------

[params]
  [params.neso]
  # Neso theme options...
```
