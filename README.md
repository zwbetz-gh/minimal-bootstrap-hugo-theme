# Minimal Bootstrap Hugo Theme

A minimal hugo theme made with bootstrap that focuses on content readability. 

The typical page size, if the page has no images, is under 100kb. It's even lower if assets are compressed by your web server. The only other assets loaded besides the HTML and the Bootstrap CSS are: 

* Favicon (if enabled)
* Google Analytics JS (if enabled)
* Cookie Consent CSS/JS (if enabled)

Demos:

* Dev demo, immediate updates: <https://minimal-bootstrap-hugo-theme.netlify.com/>
* Hugo Themes demo, weekly-ish updates: <https://themes.gohugo.io/theme/minimal-bootstrap-hugo-theme/>

## Table of Contents

* [Hugo Version](#hugo-version)
* [Installation Options](#installation-options)
    * [Add it as a Git Submodule](#add-it-as-a-git-submodule)
    * [Download a Zip and Unzip it](#download-a-zip-and-unzip-it)
* [Update Options](#update-options)
    * [Git Submodule](#git-submodule)
    * [Zip](#zip)
* [Example Site Layout](#example-site-layout)
* [Configuration](#configuration)
* [Favicon and Apple Touch Icon](#favicon-and-apple-touch-icon)
* [Override](#override)
    * [Homepage Example](#homepage-example)
    * [Configure Cookie Consent](#configure-cookie-consent)
* [Syntax Highlighting](#syntax-highlighting)
* [Front Matter Dates](#front-matter-dates)
    * [publishdate](#publishdate)
    * [lastmod](#lastmod)
* [Shortcodes](#shortcodes)
    * [blockquote](#blockquote)
    * [imgAbs](#imgabs)
    * [imgRel](#imgrel)
    * [imgProc](#imgproc)
* [Getting Help](#getting-help)
* [Contribution](#contribution)

## Hugo Version

This theme requires hugo version `0.48` or above. Take a look at the [hugo releases](https://github.com/gohugoio/hugo/releases) and download the hugo binary for your operating system. 

## Installation Options

### Add it as a Git Submodule

1. `cd YOUR_SITE`
1. `git submodule add https://github.com/zwbetz-gh/minimal-bootstrap-hugo-theme.git themes/minimal-bootstrap-hugo-theme`

### Download a Zip and Unzip it

1. [Download a zip of the theme from GitHub](https://github.com/zwbetz-gh/minimal-bootstrap-hugo-theme/archive/master.zip)
1. Unzip it into `YOUR_SITE/themes/`
1. Once unzipped, it will be named `minimal-bootstrap-hugo-theme-master`. Rename it to `minimal-bootstrap-hugo-theme`

## Update Options

### Git Submodule

If you used the git submodule option to install the theme, update it by running:

1. `cd YOUR_SITE`
1. `git submodule update --remote --merge`

### Zip

If you downloaded a zip to install the theme, just do those installation steps again to update it.

## Example Site Layout

This theme expects your _posts_ to be under the `post` folder. 

If you want to use a different folder, then override the [`post-list.html`](https://github.com/zwbetz-gh/minimal-bootstrap-hugo-theme/blob/master/layouts/partials/post-list.html) partial and replace `post` with the name of your folder. 

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

## Configuration

Copy the `config.toml` from the [`exampleSite`](https://github.com/zwbetz-gh/minimal-bootstrap-hugo-theme/tree/master/exampleSite), then edit as desired. 

## Favicon and Apple Touch Icon

Place your `favicon.ico` and `apple-touch-icon.png` files at the root of your site, i.e. place them directly under `YOUR_SITE/static/`. See `exampleSite/static/` for other (optional) favicon files.

To generate all these favicons from a single image, use the [RealFaviconGenerator](https://realfavicongenerator.net/) online tool. After using the tool, you'll be prompted to download a zip of your favicon package. You'll then want to extract the zip contents directly into `YOUR_SITE/static/`. 

## Override

### Homepage Example

As an example, let's say you didn't like the default homepage, and wanted to design one of your own. To do this, you would:

1. Copy file `YOUR_SITE/themes/minimal-bootstrap-hugo-theme/layouts/index.html`
1. Paste that file to `YOUR_SITE/layouts/index.html`
1. Edit `index.html` as desired

### Configure Cookie Consent

You can change the position, layout, color palette, "Learn more" link, compliance type, and custom text of the cookie consent popup. To do this, you would:

1. Copy file `YOUR_SITE/themes/minimal-bootstrap-hugo-theme/layouts/partials/cookie-consent.html`
1. Paste that file to `YOUR_SITE/layouts/partials/cookie-consent.html`
1. Complete the [cookie consent wizard](https://cookieconsent.insites.com/download/)
1. Paste the generated code from the wizard into `cookie-consent.html`

## Syntax Highlighting

Hugo has built-in syntax highlighting, provided by Chroma. To use it, add these lines to your `config.toml` right after the `theme` line:

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

This will insert an image into your content by absolute path. To use it, pass the `pathURL` of your image. 

These arguments are optional: `alt`, `class`, `style`.

```
{{< imgAbs 
pathURL="img/some-img.png" 
alt="Some description" 
class="some-class" 
style="some-style" >}}
```

### `imgRel`

This will insert an image into your content by relative path. To use it, pass the `pathURL` of your image. 

These arguments are optional: `alt`, `class`, `style`.

```
{{< imgRel 
pathURL="img/some-img.png" 
alt="Some description" 
class="some-class" 
style="some-style" >}}
```

### `imgProc`

This will process an image from a [page bundle](https://gohugo.io/content-management/page-bundles/), then provide a link to the original image. To use it, pass the image name, command, and command options. 

The `command` argument will be one of: `Resize`, `Fit`, `Fill`. For a deeper dive see the [hugo docs for image processing](https://gohugo.io/content-management/image-processing/). 

These arguments are optional: `alt`, `class`, `style`.

The below example resizes an image to 800px width, while keeping the aspect ratio. 

```
{{< imgProc 
img="some-img.png" 
command="Resize" 
options="800x" 
alt="Some description" 
class="some-class" 
style="some-style" >}}
```

## Getting Help

If you run into an issue that isn't answered by this documentation, then head over to the [hugo discussion forum](https://discourse.gohugo.io/). The folks there are quite helpful and friendly. 

**Before** asking your question, be sure to read the [requesting help guidelines](https://discourse.gohugo.io/t/requesting-help/9132). 

## Contribution

Pull requests, issues, and general feedback are welcomed.
