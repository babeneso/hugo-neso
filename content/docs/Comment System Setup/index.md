---
title           : "Comment System Setup"
date            : 2025-10-09T19:57:51+08:00
lastmod         : 2025-10-09T19:57:51+08:00
slug            : "comment-setup"

description     : "Hugo is a static site generator, but you can still add a comment system through various vendors and free services."
summary         : "Hugo is a static site generator, but you can still add a comment system through various vendors and free services."
keywords        : ["Hugo", "comment system", "comments", "Disqus", "Theme", "Neso", "hugo-neso"]
tags            : ["hugo.toml", "Comments", "Configuration"]

params:
  neso:
    cover:
      image           : "cover.png"
      hidden_in_single: true

---

## Setup

Please start with the Hugo [official docs](https://gohugo.io/content-management/comments/) to understand how to integrate a comment system. The docs include a quick setup for Disqus and list other mainstream options for easy reference.

When you are ready to insert the template code required by your chosen provider, download **comments.html** from the Neso GitHub repo: [comments.html](https://github.com/babeneso/hugo-neso/blob/main/layouts/_partials/content/comments.html).

After adding your code, place the file under your project at: {{< highlight text "hl_inline=true" >}}layouts/_partials/content/comments.html{{< /highlight >}}.

If the directories do not exist, please create them.
