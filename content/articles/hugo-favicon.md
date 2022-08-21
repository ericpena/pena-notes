---
title: "Adding Favicons"
author: "Eric Peña"
date: 2019-03-26T00:00:00-07:00
description: "Adding Favicons"
type: non-technical_note
draft: true
---

Nothing makes a website look polished like a clean, minimalistic favicon. This article quickly lists the steps to add a favicon to a Hugo website like this one.

1. Create a favicon in an art package like **Illustrator** or **Inkscape**.
2. Upload your image to [Real Favicon Generator](https://realfavicongenerator.net/)
3. Extract the favicon package it creates to the /static/ directory which lives in the root of your HUGO site.
4. Copy the given html and add it to your `/layouts/partials/head.html`

Example Code to Copy into `head.html`

```python
  <link rel="apple-touch-icon" sizes="180x180" href="/favicon/apple-touch-icon.png">
  <link rel="icon" type="image/png" sizes="32x32" href="/favicon/favicon-32x32.png">
  <link rel="icon" type="image/png" sizes="16x16" href="/favicon/favicon-16x16.png">
  <link rel="manifest" href="/favicon/site.webmanifest">
  <meta name="msapplication-TileColor" content="#da532c">
  <meta name="theme-color" content="#ffffff">
```