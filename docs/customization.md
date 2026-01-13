# Customization Guide

This document explains how to customize the content and look of your portfolio.

## Configuration

The main configuration file is `_config.yml`. Here you can set site-wide variables:

-   **title**: The title of your site.
-   **description**: Used by search engines and social media.
-   **theme**: The Jekyll theme used (currently `minima`).

## Adding Content

### Pages
To create a new page (e.g., "About"), create a markdown file in the root directory:

**about.md**
```markdown
---
layout: page
title: About
permalink: /about/
---

This is the content of my about page.
```

### Blog Posts
If you want to add blog posts, place them in the `_posts` directory. The naming convention is crucial:
`YYYY-MM-DD-title-of-post.md`

Example: `_posts/2023-10-27-my-first-project.md`

```markdown
---
layout: post
title:  "My First Project"
date:   2023-10-27 12:00:00 -0400
categories: projects
---

Details about my project...
```

## Changing the Theme

This site uses the `minima` theme by default. To change it:

1.  Open `_config.yml`.
2.  Change `theme: minima` to another supported theme (e.g., `jekyll-theme-cayman`).
3.  Update your `Gemfile` to include the new theme gem if it's not already in `github-pages`.
4.  Run `bundle install`.
5.  Restart your local server.

## Navigation

To add links to the navigation header, you typically just need to create a page with a `title` in the front matter. The `minima` theme automatically adds pages to the header.
