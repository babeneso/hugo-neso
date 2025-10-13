---
title           : "{{ .File.ContentBaseName | humanize | replaceRE `\s+` " " | title }}"
linkTitle       : "{{ .File.ContentBaseName | humanize | replaceRE `\s+` " " | title }}"
description     : ""    # short blurb shown under the page title, also for SEO
summary         : ""    # used in list previews

keywords        : ["SEO keyword 1", "SEO keyword 2", "SEO keyword 3"]
tags            : ["tag a", "tag b", "tag c"]
categories      : []

date            : {{ .Date }}
lastmod         : {{ .Date }}
draft           : true

slug            : "{{ .File.ContentBaseName | urlize }}"  # URL segment for this post

params:
  neso:
    cover:      # cover image (remove this whole block if you have no cover)
      image     : "<abs or rel URL>"  # rel URL = relative to page bundle .md
      caption   : ""                  # optional; shown under the cover image
      alt_text  : ""                  # optional; accessibility text
---

↓ Text before the "more" marker below is used for content previews.
  (if present, it overrides the front matter `summary`).
<!--more-->
The main content starts here.
