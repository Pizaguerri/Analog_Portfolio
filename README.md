# Analog

A static photography portfolio and blog built with Hugo, designed to replace platforms like Instagram, Visura or Squarespace and give you full ownership of your work.

Built by a documentary photographer and visual anthropologist who wanted out of the platforms.

![Hugo](https://img.shields.io/badge/Hugo-0.161+-blue) ![License](https://img.shields.io/badge/license-MIT-green) ![Cloudflare Pages](https://img.shields.io/badge/deployed%20on-Cloudflare%20Pages-orange)

---

## What this is

Analog is a minimal, fast, multilingual Hugo template for photographers and visual researchers. It includes:

- **Justified photo gallery** with lightbox (PhotoSwipe)
- **Slider** on the home page for featured projects
- **Blog** with featured image support
- **Multilingual** (Catalan, Spanish, English — or any language you configure)
- **Dark mode** support
- **RSS feed**
- **Git LFS** ready for large image files
- **Obsidian** compatible — write your content in Obsidian, publish with a git push
- Deploys for free on **Cloudflare Pages**

---

## Tech stack

- [Hugo](https://gohugo.io) — static site generator
- [PhotoSwipe](https://photoswipe.com) — lightbox gallery
- [Cloudflare Pages](https://pages.cloudflare.com) — free hosting with global CDN
- [Obsidian](https://obsidian.md) — optional content writing workflow
- [Git LFS](https://git-lfs.com) — large file storage for images
- HTML / SCSS / Vanilla JS — no frameworks, no dependencies

---

## Project structure

```
analog/
├── content/
│   ├── _index.{ca,es,en}.md      # Home page by language
│   ├── about/
│   │   └── _index.{ca,es,en}.md  # About page by language
│   ├── blog/
│   │   ├── _index.{ca,es,en}.md
│   │   └── post-name/
│   │       ├── index.ca.md        # Post content (one file per language)
│   │       └── featured.jpg       # Featured image (filename must contain "featured")
│   └── projects/
│       ├── _index.{ca,es,en}.md
│       └── project-name/
│           ├── index.ca.md        # Project content
│           ├── feature.jpg        # Cover image (filename must contain "feature")
│           └── photo-01.jpg       # Gallery images
├── layouts/
│   ├── _default/                  # Base templates
│   ├── blog/                      # Blog templates
│   ├── page/                      # Static page templates
│   └── partials/                  # Reusable components
├── assets/
│   ├── css/                       # SCSS stylesheets
│   └── js/                        # JavaScript
├── static/
│   └── images/                    # Static images (logo, profile pic, favicons)
├── i18n/                          # Translation strings
├── archetypes/                    # Content templates
└── hugo.toml                      # Main configuration
```

---

## Getting started

### Requirements

- [Hugo extended](https://gohugo.io/installation/) v0.158+
- [Git LFS](https://git-lfs.github.com/) (for image handling)

### Installation

```bash
git clone https://github.com/Pizaguerri/Analog.git
cd Analog
git lfs install
hugo server -D
```

The site will be available at `http://localhost:1313`.

---

## Adding content

### New photography project

```bash
hugo new projects/project-name/index.ca.md
```

This uses the `archetypes/proyectos.md` template and generates the correct frontmatter. Place your images in the same folder as the markdown file.

**Frontmatter reference:**

```yaml
---
title: "Project title"
date: 2024-01-15
draft: true           # Set to false to publish
description: ""
weight: 10            # Display order (lower = first)
featured: true        # Show in home slider
private: false        # Hide from project list
gallery_position: top # "top" or "bottom" relative to text
tags:
  - Portfolio
resources:
  - src: feature.jpg
    title: ""
    params:
      hidden: true    # Prevents duplicate in gallery
---
```

### New blog post

```bash
hugo new blog/post-name/index.ca.md
```

Add a `featured.jpg` image to the post folder — it will appear as the cover image automatically.

### Image export settings (Lightroom / Capture One)

- **Long edge:** 1600px
- **Quality:** 82–85%
- **Format:** JPEG
- **Color space:** sRGB

Hugo processes and resizes images automatically. Do not export at full resolution.

---

## Obsidian workflow (optional)

You can write your content directly in Obsidian and sync it to Hugo via a symlink:

```bash
ln -s /path/to/hugo/content /path/to/obsidian/vault/content
```

From that point, anything you write in Obsidian under `content/` is immediately visible to Hugo.

---

## Deployment

### Cloudflare Pages (recommended, free)

1. Push your repo to GitHub or Codeberg
2. Connect the repo in Cloudflare Pages dashboard
3. Set build command: `hugo --minify`
4. Set output directory: `public`
5. Add environment variable: `HUGO_VERSION = 0.161.1`

Every push to `main` triggers an automatic deploy.

---

## Multilingual setup

The template supports any number of languages. Languages are configured in `hugo.toml`. Each piece of content can have one file per language (`index.ca.md`, `index.es.md`, `index.en.md`). You only need to create the files for the languages you want — missing translations are simply not shown.

---

## License

Code: [MIT License](LICENSE)

Content (photos, texts) in the demo is © UNSPLASH — not included in the MIT license.

Built with the help of [Claude](https://claude.ai) (Anthropic).

---

## Author

[Pablo Izaguerri](https://pabloizaguerri.org) — documentary photographer and visual anthropologist based in Barcelona.
