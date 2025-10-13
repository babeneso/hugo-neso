---
title           : "Theme Parameters (Site-wide)"
date            : 2025-10-04T15:06:02+08:00
lastmod         : 2025-10-06T14:52:35+08:00
draft           : false
slug            : "site-params"

description     : "This page lists the theme's built-in site-wide parameters that control the homepage, global UI, SEO, and more."
summary         : "This page lists the theme's built-in site-wide parameters that control the homepage, global UI, SEO, and more."
keywords        : ["Hugo", "Parameters", "Settings", "Configuration", "Customization", "Theme", "Neso", "hugo-neso"]
tags            : ["hugo.toml", "Configuration", "Favicon"]

params:
  neso:
    show_toc    : true
    cover:
      image           : "cover.png"
      hidden_in_single: true
---

> [!TIP]
> The theme works out of the box with sensible defaults. You can ignore these settings at first and add them later when needed.


## About the site-wide config

This theme's site‑wide parameters are grouped under the `params.neso` namespace. In your project's root `hugo.toml`, it should look like this:

```toml
[params]
  [params.neso]                  # table header
    support_theme_author = true  # key / value
    [params.neso.home]
      display_mode = "profile"
      # omitted...
```

You may also split the configuration into multiple files as needed; see the [Hugo documentation](https://gohugo.io/configuration/introduction/).

> [!NOTE]
> Hugo also accepts YAML or JSON config files. Use any converter if you need to switch formats.

---


## Top-level settings {id="general-settings"}

Table header: `[params.neso]`.

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| Key | Type | Description |
| --- | :---: | --- |
| `time_format` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | The format used to display a post's publish time. See the Hugo [docs](https://gohugo.io/functions/time/format/) |
| `disable_responsive_menu` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Disable the responsive site menu |
| `show_breadcrumbs` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Show the breadcrumb trail at the top of pages (can be turned off per page via [Front Matter]({{% relref "Params - Front Matter/#other-settings" %}})) |
| `ext_link_indicator` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Add an indicator icon to external links |
| `ext_link_no_opener_referrer` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Add `noopener`, `noreferrer`, etc. to the `rel` attribute of external link {{< highlight html "hl_inline=true" >}}<a>{{< /highlight >}} elements |
| `ext_link_new_window` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Open external links in a new tab/window |
| `show_full_content_in_rss` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Include full content in [RSS output](https://gohugo.io/configuration/outputs/) (by default, the post `Summary` from Front Matter is used) |
| `archive_includes_all_sections` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Include posts from all sections on the Archives page. (Default {{< highlight toml "hl_inline=true" >}}false{{< /highlight >}}: only include posts from [`mainSections`](https://gohugo.io/configuration/all/#mainsections)) |
| `disable_scroll_to_top` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Hide and disable the "Back to top" button |
| `footer_text` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Custom text appended after the copyright line in the footer |
| `hide_copyright` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Hide the copyright line in the footer |
| `support_theme_author` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Show a "Powered by" line in the footer to credit the theme author (thank you 🥹) |
| `hide_footer` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Hide the entire footer block (copyright, custom text, and the "Powered by" line) |
| `force_color_scheme` | {{< highlight toml "hl_inline=true" >}}false{{< /highlight >}}<br>{{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | When set to {{< highlight toml "hl_inline=true" >}}false{{< /highlight >}}, display a color‑scheme switcher UI in the footer. If set to the string {{< highlight toml "hl_inline=true" >}}"system"{{< /highlight >}} (follow the user's OS), {{< highlight toml "hl_inline=true" >}}"light"{{< /highlight >}}, or {{< highlight toml "hl_inline=true" >}}"dark"{{< /highlight >}}, hide the switcher and force that scheme site‑wide |
| `display_short_lang_name` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | When multiple languages are enabled, show short codes like "EN" / "ZH" in the top nav instead of full names like "English" / "中文" |

</div>

---


## Branding {id="branding"}

Table header: `[params.neso.branding]`.

> [!IMPORTANT]
> There are many possible image slots here, but in practice `og_image` + `favicon_ico` + `favicon_svg` already provide solid on‑site display and rich link previews. The rest are for pixel‑perfect support in specific environments and can usually be skipped.

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| Key | Type | Description |
| --- | :---: | --- |
| `logo_text` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Custom text logo in the top navigation bar (This string is only used as the visual logo in the nav; elsewhere the site name comes from the site’s `title` setting) |
| `hide_logo_text` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Hide the text logo in the top navigation bar |
| `logo_image` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Logo image [URL](#assets_url) for the top navigation bar |
| `logo_image_dark` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Dark‑mode variant logo image [URL](#assets_url) for the top nav (used only when the site is in dark color scheme) |
| `logo_image_width` | {{< highlight text "hl_inline=true" >}}Integer{{< /highlight >}} | Width of the logo image in the top nav (unit is `px`; enter a plain integer without the unit) |
| `logo_image_height` | {{< highlight text "hl_inline=true" >}}Integer{{< /highlight >}} | Height of the logo image in the top nav (unit is `px`; enter a plain integer without the unit) |
| `og_image` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Default site‑wide `og:image` [URL](#assets_url). Recommended size: 1200×630 px |
| `favicon_ico` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Favicon image URL ({{< highlight text "hl_inline=true" >}}ICO{{< /highlight >}}). For compatibility and SEO, unless you have special needs, it’s strongly recommended to name the file {{< highlight text "hl_inline=true" >}}favicon.ico{{< /highlight >}}, place it at the top level of the site’s {{< highlight text "hl_inline=true" >}}static/{{< /highlight >}} directory, and **leave this setting empty** |
| `favicon_svg` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Favicon image [URL](#assets_url) ({{< highlight text "hl_inline=true" >}}SVG{{< /highlight >}}). Modern browsers support SVG favicons and they usually render crisper |
| `apple_touch_icon` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | `apple-touch-icon` image [URL](#assets_url) ({{< highlight text "hl_inline=true" >}}PNG{{< /highlight >}}) |
| `pwa_short_title` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Short name shown when users add the site to the home screen on mobile; keep it brief for better fit |
| `pwa_theme_color_light` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Hex theme color (e.g. `#bada55`). Supported browsers may tint UI surfaces to provide a more immersive feel; choose a value that matches your light background |
| `pwa_theme_color_dark` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Hex theme color for dark mode. Pick a value that matches your dark background |
| `pwa_icon_svg` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | PWA icon [URL](#assets_url) ({{< highlight text "hl_inline=true" >}}SVG{{< /highlight >}}) |
| `pwa_icon_192` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | PWA icon [URL](#assets_url) ({{< highlight text "hl_inline=true" >}}PNG{{< /highlight >}}, 192×192 px) |
| `pwa_icon_512` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | PWA icon [URL](#assets_url) ({{< highlight text "hl_inline=true" >}}PNG{{< /highlight >}}, 512×512 px) |
| `pwa_icon_maskable_svg` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Maskable PWA icon [URL](#assets_url) ({{< highlight text "hl_inline=true" >}}SVG{{< /highlight >}}) |
| `pwa_icon_maskable_192` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Maskable PWA icon [URL](#assets_url) ({{< highlight text "hl_inline=true" >}}PNG{{< /highlight >}}, 192×192 px) |
| `pwa_icon_maskable_512` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Maskable PWA icon [URL](#assets_url) ({{< highlight text "hl_inline=true" >}}PNG{{< /highlight >}}, 512×512 px) |

</div>

> [!NOTE]
> For settings prefixed with `pwa_`, the theme generates a manifest.json for you according to the W3C Web App Manifest [spec](https://www.w3.org/TR/appmanifest/) spec. See also [web.dev](https://web.dev/learn/pwa/web-app-manifest) and [MDN](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Manifest).
>
> For recommended icon variants, usage scenarios, and sizing details, refer to [web.dev](https://web.dev/learn/pwa/web-app-manifest#icons).

---


## Social links

Table header: `[params.neso.social]`.

These settings control the social links shown on the homepage. In TOML, write them as an "Array of Tables". Example:

```toml {hl_lines=["4-10"]}
[params]
  [params.neso]
    # other settings omitted...
    [params.neso.social]
      [[params.neso.social.links]]
        name = "Github"
        url  = "https://github.com/babeneso"
      [[params.neso.social.links]]
        name = "X"
        url  = "https://x.com/babeneso"
    [params.neso.home]
    # other settings omitted...
```

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| Key | Type | Description |
| --- | :---: | --- |
| `name` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Platform name; case-insensitive, but spelling must be correct (English) to display the correct icon |
| `url` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Your profile URL on that platform |

</div>

---


## Homepage {id="homepage"}

The following explains the homepage settings in detail.

1. ### Prepare the Index file
    
    At the top level under {{< highlight text "hl_inline=true" >}}content/{{< /highlight >}} in your Hugo project root, create an {{< highlight text "hl_inline=true" >}}_index.md{{< /highlight >}} file (note the leading underscore), and put the following in it:
    
    ```yaml
    ---
    # The Front Matter for the homepage only needs the two fields below:
    title       : "Kitty Home"
    description : "I love cooking and making small treats. My dream is to cuddle cats every day and sleep in!"
    ---
    
    # The main content area is only used when `display_mode` is NOT set to "profile".
    # If the file is "_index.md", you can write Markdown here to enrich the content;
    # If the file is "_index.html", you can write HTML here to implement more complex content.
    ```
    

2. ### Choose the layout

    In the site-wide config file (hugo.toml), set the layout mode under the `[params.neso.home]` table header:

    ```toml {hl_lines=["4-5"]}
    [params]
      [params.neso]
        # other settings omitted...
        [params.neso.home]
          display_mode = "profile"
        # other settings omitted...
    ```
    
    <dl>
        <dt>{{< highlight toml "hl_inline=true" >}}display_mode = "profile"{{< /highlight >}}</dt>
        <dd>
            {{< figure src="home-profile.png" >}}
            <p>Show avatar, title, bio text, plus social links and custom link buttons, with a centered layout. This mode is simpler and does not use the Index file's main content.</p>
        </dd>
        <dt>{{< highlight toml "hl_inline=true" >}}display_mode = "intro"{{< /highlight >}}</dt>
        <dd>
            {{< figure src="home-intro.png" >}}
            <p>Show the title, social links, and the Index file's main content, laid out according to the language's writing direction.</p>
        </dd>
        <dt>{{< highlight toml "hl_inline=true" >}}display_mode = "<any other string>"{{< /highlight >}}</dt>
        <dd>
            <p>Highly customizable mode; only the Index file's main content is shown.</p>
            <p>In this mode, it is recommended to name the file {{< highlight text "hl_inline=true" >}}_index.html{{< /highlight >}} and write HTML directly inside it. The HTML will be wrapped in a responsive-width container, so you do not need to write {{< highlight html "hl_inline=true" >}}<html>{{< /highlight >}} or {{< highlight html "hl_inline=true" >}}<body>{{< /highlight >}} tags, just write the content.</p>
            <p>The theme already wires up a Tailwind CSS pipeline, so you can use utility classes freely.</p>
        </dd>
    </dl>


### Detailed settings: {{% highlight toml "hl_inline=true" %}}"profile"{{% /highlight %}} mode

Table header: `[params.neso.home.profile]`.

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| Key | Type | Description |
| --- | :---: | --- |
| `avatar_image` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Avatar image [URL](#assets_url) |
| `avatar_image_alt_text` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Alt text for the avatar image |
| `avatar_image_size` | {{< highlight text "hl_inline=true" >}}Integer{{< /highlight >}} | Avatar image size; provide a positive integer; width and height are equal (unit is `px`; do not include the unit) |
| `avatar_image_size_sm` | {{< highlight text "hl_inline=true" >}}Integer{{< /highlight >}} | Avatar image size on small screens (mobile); provide a positive integer; width and height are equal (unit is `px`; do not include the unit) |

</div>

You can also add extra link buttons shown under the bio. In TOML, write them as an [Array of Tables](https://toml.io/en/v1.0.0#array-of-tables). Example:

```toml {hl_lines=["4","7-12"]}
[params]
  [params.neso]
    # other settings omitted...
    [params.neso.home.profile]
      avatar_image = "img/profile-photo.jpg"
      # other settings omitted...
      [[params.neso.home.profile.link_btns]]
        label = "Download My Resume"
        url   = "https://example.com/resume"
      [[params.neso.home.profile.link_btns]]
        label = "Top Repos"
        url   = "https://github.com/babeneso"
    [params.neso.home.list]
    # other settings omitted...
```

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| Key | Type | Description |
| --- | :---: | --- |
| `label` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Button text |
| `url` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Button link URL |

</div>


### Detailed settings: Recent posts

Table header: `[params.neso.home.list]`.

Regardless of the homepage layout you choose, you can additionally append a recent posts list below.

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| Key | Type | Description |
| --- | :---: | --- |
| `featured_entries_limit` | {{< highlight text "hl_inline=true" >}}Integer{{< /highlight >}} | Number of recent posts to show on the homepage; set to {{< highlight toml "hl_inline=true" >}}0{{< /highlight >}} to hide |
| `includes_all_sections` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Include posts from all sections. (Default {{< highlight toml "hl_inline=true" >}}false{{< /highlight >}}: only include posts from [mainSections](https://gohugo.io/configuration/all/#mainsections)) |
| `hide_view_archives_cta` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Hide the "View Archives" button below the list (the button links to the archives page) |

</div>

---


## Post list pages {id="list-settings"}

Table header: `[params.neso.list]`.

Post list pages appear throughout the site, such as a Section's post list or the list of posts under a specific Tag. The following parameters control how these lists are displayed.

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| Key | Type | Description |
| --- | :---: | --- |
| `prominent_first_entry` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Visually emphasize the first entry in the list (styling only) |
| `provide_rss_for_each_list` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Show an RSS button on every list page (in addition to the homepage), pointing to that list’s own feed |
| `hide_page_nums` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | When pagination is present, hide page numbers |
| `hide_summary` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Hide post summaries in lists |
| `hide_cover_image` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Hide cover images in lists |
| `disable_responsive_cover_image` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | By default, list cover images are processed via Hugo Pipes into multiple sizes at build time so the browser can choose an appropriate `src` for the viewport. Enable this to disable that mechanism (faster builds, potentially lower UX). |

</div>

---


## Single post pages

Table header: `[params.neso.page]`.

These parameters control the site‑wide defaults for individual post pages. Some settings can be overridden per page via [Front Matter]({{% relref "Params - Front Matter/#other-settings" %}}).

> [!TIP]
> For example, if you turn off the Table of Contents here with {{< highlight toml "hl_inline=true" >}}show_toc = "false"{{< /highlight >}}, you can still re‑enable the ToC for a specific post via that page’s Front Matter. Notes like this are provided where applicable below.

### General settings {id="single-general"}

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| Key | Type | Description |
| --- | :---: | --- |
| `ext_link_indicator` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Add an indicator icon to external links inside the article |
| `ext_link_no_opener_referrer` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Add `noopener`, `noreferrer` to the `rel` attribute of external link {{< highlight html "hl_inline=true" >}}<a>{{< /highlight >}} elements in the article |
| `ext_link_new_window` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Open external links in a new tab/window |
| `hide_description_in_single` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | If a post’s Front Matter provides `description`, the value is used for SEO (e.g., {{< highlight html "hl_inline=true" >}}<meta>{{< /highlight >}} tags) and also displayed at the top of the article as an introduction. Enable this to hide that introduction block so the value is only used as SEO metadata. |
| `full_size_cover_image_link` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | If a cover image is set in Front Matter, add a link to the full‑size original |
| `show_toc` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Show the in‑content table of contents (can be overridden per page via Front Matter) |
| `toc_expanded` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Expand the table of contents by default (can be overridden per page via Front Matter) |
| `disable_heading_links` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Do not add anchor {{< highlight html "hl_inline=true" >}}<a>{{< /highlight >}} elements to Markdown headings (like {{< highlight markdown "hl_inline=true" >}}##{{< /highlight >}}); similar to GitHub’s Section links; see the [Hugo docs](https://gohugo.io/configuration/markup/#parserautoheadingid) |
| `enable_comments` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Enable the comments block; see the comments configuration section (can be disabled per page via Front Matter) |
| `hide_copy_code_button` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Hide the "Copy" button on code blocks |

</div>


### Header metadata {id="single-metadata"}

The header block shows post metadata such as publish date, author(s), word count, and more. Some settings can be overridden per page via [Front Matter]({{% relref "Params - Front Matter/#metadata-settings" %}}).

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| Key | Type | Description |
| --- | :---: | --- |
| `show_reading_time` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Show the estimated reading time |
| `show_word_count` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Show the word count |
| `show_author` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Show author(s) (author info can be set in site‑wide params or per post in Front Matter) |
| `show_canonical_link` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | If the post’s Front Matter provides `canonical_url`, display a link to it |
| `canonical_link_text` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | When showing the `canonical_url` link, prefix it with this default text; e.g., {{< highlight text "hl_inline=true" >}}Originally published on{{< /highlight >}} (can be overridden in the page’s Front Matter) |
| `hide_metadata` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Hide the entire header block (can be overridden per page via Front Matter) |

</div>


### Footer features {id="single-footer"}

The footer block shows post tags, share buttons, and the previous/next links for further reading. Some settings can be overridden per page via [Front Matter]({{% relref "Params - Front Matter/#footer-settings" %}}).

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| Key | Type | Description |
| --- | :---: | --- |
| `show_content_footer` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Show the footer block (can be turned off per page via Front Matter) |
| `show_share` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Show share buttons (can be turned off per page via Front Matter) |
| `share_providers` | {{< highlight text "hl_inline=true" >}}String[]{{< /highlight >}} | Choose share targets; if set, only the selected providers are shown, e.g. {{< highlight toml "hl_inline=true" >}}["facebook", "line"]{{< /highlight >}}; if not set, all providers are shown by default: {{< highlight toml "hl_inline=true" >}}["facebook", "line", "linkedin", "messenger", "reddit", "telegram", "whatsapp", "x"]{{< /highlight >}} |
| `show_prev_next` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Show "Previous / Next" links for further reading (can be overridden per page via Front Matter) |

</div>


> [!NOTE]
> “Single post page” here refers to the HTML page rendered by Hugo. Most settings in this section target pages whose [page kind](https://gohugo.io/quick-reference/glossary/#page-kind) is `page` — in typical use this is a blog post. Hugo’s terminology is somewhat abstract, so we call it a single post page here for simplicity.

---


## SEO

Table header: `[params.neso.seo]`.

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| Key | Type | Description |
| --- | :---: | --- |
| `block_indexing` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Set the {{< highlight html "hl_inline=true" >}}<meta name="robots">{{< /highlight >}} of all pages to `noindex`, `nofollow` (can be overridden per page via Front Matter) |
| `site_description` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Site‑wide description/summary |
| `site_keywords` | {{< highlight text "hl_inline=true" >}}String[]{{< /highlight >}} | Site‑wide list of keywords, e.g. {{< highlight toml "hl_inline=true" >}}["cats", "cute"]{{< /highlight >}} |
| `site_author` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} {{< highlight text "hl_inline=true" >}}String[]{{< /highlight >}} | Site owner/author name. For a single person, provide a string (e.g., {{< highlight toml "hl_inline=true" >}}"Ada Lovelace"{{< /highlight >}}); for multiple people, provide an array of strings (e.g., {{< highlight toml "hl_inline=true" >}}["Alice", "Bob", "Carol"]{{< /highlight >}}). |

</div>


### Detailed settings: Structured data

Table header: `[params.neso.seo.schema]`.

The theme automatically generates structured data in JSON‑LD format to improve SEO. The following fields let you provide additional information.

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| Key | Type | Description |
| --- | :---: | --- |
| `publisher_type` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Publisher type; allowed values are `Person` or `Organization`. See Google Search Central (Article structured data) and Schema.org. [[docs](https://developers.google.com/search/docs/appearance/structured-data/article#author-bp)] [[schema](https://schema.org/publisher)] |
| `same_as` | {{< highlight text "hl_inline=true" >}}String[]{{< /highlight >}} | Other URLs that represent you (e.g., social profile pages). See Google Search Central (Profile page) and Schema.org. [[docs](https://developers.google.com/search/docs/appearance/structured-data/profile-page#profile-target-specification)] [[schema](https://schema.org/sameAs)] |

</div>


### Detailed settings: Search engine verification

Table header: `[params.neso.seo.verification]`.

When managing SEO for your site, you may need to verify ownership with search engines.

Most engines offer multiple verification methods. Inserting a {{< highlight html "hl_inline=true" >}}<meta>{{< /highlight >}} tag in your HTML is one of them. For example, Google provides code like this:

```html
<meta name="google-site-verification" content="...">
```

Other engines provide similar mechanisms. In short: after you obtain the verification snippet, find the token inside the `content` attribute and paste that token into the fields below. The theme will then insert the verification {{< highlight html "hl_inline=true" >}}<meta>{{< /highlight >}} tag for you in the document head.

The following search engines are supported:

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| Key | Type | Description |
| --- | :---: | --- |
| `google` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | [Google](https://support.google.com/webmasters/answer/9008080#meta_tag_verification) |
| `bing` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | [Bing](https://www.bing.com/webmasters/help/add-and-verify-site-12184f8b) |
| `yandex` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | [Yandex](https://yandex.com/dev/webmaster/doc/en/concepts/verification) |
| `naver` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | [Naver](https://searchadvisor.naver.com/guide/faq-start-register) |

</div>

---


## Site search

Table header: `[params.neso.search]`.

These settings assume you have already set up the [search page]({{% ref "Pages and Menu Setup/#search" %}}). If you don’t need on‑site search, you can ignore this section.

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| Key | Type | Description |
| --- | :---: | --- |
| `input_placeholder` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Placeholder text shown in the search input |

</div>

---


## Hugo Pipes asset pipeline

Table header: `[params.neso.assets]`.

Some assets used by the theme are processed by [Hugo Pipes](https://gohugo.io/hugo-pipes/introduction/), such as CSS, JavaScript, and certain images — sometimes for minification/transpilation, sometimes to add a [fingerprint](https://gohugo.io/functions/resources/fingerprint/) for cache busting. The options below control this behavior.

<div class="overflow-x-auto [&_table]:my-0
            [&_tbody_tr_td_.chroma]:break-keep
            [&_tbody_tr_td:last-child]:min-w-60
            [&_tbody_tr_td:last-child]:md:min-w-auto">

| Key | Type | Description |
| --- | :---: | --- |
| `output_dir` | {{< highlight text "hl_inline=true" >}}String{{< /highlight >}} | Choose the subdirectory (name) under the [publish directory](https://gohugo.io/configuration/all/#publishdir) where Hugo Pipes should place its output. Default: {{< highlight toml "hl_inline=true" >}}"assets"{{< /highlight >}} |
| `disable_fingerprinting` | {{< highlight text "hl_inline=true" >}}Boolean{{< /highlight >}} | Turn off fingerprinting |

</div>

---


## Additional notes

### Image locations and URLs {id="assets_url"}

The settings above that take an image URL follow these rules:

Absolute path
: Use the URL as-is; it may be root‑relative within the site or a fully qualified external URL.
: For example: {{< highlight toml "hl_inline=true" >}}"/special/stuff.png"{{< /highlight >}}, {{< highlight toml "hl_inline=true" >}}"https://example.com/image.png"{{< /highlight >}}.

Relative path
: Place images under the project's {{< highlight text "hl_inline=true" >}}assets/{{< /highlight >}} or {{< highlight text "hl_inline=true" >}}static/{{< /highlight >}} folder (choose one). In both cases, write the path relative to the top of that folder.
: For example, if the file is at {{< highlight text "hl_inline=true" >}}assets/img/example.png{{< /highlight >}} or {{< highlight text "hl_inline=true" >}}static/img/example.png{{< /highlight >}}, set it as {{< highlight toml "hl_inline=true" >}}"img/example.png"{{< /highlight >}}. The theme will locate the correct place. Do not start with a leading slash; otherwise it becomes a root‑relative absolute path.
: Files placed under {{< highlight text "hl_inline=true" >}}assets/{{< /highlight >}} support fingerprinting.
