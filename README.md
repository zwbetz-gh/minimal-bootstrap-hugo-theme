# Minimal Bootstrap Hugo Theme

A minimal hugo theme made with bootstrap that focuses on content readability.

## Table of Contents

* [Screenshot](#screenshot)
* [Installation Options](#installation-options)
* [Update Options](#update-options)
* [Site Layout](#site-layout)
* [Configuration](#configuration)
    * [Example config.toml](#example-configtoml)
    * [Config Options](#config-options)
    * [Favicon and Apple Touch Icon](#favicon-and-apple-touch-icon)
* [Front Matter Dates](#front-matter-dates)
* [Shortcodes](#shortcodes)
    * [blockquote](#blockquote)
    * [imgAbs](#imgabs)
    * [imgRel](#imgrel)
* [Override](#override)
* [Contribution](#contribution)

## Screenshot

TODO take

## Installation Options

1. Add it as a git submodule. (This requires that your site already be in a git repo. This is the **recommended** installation option since the parent/child repos will be handled correctly when deploying your site)
    1. `cd YOUR_SITE`
    1. `mkdir themes`
    1. `git submodule add https://github.com/zwbetz-gh/minimal-bootstrap-hugo-theme.git themes/minimal-bootstrap-hugo-theme`
1. Add it by using git clone
    1. `cd YOUR_SITE`
    1. `mkdir themes`
    1. `cd themes`
    1. `git clone https://github.com/zwbetz-gh/minimal-bootstrap-hugo-theme.git`
1. Download a zip and unzip it
    1. [Download the theme from GitHub](https://github.com/zwbetz-gh/minimal-bootstrap-hugo-theme/archive/master.zip)
    1. Unzip it into the `themes/` folder

Once installed, add this line to your `config.toml`:

```
theme = "minimal-bootstrap-hugo-theme"
```

## Update Options

If you used one of the git options to install the theme, update it by running:

1. `cd YOUR_SITE/themes/minimal-bootstrap-hugo-theme`
1. `git pull`

If you downloaded a zip to install the theme, just do those installation steps again.

## Site Layout

This theme expects your _posts_ to be under the `post/` folder.

```
├───content/
│   │   about.md
│   │   contact.md
│   └───post/
│           creating-a-new-theme.md
│           goisforlovers.md
│           hugoisforlovers.md
│           migrate-from-jekyll.md
│           simple-pleasures.md
```
## Configuration

### Example `config.toml`

```toml
baseurl = "https://example.org/"
title = "Site Title"
author = "Your Name"
languageCode = "en-us"
theme = "minimal-bootstrap-hugo-theme"
enableGitInfo = false

[params]
description = "Your site description"
navbarBackgroundColor = "#000"
wrapperMaxWidth = "780px"
customDateFormat = "Monday, January 2, 2006"
customCodeStyle = true
customBlockquoteStyle = true
showPostSummary = false
googleAnalytics = "UA-123456789-1"
faviconSafariPinnedTabColor = "#000000"
faviconMsApplicationTileColor = "#da532c"
faviconThemeColor = "#ffffff"

[menu]
[[menu.nav]]
name = "Posts"
url = "/"
weight = 1
[[menu.nav]]
name = "About"
url = "/about/"
weight = 2
[[menu.nav]]
name = "Contact"
url = "/contact/"
weight = 3
[[menu.nav]]
name = "Random Page"
url = "/random-page/"
weight = 4
```

### Config Options

```
theme = "minimal-bootstrap-hugo-theme"
```
* **Required**
* Set your site's theme
<br><br>

```
enableGitInfo = false
```
* Optional
* If set to true, `lastmod` date will be git's last revision of the file
* If set to false, `lastmod` date will pull from front matter
<br><br>

```
description = "Your site description"
```
* Optional
* If present, this will populate the `<meta>` description element
<br><br>

```
navbarBackgroundColor = "#000"
```
* Optional
* If present, this will set the navbar background color
* If not present, the default navbar background color is `#212529`
* The color value can be one of the below:
    * hex: `"#000"`
    * rgb: `"rgb(0,0,0)"`
    * rgba: `"rgba(0,0,0,1)"`
    * name: `"black"`
<br><br>

```
wrapperMaxWidth = "780px"
```
* Optional
* If present, this will set the max width of the navbar and page content
* If not present, the default max width is `"800px"`
<br><br>

```
customDateFormat = "Monday, January 2, 2006"
```
* Optional
* If present, this will set the date format on your homepage and posts
* If not present, the default date format is `"January 2, 2006"`
* See below hugo docs link for a list of valid date formats 
* <https://gohugo.io/functions/format/#hugo-date-and-time-templating-reference>
<br><br>

```
customCodeStyle = true
```
* Optional (but **recommended**, so that your code snippets are formatted nicely)
* If set to true, this will use custom code styles
<br><br>

```
customBlockquoteStyle = true
```
* Optional (but **recommended**, so that your blockquotes are formatted nicely)
* If set to true, this will use custom blockquote styles
<br><br>

```
showPostSummary = false
```
* Optional
* If set to true, this will show a summary for each post on the homepage
* For how many words to show in the summary, where to cut it off, etc., see below hugo docs link
* <https://gohugo.io/content-management/summaries/>
<br><br>

```
googleAnalytics = "UA-123456789-1"
```
* Optional
* If present, google analytics will be enabled
<br><br>

```
faviconSafariPinnedTabColor = "#000000"
faviconMsApplicationTileColor = "#da532c"
faviconThemeColor = "#ffffff"
```
* Optional
* If present, these will set the favicon colors for various platforms
* To generate these values, see the [Favicon and Apple Touch Icon](#favicon-and-apple-touch-icon) section
<br><br>

```
[menu]
[[menu.nav]]
name = "Posts"
url = "/"
weight = 1
```
* **Required**
* At least one menu nav is required
* The `name` is what will display in the navbar
* The `url` will be the url of the menu nav
* The `weight` will determine how the manu navs are ordered in the navbar

### Favicon and Apple Touch Icon

Place your `favicon.ico` and `apple-touch-icon.png` files at the root of your site, i.e. place them directly under your `static/` folder. 

To generate these icons (and additional icons for other platforms) from a single image file, use the [RealFaviconGenerator](https://realfavicongenerator.net/) online tool. 

## Front Matter Dates

If you don't set `publishdate` in your front matter, it will fallback to `date`. 

If you don't set `lastmod` in your front matter, but you have `enableGitInfo = true` in your `config.toml`, then `lastmod` date will the git's last revision of the file.

If you don't set `lastmod` in your front matter, and you have `enableGitInfo = false` (or don't have that line at all) in your `config.toml`, then `lastmod` date will fallback to `date`. 

For more info see the hugo docs for [Configure Dates](https://gohugo.io/getting-started/configuration/#configure-dates). 

## Shortcodes

### `blockquote`

This will format your blockquotes nicely. To use it, pass the author's name as an argument, then within the shortcode put the quote: 

```
{{% blockquote "Laura Ingalls" %}}
I am beginning to learn that it is the sweet, **simple** things of life which are the real ones after all.  
{{% /blockquote %}}
```

### `imgAbs`

This will insert an image into your content by absolute path. To use it, pass the `pathURL` of your image. The `alt` and `class` arguments are optional.

```
{{< imgAbs pathURL="img/some-img.png" alt="Some description" class="some-class" >}}
```

### `imgRel`

This will insert an image into your content by relative path. To use it, pass the `pathURL` of your image. The `alt` and `class` arguments are optional.

```
{{< imgRel pathURL="img/some-img.png" alt="Some description" class="some-class" >}}
```

## Override

As an example, let's say you didn't like the default theme navbar, and wanted to design one of your own. To do this, you would:

1. Copy file `YOUR_SITE/themes/minimal-bootstrap-hugo-theme/layouts/partials/nav.html`
1. Paste that file to `YOUR_SITE/layouts/partials/nav.html`
1. Edit `nav.html` as desired

## Contribution

Pull requests, issues, and general feedback are welcomed.