---
layout: page
title: Alle - Task Management
permalink: /projects/alle/
repo_url: https://github.com/funkybooboo/alle
description: An open-source minimalist to-do list app inspired by Teuxdeux.
---

**Repository:** [github.com/funkybooboo/alle](https://github.com/funkybooboo/alle)

Alle is a custom-built task management SaaS application serving 100+ daily active users. Architected from the ground up to extend TeuxDeux functionality with features tailored to modern productivity workflows.

## Key Features

*   **Drag-and-Drop Organization:** Intuitive task management with smooth animations
*   **Offline-First Architecture:** Service workers enable seamless offline functionality with automatic sync
*   **Automatic Rollover:** Unfinished tasks intelligently move to the next day
*   **Recurring Tasks:** Flexible scheduling patterns for repeating tasks
*   **99.9% Uptime:** Reliable deployment with Docker Compose orchestration

## Technology Stack

*   **Frontend:** React 19, TypeScript
*   **Backend:** Rust (Tokio), GraphQL API, Tower HTTP framework
*   **Database:** SQLite with SeaORM
*   **Testing:** 60+ tests (unit, integration, E2E) with 85% code coverage
*   **Deployment:** Docker Compose

## Challenges & Solutions

Building Alle required solving complex state management issues to ensure the drag-and-drop interface felt snappy while maintaining data consistency with the backend. Implemented optimistic UI updates with conflict resolution strategies to handle offline scenarios gracefully.
