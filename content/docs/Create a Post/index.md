---
title           : "Create a Post"
date            : 2025-10-10T19:01:49+08:00
lastmod         : 2025-10-10T19:01:49+08:00
slug            : "create-post"

description     : "This page explains a recommended way to organize your posts, the suggested Front Matter, and a reusable archetype template."
summary         : "This page explains a recommended way to organize your posts, the suggested Front Matter, and a reusable archetype template."
keywords        : ["setup guide", "hugo.toml", "Front Matter", "Hugo", "Markdown", "Theme", "Neso", "hugo-neso"]
tags            : ["hugo.toml", "Front Matter"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
      hidden_in_single: true
---


## Page Bundle

When publishing a post, it is recommended to create a **dedicated folder per post**, and put the Markdown file for the post body (**must be named** `index.md`) **together** with all assets used by that post (images, cover, etc.) inside that folder.

Such a “post package” is called a **[Leaf Bundle](https://gohugo.io/content-management/page-bundles/#leaf-bundle)**.

```text
mysite/    <- Hugo project directory
├── ...
├── content/       <- content directory
│   ├── _index.md      <- top-level _index.md under /content is the homepage
│   │
│   └── posts/         <- this is a Section (a top-level category; also called a branch bundle)
│       │
│       ├── foo/           <- a leaf bundle (a post and its assets)
│       │   ├── index.md   <- the post body inside the bundle
│       │   └── cover.jpg  <- an asset packaged with the post
│       │
│       └── bar/           <- another leaf bundle (another post)
│           └── index.md
├── data/
├── i18n/
└── ...
```


## Create a Post

When you want to publish a post, open a terminal, `cd` to your Hugo project directory, and run:

```shell {linenos=true data-prompt=true}
hugo new <section name>/'<post title>'/index.md
```

For example:

```shell {linenos=true data-prompt=true}
hugo new posts/'Mochis Happy Day'/index.md
```

Hugo will create a `Mochis Happy Day/` leaf bundle folder, place an `index.md` inside, and automatically prefill the Front Matter (such as the title) at the start of the Markdown file.

Using the terminal is only one option; Hugo does not prevent you from creating the folder structure manually.

For the available Front Matter fields, see:

- [Fields provided by Hugo](https://gohugo.io/content-management/front-matter/#fields)
- [Fields provided by the Neso theme]({{% ref "Params - Front Matter" %}})


## Archetype

The `hugo new …` command is convenient because you can design a **template** for the Markdown file and put the commonly used Front Matter there. You will not need to look up parameters and copy‑paste them every time.

The most intuitive way is to try it once. Copy the following content and **overwrite** the `default.md` under `archetypes/` in your current Hugo project directory.

```yaml
---
title           : "{{ .File.ContentBaseName | humanize | replaceRE `\s+` " " | title }}"
date            : {{ .Date }}
slug            : "{{ .File.ContentBaseName | urlize }}"  # slug (URL segment) for this post

description     : "Enter the post description (a short SEO-friendly blurb)"
summary         : "Enter a brief summary of the post (used in list previews)"
keywords        : ["SEO keyword 1", "SEO keyword 2", "SEO keyword 3"]
tags            : ["tag a", "tag b", "tag c"]

params:
  neso:
    show_toc   : false  # show the table of contents
    cover:     # cover image settings (remove this whole block if you have no cover)
      image    : "<cover image URL>"  # just put the filename if the cover lives in the same bundle as the md
      caption  : "<cover caption>"    # optional; shown under the cover image
      alt_text : "<cover alt text>"   # optional; accessibility text
---

The main Markdown content starts here.
```

After saving, try this in the project directory:

```shell {linenos=true data-prompt=true}
hugo new posts/'Mochi Essay'/index.md
```

You will see that Hugo creates the post Markdown with important data filled in, and the suggested settings listed for you to edit.

The `default.md` under `archetypes/` is the template file. The `hugo new` command uses that template for new posts (the `{{ ... }}` are Hugo template expressions that insert values).
