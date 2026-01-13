# Writing Blog Posts

This guide explains how to add new blog posts to your portfolio.

## The `_posts` Directory

Jekyll requires all blog posts to be stored in the `_posts` folder. The file naming convention is **critical**:

`YYYY-MM-DD-title-of-post.md`

**Examples:**
- `2026-01-13-my-first-post.md` (Valid)
- `my-first-post.md` (Invalid - missing date)
- `2026-1-13-post.md` (Invalid - month must be two digits)

## Front Matter

Every post must begin with "Front Matter" — a block of YAML between two lines of triple dashes `---`. This tells Jekyll how to process the file.

```markdown
---
layout: post
title:  "Your Post Title Here"
date:   2026-01-13 12:00:00 -0700
categories: category1 category2
---
```

- **layout**: Always use `post`.
- **title**: The headline that appears on the page.
- **date**: The publication date. Posts with future dates will not be published until that day.
- **categories**: (Optional) Helps organize your posts.

## Writing Content

After the second `---`, simply write your post in standard Markdown.

### Code Blocks
You can use triple backticks for syntax highlighting:

```python
def hello():
    print("Hello, World!")
```

### Images
You can include images using standard Markdown syntax. It's best to store images in an `assets/images` folder.

`![Alt text for image](/assets/images/my-image.jpg)`

## Drafts

If you want to work on a post without publishing it yet, you can create a `_drafts` folder. Files in this folder don't need a date in the filename.

To preview drafts locally:
```bash
bundle exec jekyll serve --drafts
```

