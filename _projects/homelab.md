---
layout: page
title: Homelab - Proxmox Virtualization Cluster
permalink: /projects/homelab/
repo_url: https://github.com/funkybooboo/homelab
description: A 5-node Proxmox VE cluster backed by TrueNAS Scale, running ~19 HA-managed LXC containers over a Tailscale mesh.
---

**Repository:** [github.com/funkybooboo/homelab](https://github.com/funkybooboo/homelab)

A self-hosted infrastructure platform built on a 5-node Proxmox VE cluster,
backed by TrueNAS Scale and fronted by a Tailscale mesh VPN. The cluster runs
around 19 LXC workloads under high-availability management, demonstrating
real-world virtualization, storage, and network engineering at homelab scale.

## Architecture

*   **Compute:** 5-node Proxmox VE cluster --- four `x86_64` nodes
    (`pve-framework`, `pve-thermaltake`, `pve-aspires`, `pve-aspiree15`)
    plus a Raspberry Pi running **PxVirt** (the ARM port of Proxmox VE) as a
    quorum-only witness, giving the cluster a 5-vote majority across mixed
    x86/ARM hardware.
*   **Storage backend:** **TrueNAS Scale** (`tnas`) exporting NFS for shared
    container rootdisks (`pve-shared`) and nightly `vzdump` backups
    (`pve-backups`), with per-node `local-lvm` for node-local storage.
*   **Workload model:** **LXC containers** (not full VMs) for density,
    managed as **HA resources** via `ha-manager` so the cluster automatically
    restarts a failed guest on a surviving node.
*   **Networking:** **Tailscale** mesh VPN connecting every node and client,
    with `tailscale serve --bg --https 443` giving each service automatic
    TLS-terminated HTTPS ingress on its `*.ts.net` hostname.

## Services

A self-hosted stack running across the cluster, each behind Tailscale HTTPS:

*   **Media:** Jellyfin (reads media over NFS)
*   **Dev tools:** Forgejo (+ mirror), Opengist (git + SSH), Jupyter Notebook
*   **Productivity:** n8n workflow automation, Excalidraw, Drawio
*   **Knowledge:** FreshRSS, Linkwarden, SearXNG
*   **Security:** Vaultwarden, Adminer
*   **Observability:** Prometheus, Grafana, Prometheus PVE Exporter, Speedtest Tracker
*   **Platform:** PostgreSQL, CronMaster, Alpine IT-Tools

## Key Features

*   **High Availability:** ~19 guests managed by `ha-manager`, surviving node
    loss with automatic restart on a healthy node
*   **Mixed-architecture clustering:** x86 compute plus an ARM quorum witness,
    including version-skew management (PVE on x86 vs PxVirt on the Pi)
*   **Shared storage on NFS:** TrueNAS Scale NFS for container rootdisks and
    backups, tuned with 64 nfsd threads
*   **Zero-trust ingress:** every web service terminated with automatic HTTPS
    via Tailscale Serve --- no exposed public ports
*   **Operational depth:** NFS kernel-thread recovery, stale backup-lock
    clearing, HA service failover, and Magic SysRq node recovery

## Technology Stack

*   **Hypervisor:** Proxmox VE, PxVirt (ARM)
*   **Storage:** TrueNAS Scale, NFS, LVM-thin (`local-lvm`), btrfs snapshots
*   **Networking:** Tailscale (mesh VPN, Serve, HTTPS termination)
*   **Containers:** LXC / LXD, `pct`, `ha-manager`
*   **Automation:** Bash scripting, declarative dotfiles migrations

## Learning Outcomes

This cluster is a hands-on lab for systems and infrastructure engineering:

*   Distributed quorum and mixed-architecture cluster management
*   NFS-backed container storage --- its failure modes and recovery paths
*   High-availability resource management and failover under real outages
*   Network hardening with a zero-trust mesh VPN and per-service TLS
*   Backup/restore lifecycle and the operational reality of `vzdump` on NFS