# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a personal academic website for Nicolás Violante Grezzi, hosted on GitHub Pages at `nviolante25.github.io`. The entire site is a single static file — no build step, no package manager, no framework.

## Structure

- `index.html` — the entire website (HTML + inline CSS + inline JS)
- `assets/images/` — profile photo and publication thumbnails (named `publi_NN_slug.png`)
- `assets/docs/resume.pdf` — CV/resume

## Development

Preview locally by opening `index.html` in a browser, or serve it with any static file server:

```bash
python3 -m http.server 8000
```

Deploying is just pushing to the `master` branch — GitHub Pages serves it automatically.

## Architecture

**Styling:** Tailwind CSS loaded from CDN (`cdn.tailwindcss.com`). No config file. Custom CSS lives in a `<style>` block in `<head>` and handles layout (fixed sidebar + scrollable main), responsive breakpoints, and component-specific styles.

**Layout:** Fixed left sidebar (250 px) with profile, contact icons, and nav links. Right main area scrolls independently. On mobile (`max-width: 768px`) the sidebar stacks above content and the nav becomes horizontal.

**Navigation:** Vanilla JS in a `<script>` block at the bottom of `<body>`. It highlights the active nav link on scroll and smooth-scrolls to sections on click.

**Publications:** Each publication is a `.publication-card` div with a thumbnail image, authors, venue, action buttons (Website, PDF, Code, Video), and a collapsible abstract toggled by `toggleAbstract()`. New publications go inside `#publications-container` in reverse-chronological order. Thumbnail images follow the naming convention `publi_NN_slug.png`.

**News:** Items are `<div class="flex items-start">` rows with a date badge (`<span class="text-sm text-gray-500 bg-emerald-100 ...">MM/YYYY</span>`) and a description paragraph. Add new items at the top of `#news`.
