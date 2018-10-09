# Minimal Bootstrap Hugo Theme

A minimal hugo theme made with bootstrap that focuses on content readability.

## Table of Contents

TODO generate

## Screenshot

TODO take

## Installation Options

1. Add it as a git submodule (this requires your site to already be in a git repo)
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

### `config.toml`

```toml
baseurl = "https://example.org/"
title = "Site Title"
author = "Your Name"
languageCode = "en-us"

# Required
theme = "minimal-bootstrap-hugo-theme"

# Optional
# If true, lastmod date will be git's last revision of the file, instead of the lastmod date specified in frontmatter
enableGitInfo = true

# Required
[params]

# Optional
# If present, this will populate the <meta> description element in your <head>
description = "Your site description here"

# Optional
# If present, it will set the navbar background color
# The color value can be one of the below:
# hex like "#000"
# rgb like "rgb(0,0,0)"
# rgba like "rgba(0,0,0,1)"
# name like "black"
navbarBackgroundColor = "#000"

# Optional
# If present, it will set the max width of the navbar and page content
# If not present, the default wrapper max width is "800px"
wrapperMaxWidth = "600px"

# Optional
# If present, it will set the date format on your homepage and posts
# If not present, the default date format is "January 2, 2006"
# See below hugo docs link for a list of valid date formats 
# https://gohugo.io/functions/format/#hugo-date-and-time-templating-reference
customDateFormat = "Monday, January 2, 2006"

# Optional
# If set to true, this will use custom code styles
customCodeStyle = true

# Optional
# If set to true, this will use custom blockquote styles
customBlockquoteStyle = true

# Optional
# If set to true, this will show a summary for each post on the homepage
# For how many words to show in the summary, where to cut it off, etc., see below hugo docs link
# https://gohugo.io/content-management/summaries/
showPostSummary = false

# Optional
# If present, google analytics will be enabled
googleAnalytics = "UA-123456789-1"

# Optional
# If present, your favicon will display as the tab icon
# The value is the relative path to your favicon
# The favicon is also known as your tab icon or your bookmark icon
# It must have the extension of ".ico"
# To convert a ".jpg" or ".png" image to ".ico", see below link
# https://realfavicongenerator.net/
tabIcon = "favicon.ico"

# Required
[menu]

# The first nav menu item is required
# Additional nav menu items are optional
# The weight determines what order they will show in

# Required
[[menu.nav]]
name = "Posts"
url = "/"
weight = 1

# Optional
[[menu.nav]]
name = "About"
url = "/about/"
weight = 2

# Optional
[[menu.nav]]
name = "Contact"
url = "/contact/"
weight = 3
```

### Front Matter Dates

If you don't set `publishdate` in your front matter, it will fallback to `date`. 

If you don't set `lastmod` in your front matter, but you have `enableGitInfo = true` in your `config.toml`, then `lastmod` date will the git's last revision of the file.

If you don't set `lastmod` in your front matter, and you have `enableGitInfo = false` (or don't have that line at all) in your `config.toml`, then `lastmod` date will fallback to `date`. 

For more info see the hugo docs for [Configure Dates](https://gohugo.io/getting-started/configuration/#configure-dates). 

### Shortcodes

TODO blockquote, relimg, absimg

To use it, pass the author's name as an argument, then within the shortcode put the quote: 

```
{{% blockquote "Laura Ingalls" %}}
I am beginning to learn that it is the sweet, **simple** things of life which are the real ones after all.  
{{% /blockquote %}}
```

## Contribution

Pull requests, issues, and general feedback are welcomed.