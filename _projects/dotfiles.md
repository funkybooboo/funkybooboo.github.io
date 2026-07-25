---
layout: page
title: Dotfiles - Declarative System Configuration Framework
permalink: /projects/dotfiles/
repo_url: https://github.com/funkybooboo/dotfiles
description: A idempotent, non-fatal migration system that declaratively provisions and converges every Arch Linux machine I own.
---

**Repository:** [github.com/funkybooboo/dotfiles](https://github.com/funkybooboo/dotfiles)

A declarative configuration-management framework I built to provision and
converge every Arch Linux machine I own from a single Git repository. Rather
than a pile of dotfiles, it is a versioned migration system that brings any
new or existing machine to a known state with one command (`./migrate.sh`),
and re-runs safely and idempotently.

## Key Features

*   **Migration engine:** 124 ordered, idempotent, non-fatal migrations that
    install packages, link config, deploy system files, and enable services.
    A single failure records a warning and continues --- one broken step never
    aborts a whole-machine convergence.
*   **Layered 7-tier install policy:** pacman -> upstream release assets ->
    nix -> from source -> flatpak -> appimage -> snap. Each tier is preferred
    over the next for provenance and reproducibility, with the AUR removed
    entirely.
*   **Nix flake integration:** a local flake wraps nixpkgs with
    `allowUnfree = true` and pins the nixpkgs revision via `flake.lock`, so
    `nix profile add .#<pkg>` works for free and unfree packages without
    `--impure` or env vars.
*   **Hardened supply chain:** upstream release assets are SHA-256 verified
    against upstream checksum files and GPG signature-verified where a release
    key exists --- binaries are fetched directly from signed upstream releases
    rather than repackaged third-party builds.
*   **Dual-architecture:** the same migrations converge both the x86_64
    workstation and an aarch64 Raspberry Pi node.

## Technology Stack

*   **Core:** Bash migrations, Nix flakes, pacman
*   **Linking:** symlink trees for tracked config (`link_tree`/`link_file`/
    `link_dir`), deployed `/etc` files (`deploy_etc_file`)
*   **Services:** systemd user/system service enablement helpers
*   **Verification:** SHA-256, GPG, `vercmp` version checks