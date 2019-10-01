# Minimal Bootstrap Hugo Theme

[![Netlify Status](https://api.netlify.com/api/v1/badges/e3929c16-50cc-4e8f-a8f2-e63acc35c83d/deploy-status)](https://app.netlify.com/sites/minimal-bootstrap-hugo-theme/deploys)

A minimal hugo theme made with bootstrap that focuses on content readability. 

## Table of contents

- [Demo](#demo)
- [Minimum Hugo version](#minimum-hugo-version)
- [Installation](#installation)
- [Updating](#updating)
- [Run example site](#run-example-site)
- [Configuration](#configuration)
- [Favicons](#favicons)
- [Override](#override)
  - [Homepage example](#homepage-example)
  - [Configure cookie consent](#configure-cookie-consent)
- [Syntax highlighting](#syntax-highlighting)
- [Shortcodes](#shortcodes)
  - [`blockquote`](#blockquote)
  - [`imgAbs`](#imgabs)
  - [`imgRel`](#imgrel)
  - [`imgProc`](#imgproc)
  - [`mastodon`](#mastodon)
- [Getting help](#getting-help)
- [Stackbit Deploy](#stackbit-deploy)

## Demo

https://minimal-bootstrap-hugo-theme.netlify.com/

## Minimum Hugo version

Hugo version `0.58.3` or higher is required. View the [Hugo releases](https://github.com/gohugoio/hugo/releases) and download the binary for your OS.

## Installation

From the root of your site:

```
git submodule add https://github.com/zwbetz-gh/minimal-bootstrap-hugo-theme.git themes/minimal-bootstrap-hugo-theme
```

## Updating

From the root of your site:

```
git submodule update --remote --merge
```

## Run example site

From the root of `themes/minimal-bootstrap-hugo-theme/exampleSite`:

```
hugo server --themesDir ../..
```

## Configuration

Copy the `config.toml` from the [`exampleSite`](https://github.com/zwbetz-gh/minimal-bootstrap-hugo-theme/tree/master/exampleSite), then edit as desired.

## Favicons

Upload your image to [RealFaviconGenerator](https://realfavicongenerator.net/) then copy-paste the generated favicon files under `static`. 

## Override

### Homepage example

As an example, let's say you didn't like the default homepage, and wanted to design one of your own. To do this, you would:

1. Copy file `YOUR_SITE/themes/minimal-bootstrap-hugo-theme/layouts/index.html`
1. Paste that file to `YOUR_SITE/layouts/index.html`
1. Edit `index.html` as desired

### Configure cookie consent

You can change the position, layout, color palette, "Learn more" link, compliance type, and custom text of the cookie consent popup. To do this, you would:

1. Copy file `YOUR_SITE/themes/minimal-bootstrap-hugo-theme/layouts/partials/cookie-consent.html`
1. Paste that file to `YOUR_SITE/layouts/partials/cookie-consent.html`
1. Complete the [cookie consent wizard](https://cookieconsent.insites.com/download/)
1. Paste the generated code from the wizard into `cookie-consent.html`

## Syntax highlighting

Hugo has built-in syntax highlighting, provided by Chroma. To use it, add these lines to your `config.toml` right after the `theme` line:

```
pygmentsCodefences = true
pygmentsStyle = "pygments"
```

Here, `"pygments"` is just the name of the Chroma style to be used. Checkout the [Chroma style gallery](https://xyproto.github.io/splash/docs/all.html) and choose the style you like.

For a deeper dive see the [hugo docs for syntax highlighting](https://gohugo.io/content-management/syntax-highlighting/).

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

### `mastodon`

This will embed a toot in an `iframe`.

These arguments are optional: `width`, `height`.

```
{{% mastodon
status="https://mastodon.social/@kevingimbel/100700713283716694"
width="1000" height="500" %}}
```

## Getting help

If you run into an issue that isn't answered by this documentation or the [`exampleSite`](https://github.com/zwbetz-gh/minimal-bootstrap-hugo-theme/tree/master/exampleSite), then visit the [Hugo forum](https://discourse.gohugo.io/). The folks there are helpful and friendly. **Before** asking your question, be sure to read the [requesting help guidelines](https://discourse.gohugo.io/t/requesting-help/9132). Feel free to tag me in your question, my forum username is [@zwbetz](https://discourse.gohugo.io/u/zwbetz/summary).

## Stackbit Deploy

This theme is ready to import into Stackbit. This theme can be deployed to Netlify and you can connect any headless CMS including Forestry, NetlifyCMS, DatoCMS, or Contentful.  

[![Create with Stackbit](https://assets.stackbit.com/badge/create-with-stackbit.svg)](https://app.stackbit.com/create?theme=https://github.com/zwbetz-gh/minimal-bootstrap-hugo-theme)
