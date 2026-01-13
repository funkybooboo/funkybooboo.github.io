# Managing Projects

This site uses a Jekyll **Collection** to manage portfolio projects. This allows for a structured and scalable way to add new projects without manually updating the main `projects.md` list every time.

## Directory Structure

All detailed project pages are stored in the `_projects/` directory.

- `_projects/alle.md`
- `_projects/rylee.md`
- `_projects/insighthub.md`
- ...

## Adding a New Project

To add a new project, create a new markdown file in the `_projects/` folder (e.g., `_projects/my-new-app.md`).

### Front Matter

Each project file **must** include specific Front Matter to be correctly displayed on the site.

```markdown
---
layout: page
title: Project Name
permalink: /projects/project-slug/
repo_url: https://github.com/username/repo-name
description: A short, one-sentence summary for the list view.
---
```

- **layout**: Use `page` (or a custom `project` layout if you create one).
- **title**: The name of the project.
- **permalink**: The URL where this project will live (e.g., `/projects/alle/`).
- **repo_url**: (Optional) The direct link to the GitHub repository.
- **description**: A brief summary used on the main Projects listing page.

### Content

Below the Front Matter, write the detailed description of your project using Markdown.

## The Projects Index (`projects.md`)

The main `/projects/` page (`projects.md` in the root) automatically loops through all files in the `_projects` collection. You generally **do not** need to edit this file when adding a new project.

It uses logic like this:

```liquid
{% for project in site.projects %}
  <h2><a href="{{ project.url }}">{{ project.title }}</a></h2>
  <p>{{ project.description }}</p>
{% endfor %}
```
