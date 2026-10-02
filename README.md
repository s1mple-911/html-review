# HTML Review — Lab Work 3

A nine-page static website reviewing core HTML5 tags: each page documents one
group of tags with a definition, an attribute table, a code example and a
live rendered result, styled by a single shared stylesheet.

## Authors

- Asilbek Ermatov
- Partner: ___

## Pages

| # | File            | Topic                                              |
|---|-----------------|-----------------------------------------------------|
| 1 | `index.html`    | Home & page structure (`<!DOCTYPE>`, `<html>`, `<head>`, `<body>`, headings, `<p>`, `<div>`, `<span>`, comments) |
| 2 | `text.html`     | Text formatting (`<strong>`, `<em>`, `<blockquote>`, `<code>`, …) |
| 3 | `links.html`    | Links, images, video & audio (`<a>`, `<img>`, `<video>`, `<audio>`, `<source>`) |
| 4 | `lists.html`    | Lists (`<ul>`, `<ol>`, `<li>`, `<dl>`/`<dt>`/`<dd>`, nested lists) |
| 5 | `tables.html`   | Tables (`<table>`, `<thead>`, `<tbody>`, `<tfoot>`, `<colgroup>`) |
| 6 | `forms.html`    | Forms (`<form>`, `<label>`, `<input>` types, `<select>`, `<fieldset>`) |
| 7 | `media.html`    | Multimedia (`<figure>`, `<picture>`, `<iframe>`, `<canvas>`, `<svg>`, `<embed>`/`<object>`) |
| 8 | `semantic.html` | Semantic & layout (`<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`, `<details>`, `<time>`, `<address>`, Flexbox) |
| 9 | `metadata.html` | Metadata (`<meta>`, `<title>`, `<link>`, `<base>`, Open Graph, `<script defer>`) |

## Project structure

```
html-review/
├── index.html
├── text.html
├── links.html
├── lists.html
├── tables.html
├── forms.html
├── media.html
├── semantic.html
├── metadata.html
├── css/
│   └── style.css        # single shared stylesheet for every page
├── images/
│   ├── logo.svg                        # site logo (vector)
│   ├── icon-*.svg                      # 9 two-color icon cards for the home page
│   ├── hero.jpg                        # hero banner (generated with Python/Pillow)
│   ├── sample.jpg / sample-small.jpg / sample-large.jpg  # sample photos (Pillow)
│   ├── intro.mp4 / intro.webm / poster.jpg  # animated demo clip (generated with ffmpeg)
│   ├── tone.mp3 / tone.wav             # 2.5s chord tone (generated with ffmpeg)
│   └── README.txt                      # full asset list + regeneration commands
└── README.md
```

## Opening the site

This is a static site with no build step and no backend. Open it with a
local web server so relative links, fonts, audio and video all resolve the
same way they would once deployed (e.g. to GitHub Pages):

1. Open the `html-review` folder in VS Code.
2. Install the **Live Server** extension if you don't already have it.
3. Right-click `index.html` → **Open with Live Server**.
4. The site opens at a local address such as `http://127.0.0.1:5500/index.html`.

Opening the HTML files directly by double-clicking (`file://` URLs) will
mostly work too, but some browsers restrict `<iframe>`/`<video>` behavior on
`file://`, so Live Server is the recommended way to review the site.

## Notes

- All styling lives in `css/style.css` — no `style="..."` attributes or
  `<style>` tags are used anywhere in the HTML.
- Every image, video and audio file used on the site is a real local asset
  under `images/` (generated with Python/Pillow and ffmpeg) — nothing
  points at an external URL. See `images/README.txt` for the full list and
  the commands used to generate each one.
