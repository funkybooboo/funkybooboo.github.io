---
layout: page
title: lazyrts - Terminal RTS Game
permalink: /projects/lazyrts/
repo_url: https://github.com/funkybooboo/lazyrts
description: Real-time strategy in the terminal - AOE2 shrunk down until only the important parts are left, written in Zig.
---

**Repository:** [github.com/funkybooboo/lazyrts](https://github.com/funkybooboo/lazyrts)

lazyrts is real-time strategy in a terminal: like AOE2 shrunk down until only
the important parts are left. Two resources. Two unit types. Five buildings.
No ages, no tech tree, no save files.

## How It Works

*   **10 Hz tick loop, decoupled render:** game state is a plain struct - no globals, no heap in the hot path
*   **A-star pathfinding; BFS cluster growth for map generation**
*   **A working economy:** farms yield 250 food then go fallow (resow for wood), deer spawn in herds and leave carcasses that drain as they are gathered, trees fell after ten trips
*   **Keyboard-first:** hjkl/arrows cursor movement, Tab/Shift+Tab unit cycling, shift+dir multi-select, and a ? overlay that lists every key without pausing the game

## Technology Stack

*   **Language:** Zig 0.16
*   **TUI:** libvaxis, fetched automatically by the build

## Status

Milestone 3 (economy) shipped. Working on buildings (milestone 4).