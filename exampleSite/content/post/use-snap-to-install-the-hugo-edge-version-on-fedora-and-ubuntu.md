---
title: "Use Snap to install the Hugo edge version on Fedora and Ubuntu"
date: 2018-10-26T12:59:51-05:00
publishdate: 2018-10-26
lastmod: 2018-10-26
draft: false
aliases:
  - /use-snap-to-install-the-hugo-edge-version-on-fedora/
tags: ["hugo", "snap", "fedora", "ubuntu"]
---

If you are using the Fedora or Ubuntu Linux distributions -- I'm currently on Fedora 28 -- and would like to [help test the latest development version of Hugo](https://discourse.gohugo.io/t/help-test-upcoming-hugo-0-50/14880), or if you just want to be on the bleeding-edge of things, this post is for you. 

## Fedora-only steps

To get started, [install Snap on Fedora](https://docs.snapcraft.io/installing-snap-on-fedora/6755):

```
sudo dnf install snapd
```

Add the [Snap directory](https://docs.snapcraft.io/commands-and-aliases/3950) to your `PATH` by adding this line to your `~/.bashrc` file. Then restart your terminal to pick up the change: 

```
export PATH="$PATH:/var/lib/snapd/snap/bin"
```

## Ubuntu-only steps

Ubuntu 16.04 and above come with [Snap already installed](https://docs.snapcraft.io/installing-snap-on-ubuntu/6740). If you're using an older Ubuntu version, install Snap by running:

```
sudo apt update && sudo apt install snapd
```

Check if the Snap directory is on your `PATH` by listing each entry:

```
echo $PATH | tr ':' '\n'
```

If you don't see `/snap/bin` listed, then add this line to your `~/.bashrc` file. Then restart your terminal to pick up the change: 

```
export PATH="$PATH:/snap/bin"
```

## Install Hugo

See which Snap channels are available for Hugo:

```
snap info hugo
```

Install Hugo from the edge channel:

```
sudo snap install hugo --channel=edge
```

Or, if you prefer Hugo Extended -- which has the [Hugo Pipes](https://gohugo.io/hugo-pipes/) feature -- install it from the extended edge channel:

```
sudo snap install hugo --channel=extended/edge
```

Lastly, confirm the location and version of Hugo that was intalled:

```
which hugo && hugo version
```

Happy testing :)

## Update or remove Hugo

Snaps are [updated automatically](https://docs.snapcraft.io/keeping-snaps-up-to-date/7022). To manually update Hugo:

```
sudo snap refresh hugo
```

To remove Hugo:

```
sudo snap remove hugo
```