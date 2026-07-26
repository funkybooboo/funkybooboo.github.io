---
layout: page
title: Alle - Task Management
permalink: /projects/alle/
repo_url: https://github.com/funkybooboo/alle
description: An open-source minimalist to-do app inspired by Teuxdeux, built as a TypeScript monorepo.
---

**Repository:** [github.com/funkybooboo/alle](https://github.com/funkybooboo/alle)

Alle is a custom-built task management application inspired by TeuxDeux, built
from the ground up as a TypeScript monorepo with a focus on a clean,
maintainable architecture and adapter-pattern design.

## Key Features

*   **Drag-and-Drop Organization:** Intuitive task management with smooth interactions
*   **Automatic Rollover:** Unfinished tasks roll forward to the next day
*   **Recurring Tasks:** Flexible scheduling patterns for repeating tasks
*   **Repository Pattern Data Layer:** A pluggable data layer (currently in-memory Map-backed), designed to swap to a persistent backend without changing business logic

## Technology Stack

*   **Frontend:** SvelteKit with Svelte 5 and TypeScript
*   **Backend:** Bun runtime (TypeScript) with an adapter-pattern architecture
*   **API:** OpenAPI, with schemas validated using Zod (`zod-to-openapi`)
*   **Testing:** Unit tests via Bun's test runner and E2E tests via Playwright across the client, server, and shared packages
*   **Monorepo:** Workspaces for shared types and tooling (biome, mise)

## Architecture

Alle is structured as a monorepo with a shared package and separate client and
server packages, following an adapter pattern with a repository abstraction for
data access so the storage implementation can change without touching domain
logic. The API is defined semantically with Zod schemas and surfaced through
OpenAPI tooling rather than a hand-rolled endpoint layer.