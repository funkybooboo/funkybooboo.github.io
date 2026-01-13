---
layout: post
title:  "Building a Portfolio with Jekyll"
date:   2026-01-13 12:00:00 -0700
categories: jekyll web-development
---

Setting up a personal portfolio is a rite of passage for every developer. I decided to build mine using **Jekyll**, a static site generator that pairs perfectly with GitHub Pages.

## Why Jekyll?

I chose Jekyll for a few reasons:

1.  **Simplicity**: It transforms plain text (Markdown) into static websites. No databases, no complex backend.
2.  **GitHub Integration**: GitHub Pages supports Jekyll natively. I can push my changes to the `main` branch, and GitHub builds and serves the site automatically.
3.  **Control**: I have full control over the HTML and CSS if I want it, but the defaults are great for getting started quickly.

## The Setup

The setup was straightforward. I initialized a new repository, created a `Gemfile` to manage dependencies, and set up a basic `_config.yml`.

```ruby
# Gemfile
source "https://rubygems.org"
gem "github-pages", group: :jekyll_plugins
gem "erb"
```

With just a few commands, I had a local development server running:

```bash
bundle exec jekyll serve
```

## What's Next?

Now that the foundation is laid, I plan to:
*   Document my journey building **Alle**, my task management app.
*   Share insights on Multi-Agent Systems from my research.
*   Write about the "Twelve-Factor App" methodology and why I love it.

Stay tuned for more updates!
