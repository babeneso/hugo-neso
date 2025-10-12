---
title           : "Get Started"
date            : 2025-10-11T06:21:30+08:00
lastmod         : 2025-10-11T06:21:30+08:00
slug            : "get-started"

description     : "Learn how to install and start using the Neso theme in a few steps, while understanding Hugo’s basics."
summary         : "Install Neso and get running in a few steps: first understand hugo.toml and Front Matter, then complete installation, posting, and basic configuration."
keywords        : ["setup guide", "hugo.toml", "Front Matter", "Hugo", "Markdown", "Theme", "Neso", "hugo-neso"]
tags            : ["hugo.toml", "Front Matter", "Configuration", "Installation"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
      hidden_in_single: true
---

## Welcome!

This page will help you:
1. Understand **hugo.toml** and **Front Matter**, which you will use frequently in Hugo.
2. Learn this documentation’s **format conventions**: site‑wide configuration uses TOML; Front Matter uses YAML.
3. Complete three steps in order: **install the theme** → **publish a post** → **basic & detailed configuration**.


---

## What is hugo.toml

1. `hugo.toml` is the **site‑wide configuration** file. It covers languages, navigation menus, themes, and advanced features.
2. Many [options](https://gohugo.io/configuration/all/) built into Hugo are structural (rather than visual). For that reason, the Neso theme adds options for customization (for example Tailwind integration, syntax highlighting, menus, etc.).
3. In earlier projects the config filename was often config, such as config.toml. Today it is recommended to use a single file **hugo.toml** at the project root.
4. [TOML](https://en.wikipedia.org/wiki/TOML) is a format commonly used for configuration files. In this documentation, whenever we discuss **site‑wide configuration**, we demonstrate it in **TOML**.

TOML looks like this:

```toml
baseURL = "https://example.org/"
languageCode = "en-us"
title = "My Site Title"

# Example: select the theme
theme = "hugo-neso"
```

> [!NOTE]
> For complete required and recommended settings, subsequent pages provide detailed explanations and links.


---

## What is Front Matter

1. Front Matter is the **metadata at the top of each Markdown file**. It describes the title, date, taxonomies, summary, etc.
2. Many [options](https://gohugo.io/content-management/front-matter/#fields) built into Hugo are basic metadata. For that reason, the Neso theme adds options for better content presentation (for example cover image, ToC, share buttons, etc.).
3. Hugo supports **TOML**, **YAML**, and **JSON**.
4. Like TOML above, [YAML](https://en.wikipedia.org/wiki/YAML) is simply another serialization format. In this documentation, whenever we discuss **Front Matter**, we demonstrate it in **YAML**.

YAML Front Matter looks like this:

```yaml
---
title       : "Post title"
date        : 2025-10-11T12:00:00+08:00
description : "A short SEO‑friendly description"
summary     : "The summary shown on list pages"
tags        : ["essay", "notes"]
---
```

> [!NOTE]
> For additional Front Matter options provided by Neso to enrich your content, later pages will provide detailed explanations and links.


---

## Start here

Follow these steps in order; each has a dedicated guide.

1. **Install the theme**
    Go to: **[Theme Installation]({{% ref "Theme Installation" %}})**
    Goal: install Neso theme and integrate Tailwind CSS to your Hugo project correctly.

2. **Publish your first post**
    Go to: **[Create a Post]({{% ref "Create a Post" %}})**
    Goal: learn to manage a post and its assets as a “leaf bundle”, and apply the recommended Front Matter.

3. **Complete the basic configuration**
    Go to: **[Basic Configuration]({{% ref "Basic Config" %}})**
    Goal: adjust the required and recommended hugo.toml parameters so the site behaves and looks correct.


---

## Next steps

- Browse other documentation pages to fine‑tune details: **pages and menu setup**, **shortcodes**, **syntax highlighting**, **custom styles**, **comment system**, and more.
- The main menu’s “[Docs]({{% ref "/docs" %}})” entry lists all pages; you can also use [tags]({{% ref "/tags" %}}) and [search]({{% ref "/search" %}}).
- For a complete list of settings, see: **[Params - Site]({{% ref "Params - Site" %}})** and **[Params - Front Matter]({{% ref "Params - Front Matter" %}})**.
