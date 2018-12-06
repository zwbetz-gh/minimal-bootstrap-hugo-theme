---
title: "{{ replace .Name "-" " " }}"
date: {{ .Date }}
publishdate: {{ now.Format "2006-01-02" }}
lastmod: {{ now.Format "2006-01-02" }}
draft: true
tags: []
---
