---
title           : "Pages and Menu Setup"
date            : 2025-10-09T20:49:00+08:00
lastmod         : 2025-10-09T20:49:00+08:00
slug            : "pages-menu-setup"

description     : "The Neso theme provides tag and category pages, an Archives page, and an integrated search. Use this page to learn how to set up these pages and the site’s main menu."
summary         : "Set up the tag and category pages, the Archives page, search, and your site’s main menu."
keywords        : ["Hugo", "setup", "main menu", "categories", "tags", "search", "archives", "Theme", "Neso", "hugo-neso"]
tags            : ["hugo.toml", "Main Menu", "Categories", "Tags", "Search", "Archives", "Configuration"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
      hidden_in_single: true
---

> [!TIP]
> The homepage setup is documented separately; see [here]({{% ref "Params - Site/#homepage" %}}).

> [!NOTE]
> The author prefers **TOML** for the site-wide config and **YAML** for Front Matter. Please pay attention and convert formats as needed with your favorite tool.

---

## Search {id="search"}

In your site config hugo.toml, under the {{< highlight toml "hl_inline=true" >}}[outputs]{{< /highlight >}} table, add {{< highlight toml "hl_inline=true" >}}"json"{{< /highlight >}} to the `home` output formats:

```toml
[outputs]  # The `outputs` table lives at the top level of TOML
  home = ["html", "rss", "json"]  # Ask Hugo to emit a JSON index
```

This setting makes Hugo output your site’s index as JSON at the site root, which the search JavaScript consumes. For details on output formats, see Hugo’s official [docs](https://gohugo.io/configuration/outputs/).

Next, create {{< highlight text "hl_inline=true" >}}search.md{{< /highlight >}} under your project’s {{< highlight text "hl_inline=true" >}}content/{{< /highlight >}} directory and add the following Front Matter:

```yaml {hl_lines="2"}
---
layout          : "search"  # required
title           : "Search"
description     : "Use the Up/Down keys to select a result, then press Enter to open."
---

<!-- You can also write Markdown here if you want body content on the page -->
```

> [!IMPORTANT]
> The file must live at {{< highlight text "hl_inline=true" >}}content/search.md{{< /highlight >}} (top level).

> [!TIP]
> For multilingual sites, create one per language:
> 
> ```text
> content/
> ├── search.md     # default language
> ├── search.ja.md  # other locales
> └── ...
> ```


---

## Archives

Create {{< highlight text "hl_inline=true" >}}archives.md{{< /highlight >}} under {{< highlight text "hl_inline=true" >}}content/{{< /highlight >}}, and add the following Front Matter:

```yaml {hl_lines="2"}
---
layout          : "archives"  # required
title           : "Archives"
description     : "You can find all past content here."
---

<!-- You can also write Markdown here if you want body content on the page -->
```

> [!TIP]
> For multilingual sites, create one per language:
> 
> ```text
> content/
> ├── archives.md     # default language
> ├── archives.ja.md  # other locales
> └── ...
> ```


---

## Categories and Tags

When writing posts, add {{< highlight yaml "hl_inline=true" >}}categories = [...]{{< /highlight >}} and {{< highlight yaml "hl_inline=true" >}}tags = [...]{{< /highlight >}} in the Front Matter:

```yaml {hl_lines="6-7"}
---
title           : "Post title"
date            : 2025-08-14T01:01:00+08:00
description     : "SEO description"
summary         : "Post summary"
categories      : ["Some category", "Another category"]
tags            : ["tag-a", "tag-b"]

params:
  neso:
  # other settings...
---
```

Then see “[Set up the main menu](#menu-setup)” below to add the Category or Tag pages to your menu (optional).

> [!NOTE]
> `tags` and `categories` are just two default **taxonomies** that Hugo provides. You can define your own taxonomies for other kinds of classification. See [Taxonomy](https://gohugo.io/configuration/taxonomies/).

---

## Set up the main menu {id="menu-setup"}

Refer to Hugo’s official [Menu documentation](https://gohugo.io/configuration/menus/) for details. Below is an example that adds Tags, Categories, Search, and Archives to the main menu.

Add the following to your hugo.toml:

```toml
[menus]  # The `menus` table lives at the top level of TOML
  [[menus.main]]
    identifier = "posts"   # unique id
    name       = "Posts"   # text shown in the menu
    pageRef    = "/posts"  # your content section
    weight     = 10        # order (smaller appears earlier)
  [[menus.main]]
    identifier = "tags"
    name       = "Tags"
    pageRef    = "/tags"   # your taxonomy: tags, categories, etc.
    weight     = 20
  [[menus.main]]
    identifier = "categories"
    name       = "Categories"
    pageRef    = "/categories"  # your taxonomy: tags, categories, etc.
    weight     = 30
  [[menus.main]]
    identifier = "archives"
    name       = "Archives"
    pageRef    = "/archives"  # archives page
    weight     = 40
  [[menus.main]]
    identifier = "search"
    name       = "Search"
    pageRef    = "/search"  # search page
    weight     = 50
  [[menus.main]]
    identifier = "github"
    name       = "GitHub"
    url        = "https://github.com/babeneso"  # external link
    weight     = 60
```

> [!IMPORTANT]
> While `name` alone works, it is **strongly recommended** to set an [`identifier`](https://gohugo.io/configuration/menus/#identifier).
> 
> For **internal links**, prefer [`pageRef`](https://gohugo.io/configuration/menus/#pageref) and point to the page’s [logical path](https://gohugo.io/quick-reference/glossary/#logical-path) instead of using `url`.
> 
> Use `url` for **external links** only, not `pageRef`.

> [!NOTE]
> For multilingual menus, see Hugo’s docs [here](https://gohugo.io/content-management/multilingual/#menus), or use this demo site’s [hugo.toml](https://github.com/babeneso/hugo-neso/blob/demo/hugo.toml) as a reference.

> [!WARNING] 🚧 TODO
> I should explain why Tags and Categories pages render correctly even without corresponding Markdown files, and add that here later.
