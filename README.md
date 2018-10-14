# Minimal Bootstrap Hugo Theme

A minimal hugo theme made with bootstrap that focuses on content readability.

The typical page size (if the page has no images) is under 200kb. The only other assets loaded besides your actual HTML page are: the Bootstrap CSS, your favicon (if enabled), and Google Analytics (if enabled).  

## Table of Contents

* [Screenshot](#screenshot)
* [Installation Options](#installation-options)
* [Update Options](#update-options)
* [Site Layout](#site-layout)
* [Example config.toml](#example-configtoml)
* [config.toml Options](#configtoml-options)
    * [Theme](#theme)
    * [Enable Git Info](#enable-git-info)
    * [Description](#description)
    * [Navbar Background Color](#navbar-background-color)
    * [Wrapper Max Width](#wrapper-max-width)
    * [Date Format](#date-format)
    * [Code Style](#code-style)
    * [Blockquote Style](#blockquote-style)
    * [Post Summary](#post-summary)
    * [Google Analytics](#google-analytics)
    * [Cookie Consent](#cookie-consent)
    * [Favicon Colors on Various Platforms](#favicon-colors-on-various-platforms)
    * [Menu Nav](#menu-nav)
* [Favicon and Apple Touch Icon](#favicon-and-apple-touch-icon)
* [Override](#override)
    * [Navbar Example](#navbar-example)
    * [Cookie Consent](#cookie-consent-1)
* [Syntax Highlighting](#syntax-highlighting)
* [Front Matter Dates](#front-matter-dates)
    * [publishdate](#publishdate)
    * [lastmod](#lastmod)
* [Shortcodes](#shortcodes)
    * [blockquote](#blockquote)
    * [imgAbs](#imgabs)
    * [imgRel](#imgrel)
* [Contribution](#contribution)

## Screenshot

TODO link to screenshot by absolute path 

## Installation Options

1. Add it as a git submodule
    1. `cd YOUR_SITE`
    1. `git submodule add https://github.com/zwbetz-gh/minimal-bootstrap-hugo-theme.git themes/minimal-bootstrap-hugo-theme`
1. Download a zip and unzip it
    1. [Download a zip of the theme from GitHub](https://github.com/zwbetz-gh/minimal-bootstrap-hugo-theme/archive/master.zip)
    1. Unzip it into `YOUR_SITE/themes/`

Once installed, add this line to your `config.toml`:

```
theme = "minimal-bootstrap-hugo-theme"
```

## Update Options

If you used the git submodule option to install the theme, update it by running:

1. `cd YOUR_SITE`
1. `git submodule foreach git pull origin master`

If you downloaded a zip to install the theme, just do those installation steps again to update it.

## Site Layout

This theme expects your _posts_ to be under the `post/` folder.

```
│   config.toml
├───content/
│   │   about.md
│   └───post/
│           creating-a-new-theme.md
│           goisforlovers.md
│           hugoisforlovers.md
│           migrate-from-jekyll.md
```

Also see the `exampleSite/`.

## Example `config.toml`

```toml
baseURL = "https://example.com"
languageCode = "en-us"
title = "Some Title"
theme = "minimal-bootstrap-hugo-theme"
enableGitInfo = false

pygmentsCodefences = true
pygmentsCodefencesGuessSyntax = true
pygmentsStyle = "pygments"

[permalinks]
  post = "/:filename/"

[params]
  description = "Some description"
  navbarBackgroundColor = "#000"
  wrapperMaxWidth = "780px"
  customDateFormat = "Monday, January 2, 2006"
  customCodeStyle = true
  customBlockquoteStyle = true
  showPostSummary = false
  googleAnalytics = "UA-123456789-1"
  cookieConsent = true

  faviconSafariPinnedTabColor = "#5bbad5"
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
  name = "Some Page"
  url = "#"
  weight = 3
```

## config.toml Options

### Theme

```
theme = "minimal-bootstrap-hugo-theme"
```
* **Required**
* Set your site's theme

### Enable Git Info

```
enableGitInfo = false
```
* Optional
* If set to `true`, `lastmod` date will be git's last revision of the file
* If set to `false`, `lastmod` date will pull from front matter
* See [Front Matter Dates](#front-matter-dates) for more info

### Description

```
description = "Your site description"
```
* Optional
* If present, this will populate the `<meta>` description element

### Navbar Background Color

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

### Wrapper Max Width

```
wrapperMaxWidth = "780px"
```
* Optional
* If present, this will set the max width of the navbar and page content
* If not present, the default max width is `"800px"`

### Date Format

```
customDateFormat = "Monday, January 2, 2006"
```
* Optional
* If present, this will set the date format on your homepage and posts
* If not present, the default date format is `"January 2, 2006"`
* See the [hugo docs for a list of valid date formats](https://gohugo.io/functions/format/#hugo-date-and-time-templating-reference)

### Code Style

```
customCodeStyle = true
```
* Optional (but **recommended**, so that your code snippets are formatted nicely)
* If set to `true`, this will use custom code styles

### Blockquote Style

```
customBlockquoteStyle = true
```
* Optional (but **recommended**, so that your blockquotes are formatted nicely)
* If set to `true`, this will use custom blockquote styles
* See [blockquote](#blockquote)

### Post Summary

```
showPostSummary = false
```
* Optional
* If set to `true`, this will show a summary for each post on the homepage
* For how many words to show in the summary, where to cut it off, etc., see [hugo docs for summaries](https://gohugo.io/content-management/summaries/)

### Google Analytics

```
googleAnalytics = "UA-123456789-1"
```
* Optional
* If present, Google Analytics will be enabled

### Cookie Consent

```
cookieConsent = true
```
* Optional
* If set to `true`, this will show a cookie consent popup in order to be compliant with GDPR
* To configure the look and feel of the popup, see TODO

### Favicon Colors on Various Platforms

```
faviconSafariPinnedTabColor = "#000000"
faviconMsApplicationTileColor = "#da532c"
faviconThemeColor = "#ffffff"
```
* Optional
* If present, these will set the favicon colors for various platforms
* To generate these values, see [Favicon and Apple Touch Icon](#favicon-and-apple-touch-icon)

### Menu Nav

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

## Favicon and Apple Touch Icon

Place your `favicon.ico` and `apple-touch-icon.png` files at the root of your site, i.e. place them directly under `YOUR_SITE/static/`. See `exampleSite/static/` for other (optional) favicon files.

To generate all these favicons from a single image, use the [RealFaviconGenerator](https://realfavicongenerator.net/) online tool. After using the tool, you'll be prompted to download a zip of your favicon package. You'll then want to extract the zip contents directly into `YOUR_SITE/static/`. 

## Override

### Navbar Example

As an example, let's say you didn't like the default theme navbar, and wanted to design one of your own. To do this, you would:

1. Copy file `YOUR_SITE/themes/minimal-bootstrap-hugo-theme/layouts/partials/nav.html`
1. Paste that file to `YOUR_SITE/layouts/partials/nav.html`
1. Edit `nav.html` as desired

### Cookie Consent

You can change the banner color, banner text color, button color, and button text color of the cookie consent popup. To do this, you would:

1. Copy file `YOUR_SITE/themes/minimal-bootstrap-hugo-theme/layouts/partials/cookie-consent.html`
1. Paste that file to `YOUR_SITE/layouts/partials/cookie-consent.html`
1. Complete the [cookie consent wizard](https://cookieconsent.insites.com/download/)
1. Paste the generated code from the wizard into `cookie-consent.html`

## Syntax Highlighting

Hugo has built-in syntax highlighting, provided by Chroma. To use it, add these lines to your `config.toml`:

```
pygmentsCodefences = true
pygmentsCodefencesGuessSyntax = true
pygmentsStyle = "pygments"
```

Here, `"pygments"` is just the name of the Chroma style to be used. Checkout the [Chroma style gallery](https://xyproto.github.io/splash/docs/all.html) and choose the style you like.

For a deeper dive see the [hugo docs for syntax highlighting](https://gohugo.io/content-management/syntax-highlighting/).

## Front Matter Dates

### `publishdate`

If you don't set `publishdate` in your front matter, it will fallback to `date`. 

### `lastmod`

If you have `enableGitInfo = true` in your `config.toml`, then `lastmod` date will be git's last revision of the file.

If you have `enableGitInfo = false` (or don't have that line at all) in your `config.toml`, then `lastmod` date will be the `lastmod` value in your front matter. If you don't have `lastmod` in your front matter, it will fallback to `date`. 

For a deeper dive see the [hugo docs for configure dates](https://gohugo.io/getting-started/configuration/#configure-dates). 

## Shortcodes

### `blockquote`

This will format your blockquotes nicely. To use it, put the quote within the shortcode. The `author` argument is optional.

```
{{% blockquote author="Laura Ingalls" %}}
I am beginning to learn that it is the sweet, **simple** things of life which are the real ones after all.  
{{% /blockquote %}}
```

### `imgAbs`

This will insert an image into your content by absolute path. To use it, pass the `pathURL` of your image. These arguments are optional: `alt`, `class`, `style`.

```
{{< imgAbs pathURL="img/some-img.png" alt="Some description" class="some-class" style="some-style" >}}
```

### `imgRel`

This will insert an image into your content by relative path. To use it, pass the `pathURL` of your image. These arguments are optional: `alt`, `class`, `style`.

```
{{< imgRel pathURL="img/some-img.png" alt="Some description" class="some-class" style="some-style" >}}
```

## Contribution

Pull requests, issues, and general feedback are welcomed.