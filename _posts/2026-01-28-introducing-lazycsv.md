---
layout: post
title:  "Introducing LazyCSV: A Blazingly Fast CSV Viewer for Your Terminal"
date:   2026-01-28 00:00:00 -0000
categories: rust tui csv cli
---

Let's face it: for anyone working with data, CSV files are a daily reality. But viewing them shouldn't feel like a chore. Firing up a heavy spreadsheet application just to glance at a file is overkill, and wrestling with `less` on a large dataset is a recipe for frustration.

What if you could navigate huge CSVs with the same speed and comfort as navigating code in your favorite editor? What if your muscle memory for Vim keybindings could make you a data-browsing master?

It's time to get lazy—the smart way. Say hello to **LazyCSV**, a new terminal UI for CSV files, built from the ground up for speed and keyboard-driven efficiency.

```
┌─ lazycsv: sales_data.csv ─────────────────────────┐
│     │  A      │ ►B         │  C           │  D    │
├─────┼─────────┼────────────┼──────────────┼───────┤
│  #  │  ID     │  Date      │  Product     │  Qty  │
├─────┼─────────┼────────────┼──────────────┼───────┤
│  1  │  001    │ 2024-01-15 │ Widget A     │  100  │
│►2   │  002    │ [2024...] │ Gadget B     │   50  │
│  3  │  003    │ 2024-01-17 │ Doohickey... │   75  │
├────────────────────────────────────────────────────┤
│ [?] help │ [q] quit │ [ ] files │                 │
│ Row 2/100 │ Col B: Date (2/4) │ Cell: "2024..." │
├────────────────────────────────────────────────────┤
│ Files (1/2): ► sales.csv | customers.csv         │
└────────────────────────────────────────────────────┘
```

## The Lazy Advantage

Inspired by brilliant tools like [lazygit](https://github.com/jesseduffield/lazygit), LazyCSV is designed to make your life easier. Here's what makes it special:

-   ⚡ **Blazingly Fast:** Built in Rust, it handles over 100,000 rows at a buttery-smooth 60 FPS. No more waiting.
-   ⌨️ **Native Vim Keybindings:** Your fingers already know what to do. Use `hjkl`, `gg`, `G`, and other motions to fly through your data.
-   📁 **Seamless Multi-File Navigation:** This is a game-changer. LazyCSV treats all CSVs in a directory like browser tabs. Open one file, then cycle through all of them instantly with `[` and `]`.
-   🎯 **Zero-Config Simplicity:** It just works. The minimalist TUI puts your data front and center, with no clutter.

## Get Started in Seconds

If you have the Rust toolchain, you can be up and running in under a minute:

```bash
git clone https://github.com/funkybooboo/lazycsv.git
cd lazycsv
cargo install --path .
```

Then, point it at your data:

```bash
# Open a specific CSV file
lazycsv my_data.csv

# Or let it discover all CSVs in the current directory
lazycsv
```

Once inside, `hjkl` moves you around, and `?` reveals all available commands.

## The "Lazy" Philosophy

LazyCSV follows a simple but powerful creed:

1.  **Keyboard-First:** The mouse is optional.
2.  **Instantaneous:** It should feel fast and responsive.
3.  **Simple:** No configuration files, no hassle.
4.  **Powerful:** Enable maximum efficiency with minimum effort.

## The Road Ahead

LazyCSV is already a robust data viewer, but the journey is just beginning. The roadmap includes powerful features like cell editing, row/column manipulation, fuzzy searching, and sorting.

## Give It a Spin!

If you're a terminal enthusiast who wants a smarter, faster way to work with CSVs, LazyCSV was built for you. It’s a lightweight, powerful, and genuinely fun way to explore your data.

**Check it out on [GitHub](https://github.com/funkybooboo/lazycsv), give it a star, and let me know what you think!**
