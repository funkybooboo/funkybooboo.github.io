---
layout: page
title: Alle - Task Management
permalink: /projects/alle/
repo_url: https://github.com/funkybooboo/alle
description: An open-source minimalist to-do list app inspired by Teuxdeux.
---

**Repository:** [github.com/funkybooboo/alle](https://github.com/funkybooboo/alle)

Alle is an open-source minimalist to-do list and planning application inspired by Teuxdeux. It is designed to offer a clean, distraction-free interface for managing daily tasks.

## Key Features

*   Drag-and-Drop Organization: Easily move tasks between days or reorder them within a list.
*   Offline Functionality: Works seamlessly without an internet connection, syncing when connectivity is restored.
*   Automatic Rollover: Unfinished tasks automatically move to the next day, ensuring nothing gets lost.
*   Recurring Tasks: Support for tasks that repeat on a schedule.

## Technology Stack

*   Frontend: React 19, TypeScript
*   Backend: Rust (Tokio), GraphQL
*   Database: SQLite (via SeaORM)
*   Deployment: Docker Compose

## Challenges & Solutions

Building Alle required solving complex state management issues to ensure the drag-and-drop interface felt snappy while maintaining data consistency with the backend, especially when handling offline updates.
