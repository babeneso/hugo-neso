---
title           : "Theme Customization"
date            : 2025-10-09T16:29:04+08:00
lastmod         : 2025-10-09T16:29:04+08:00
slug            : "customization"

description     : "Thanks to Hugo’s override mechanism, customizing is straightforward and clean. The Neso theme also exposes multiple entry points for your edits. This page walks from simple to advanced ways to customize the theme."
summary         : "Thanks to Hugo’s override mechanism, customizing is straightforward and clean. The Neso theme exposes multiple entry points. This page walks from simple to advanced customization."
keywords        : ["Hugo", "Customization", "CSS", "Tailwind", "Templates", "Theme", "Neso", "hugo-neso"]
tags            : ["Customization", "Tailwind", "CSS"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
      hidden_in_single: true
---


## Override CSS Directly

Create an empty file at the following path in your Hugo project (the **filename must be exactly** {{< highlight text "hl_inline=true" >}}custom.css{{< /highlight >}}):

{{< highlight text "hl_inline=true" >}}assets/css/custom.css{{< /highlight >}}

If the directories do not exist, please create them.

Then write your own CSS there. Although this is not always the best approach, it is simple and effective. Neso’s CSS is intentionally written with low specificity so your rules can override it.

You may also follow Tailwind’s [recommendation](https://tailwindcss.com/docs/adding-custom-styles) to place styles in appropriate layers and define your own utility classes. If you prefer this method, I have prepared a small [cheat sheet](https://github.com/babeneso/hugo-neso/blob/main/assets/css/custom.css) you can start from.

> [!NOTE]
> Because this theme primarily uses Tailwind utility classes, there may be fewer static class names for you to target in the HTML. I will add reasonable hooks in future updates where appropriate.


---

## Customize Syntax Highlighting

See the instructions [here]({{% ref "Syntax Highlighting/#customize-the-highlighting-theme" %}}).


---

## Tailwind CSS

Download **palette.css** from the Neso GitHub repo: [palette.css](https://github.com/babeneso/hugo-neso/blob/main/assets/css/palette.css).

Inside that CSS you will find the color variables used by the theme. Customize them according to Tailwind’s guidance on [theme customization](https://tailwindcss.com/docs/theme#customizing-your-theme).

After editing, place the file under your project at: {{< highlight text "hl_inline=true" >}}assets/css/palette.css{{< /highlight >}}.

If the directories do not exist, please create them.


---

## Insert Custom Snippets

Download **any of these four partials** from the Neso GitHub repo ([link](https://github.com/babeneso/hugo-neso/tree/main/layouts/_partials/include)). You do **not** need all of them – pick what you need:

{{< highlight text "hl_inline=true" >}}head_start.html{{< /highlight >}}
: HTML, CSS, JavaScript, or [Go html/template](https://gohugo.io/templates/introduction/) written here will be inserted **at the very beginning** of the {{< highlight html "hl_inline=true" >}}<head>{{< /highlight >}} element on every page.
: Good for: Google Tag Manager container code; JavaScript that avoids FOUC.

{{< highlight text "hl_inline=true" >}}head_end.html{{< /highlight >}}
: Code here is inserted **at the very end** of the {{< highlight html "hl_inline=true" >}}<head>{{< /highlight >}} element on every page.
: Good for: custom CSS.

{{< highlight text "hl_inline=true" >}}body_start.html{{< /highlight >}}
: Code here is inserted **at the very beginning** of the {{< highlight html "hl_inline=true" >}}<body>{{< /highlight >}} element on every page.
: Good for: Google Tag Manager container code.

{{< highlight text "hl_inline=true" >}}body_end.html{{< /highlight >}}
: Code here is inserted **at the very end** of the {{< highlight html "hl_inline=true" >}}<body>{{< /highlight >}} element on every page.
: Good for: JavaScript.

After editing these files, place them under your project at: {{< highlight text "hl_inline=true" >}}layouts/_partials/include/<here>{{< /highlight >}}.

If the directories do not exist, please create them.

> [!TIP]
> The Neso theme ships with a Tailwind CSS pipeline enabled, so you can freely use utility classes inside your HTML templates.


---

## Override Templates (Advanced)

Examine the Neso theme’s directory structure ([GitHub repo](https://github.com/babeneso/hugo-neso)):

```text
hugo-neso/
├── assets
├── i18n
└── layouts
```

You should see similar directories (and names) in your own Hugo project. Refer to the Hugo [documentation](https://gohugo.io/getting-started/directory-structure/#directories) for each directory’s purpose.

In short, you can copy a source file from the theme (download it from the Neso theme’s [GitHub repo](https://github.com/babeneso/hugo-neso)), make your changes, and place it under the corresponding folder in your own project. During build, Hugo will prefer your version.

> [!TIP]
> The Neso theme ships with a Tailwind CSS pipeline enabled, so you can freely use utility classes inside your HTML templates.

> [!WARNING]
> If your installation method placed a copy of the theme under {{< highlight text "hl_inline=true" >}}themes/{{< /highlight >}} as {{< highlight text "hl_inline=true" >}}hugo-neso/{{< /highlight >}}, **do not modify** files inside that copy directly. Use the override approach described above. Otherwise, when the theme updates, you will have to manually track and merge your changes.
