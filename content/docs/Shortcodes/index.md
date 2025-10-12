---
title           : "Shortcodes"
date            : 2025-10-08T05:07:00+08:00
lastmod         : 2025-10-08T14:07:00+08:00
draft           : false
slug            : "shortcodes"

description     : "The Neso theme optimizes Hugo’s shortcodes to make your posts vivid and polished."
summary         : "Hugo provides several quick syntaxes beyond what Markdown supports, called \"shortcodes\". This theme fine‑tunes the appearance of those shortcodes."
keywords        : ["Hugo", "Shortcode", "Markdown", "HTML", "Syntax", "Chroma", "Customization", "Theme", "Neso", "hugo-neso"]
tags            : ["Shortcode", "Chroma", "Syntax Highlighting", "Markdown"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
      hidden_in_single: true
---


## About shortcodes

Hugo provides several quick syntaxes beyond what Markdown supports, called "shortcodes", which make it easy to insert/embed richer media in your content.

This theme fine‑tunes the appearance of those shortcodes. Below we show how they render in practice; for detailed usage, see the Hugo [documentation](https://gohugo.io/shortcodes/).

---

## HTML {{% highlight html "hl_inline=true" %}}<details>{{% /highlight %}} element

Insert the shortcode in Markdown:

```go-html-template
{{</* details summary="Details shortcode demo" */>}}
This is the content shown after expanding; you can also write **Markdown** here.
{{</* /details */>}}
```

Rendered result:

{{< details summary="Details shortcode demo">}}
This is the content shown after expanding; you can also write **Markdown** here.
{{< /details >}}

---

## HTML {{% highlight html "hl_inline=true" %}}<figure>{{% /highlight %}} element

Insert the shortcode in Markdown:

```go-html-template
{{</* figure
  src="img_demo.jpg"
  alt="Afternoon sunlight reflecting on the building’s glass facade"
  loading="lazy"
  title="HDR image test"
  caption="See the gleaming photo? Congrats! your browser supports HDR images! – Photo by "
  attr="babeneso"
  attrlink="https://instagram.com/babeneso"
*/>}}
{{/* Some attributes are optional; you don’t have to set them all. */}}
```

Rendered result:

{{< figure
  src="img_demo.jpg"
  alt="Afternoon sunlight reflecting on the building’s glass facade"
  loading="lazy"
  title="HDR image test"
  caption="See the gleaming photo? Congrats! your browser supports HDR images! – Photo by "
  attr="babeneso"
  attrlink="https://instagram.com/babeneso"
>}}

---

## Inline syntax highlighting (enhanced) {#chroma}

You can already wrap text in Markdown with a pair of backticks <kbd>\`</kbd> to show inline code, like this: `const number = 42;`. However, the native approach does not apply syntax highlighting. In that case, use this shortcode instead:

```go-html-template
{{</* highlight javascript "hl_inline=true" */>}}const number = 42;{{</* /highlight */>}}
```

Rendered result:

{{< highlight javascript "hl_inline=true" >}}const number = 42;{{< /highlight >}}

Inline code simply means it can be written inline with text, like this: {{< highlight javascript "hl_inline=true" >}}const number = 42;{{< /highlight >}}, without needing its own block… uh‑oh, am I redeclaring this constant over and over?

> [!WARNING]
> Before using this shortcode, you must configure Chroma (the syntax highlighter) as described [here]({{% ref "Syntax Highlighting" %}}); otherwise the highlighting will not render correctly.

---

## YouTube video

Insert the shortcode in Markdown:

```go-html-template
{{</* youtube jVhlJNJopOQ */>}}
```

Rendered result:

{{< youtube jVhlJNJopOQ >}}

---

## Instagram post

Insert the shortcode in Markdown:

```go-html-template
{{</* instagram DNYXvbczqGL */>}}
```

Rendered result:

{{< instagram DNYXvbczqGL >}}

---

## X post

Insert the shortcode in Markdown:

```go-html-template
{{</* x user="Kurz_Gesagt" id="1889702410852925900" */>}}
```

Rendered result:

{{< x user="Kurz_Gesagt" id="1889702410852925900" >}}
