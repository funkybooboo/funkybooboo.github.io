---
layout: page
title: Homelab - Proxmox Virtualization Cluster
permalink: /projects/homelab/
description: A 5-node Proxmox VE cluster backed by TrueNAS Scale, running ~19 HA-managed LXC containers over a Tailscale mesh.
---

A self-hosted infrastructure platform I operate as a 5-node Proxmox VE cluster,
backed by TrueNAS Scale and fronted by a Tailscale mesh VPN. The cluster runs
around 19 LXC workloads under high-availability management.

## Architecture

*   **Compute:** 5-node Proxmox VE cluster --- four `x86_64` nodes
    (`pve-framework`, `pve-thermaltake`, `pve-aspires`, `pve-aspiree15`)
    plus a Raspberry Pi running **PxVirt** (the ARM port of Proxmox VE) as a
    quorum-only witness, giving a 5-vote majority across mixed x86/ARM hardware.
*   **Storage backend:** **TrueNAS Scale** (`tnas`) exporting NFS for shared
    container rootdisks and nightly `vzdump` backups, with per-node `local-lvm`
    for node-local storage.
*   **Workload model:** **LXC containers** for density, managed as **HA
    resources** via `ha-manager` so the cluster automatically restarts a failed
    guest on a surviving node.
*   **Networking:** **Tailscale** mesh VPN with `tailscale serve --bg --https
    443` giving each service automatic TLS-terminated HTTPS ingress on its
    `*.ts.net` hostname --- no exposed public ports.

## Operations

Real-world cluster work performed across the deployment:

*   NFS kernel-thread recovery and nfsd tuning
*   Stale backup-lock clearing following NFS outages
*   HA service failover and recovery via `ha-manager`
*   Version-skew management across mixed x86/ARM nodes (PVE vs PxVirt)

## Technology Stack

*   **Hypervisor:** Proxmox VE, PxVirt (ARM)
*   **Storage:** TrueNAS Scale, NFS, LVM-thin (`local-lvm`), btrfs snapshots
*   **Networking:** Tailscale (mesh VPN, Serve, HTTPS termination)
*   **Containers:** LXC, `pct`, `ha-manager`