---
layout: page
title: Erledigen - Task Management
permalink: /projects/erledigen/
repo_url: https://github.com/funkybooboo/erledigen
description: A unified task manager inspired by TeuxDeux - daily list, Someday capture, habits, and projects in one place.
---

**Repository:** [github.com/funkybooboo/erledigen](https://github.com/funkybooboo/erledigen)

Erledigen is a unified task manager built around one idea: you should only need
one place to manage your work and your life. The daily list is the execution
surface, Someday is the capture net, and habits generate instances into the
daily list automatically. Everything is organized with one tag system that
works across tasks, groups, Someday, and filters.

## Key Features

*   **Daily list:** a continuously-scrolling list of day sections with inline add/edit and a month minimap for orientation
*   **Someday panel:** a right-side capture net for unscheduled work, organized into tag-based groups, drag-to-resize and collapsible
*   **Habits and recurring tasks:** natural-language templates ("water plants every friday at 9am") generate instances into the daily list, with streak tracking
*   **Projects:** collections of ordered tasks with activate/deactivate and a detail view
*   **Sub-tasks:** nested tasks under a parent, with completion rolling up
*   **Command palette:** Cmd/Ctrl+K or / to search across task text, notes, and tags, plus a /-prefixed command mode
*   **Keyboard-first:** vim + arrow navigation, g-sequences for modals, priority keys, and undo for every UI action, with keybindings shown on hover
*   **Trash with undo:** soft delete with an undo toast, restore from Trash, and manual purge
*   **Privacy first:** no analytics, no telemetry, no tracking - your data stays in your own database

## Technology Stack

*   **Frontend:** SvelteKit with Svelte 5 runes, hand-written scoped CSS over OKLCH design tokens
*   **Backend:** Bun runtime serving a REST API + WebSocket server; every mutation broadcasts to all connected clients for real-time sync
*   **Language:** TypeScript end-to-end
*   **API:** schema-first OpenAPI 3.1 generated from Zod, served at /openapi.yaml and /openapi.json
*   **Architecture:** adapter pattern - every subsystem sits behind an interface so implementations swap without touching application code, with a pluggable storage adapter (migrations-managed database in dev/prod, memory adapter in tests)
*   **Quality:** Biome lint and formatting, Bun test units, Playwright E2E, Bruno API tests, Storybook for component development, CI on GitHub Actions
*   **Tooling:** mise task runner, Docker/podman compose stacks for dev, prod, and tests

## Monorepo Layout

Client (SvelteKit frontend), server (Bun REST + WebSocket API), and shared
(types, adapter interfaces, constants) packages, plus user and developer docs,
ADRs, and a release-by-release roadmap in the repo.