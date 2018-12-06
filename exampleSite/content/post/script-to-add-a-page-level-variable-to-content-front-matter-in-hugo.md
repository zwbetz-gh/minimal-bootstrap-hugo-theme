---
title: "Script to add a page-level variable to content front matter in hugo"
date: 2018-10-10T12:43:20-05:00
publishdate: 2018-10-10
lastmod: 2018-10-11
draft: false
tags: ["hugo", "command-line", "awk"]
---

This was originally a question posed on the [hugo discussion forums](https://discourse.gohugo.io/t/set-frontmatter-params-in-list-template/14645). 

The user wanted to loop through all her content files and add a `weight` page-level variable to the front matter. The value of `weight` needed to be the first 2 characters of the content filename, since her content was named like `01_content.md`, `02_content.md`, etc.

She then wanted to `range` through her pages by their weight, like so:

```go
{{ range .Pages.ByWeight }}
<!-- some code -->
{{ end }}
```

## The script

```bash
#!/bin/bash

for file in *.md; do
    weight=${file:0:2}
    awk -v weight=$weight '/---/{
        count++
        if(count == 2){
        sub("---","weight: " weight "\n---",$0)
        }
    }
    {print}' $file > tmp && mv tmp $file
done
```

## Explained

Loop through all files in the directory with extension `.md`:

```bash
for file in *.md; do
    # ...
done
```

Set a variable using the first 2 characters of the filename:

```bash
weight=${file:0:2}
```

Call an `awk` program and pass it a `weight` variable:

```bash
awk -v weight=$weight
``` 

When the `awk` program encounters the 2nd occurrence of `---` (which is how you end front matter in YAML), it inserts the `weight` page-level variable on the line above:

```bash
'/---/{
    count++
    if(count == 2){
    sub("---","weight: " weight "\n---",$0)
    }
}
{print}'
```

Redirect the output of the `awk` program to a tmp file, then overwrite the original content file with the tmp file:

```bash
> tmp && mv tmp $file
```

## Result

Original `01_content.md`:

```yml
---
title: "Some title"
draft: false
---
```

Updated `01_content.md`:

```yml
---
title: "Some title"
draft: false
weight: 01
---
```