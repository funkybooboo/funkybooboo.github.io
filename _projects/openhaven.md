---
layout: page
title: OpenHaven
permalink: /projects/openhaven/
repo_url: https://github.com/funkybooboo/openhaven
description: Multi-cloud personal infrastructure orchestrator that makes self-hosting as simple as using SaaS.
---

**Repository:** [github.com/funkybooboo/openhaven](https://github.com/funkybooboo/openhaven)

OpenHaven is a convention-driven cloud orchestrator that makes self-hosting as simple as using SaaS. Choose your domain, connect your cloud accounts, and deploy a complete personal cloud with email, file storage, password management, git hosting, and AI - all running on infrastructure you own and control.

## Key Features

*   **Multi-Cloud Cost Optimization:** Automatically uses the cheapest provider for each service, achieving 75-85% cost savings vs SaaS ($5-10/month vs $40-65/month)
*   **Convention Over Configuration:** Opinionated defaults like Ruby on Rails for cloud infrastructure - nothing is locked, customize anything
*   **True Sovereignty:** You own the cloud accounts, data, and billing. OpenHaven is just a convenience layer you can remove anytime
*   **Zero Vendor Lock-In:** Everything is open source, all infrastructure exportable as Terraform
*   **Comprehensive Service Stack:** Email (Mailcow), Files (Nextcloud), Passwords (Vaultwarden), Git (Gitea), VPN (WireGuard), AI (Ollama), and more

## Technology Stack

*   **Infrastructure:** Terraform (cloud provisioning), Docker Compose (orchestration)
*   **Reverse Proxy:** Traefik with automatic SSL (Let's Encrypt)
*   **Identity/SSO:** Keycloak (OAuth/OIDC)
*   **Compute:** Hetzner Cloud (cost-optimized VMs)
*   **Storage:** Backblaze B2 (S3-compatible, cheapest)
*   **DNS:** Cloudflare (free tier, automated)
*   **Database:** PostgreSQL (industry standard)

## Architecture Philosophy

OpenHaven is built on three core principles:

1. **User-Owned Infrastructure:** Users own the cloud accounts, not OpenHaven. Grant limited IAM permissions, revoke anytime. If OpenHaven disappears, infrastructure continues running.

2. **Infrastructure as Code:** Everything generated as Terraform, Docker Compose, and YAML configs. All code is human-readable, version-controlled, exportable, modifiable, and forkable.

3. **Multi-Cloud by Design:** Uses the best provider for each service rather than locking to a single VPS. Object storage from Backblaze B2, compute from Hetzner, DNS from Cloudflare - more cost-effective and resilient.

## Cost Comparison

| Service | SaaS Approach | OpenHaven |
|---------|---------------|-----------|
| Email + Calendar | $5-10/month | Included |
| File Storage (100GB) | $2-5/month | ~$0.50/month |
| Password Manager | $1-3/month | Included |
| Git Hosting | $4-7/month | Included |
| VPN | $5-10/month | Included |
| AI Chat | $20/month | Included |
| Office Suite | $7-10/month | Included |
| **Total** | **$44-65/month** | **$5-10/month** |

**Savings: $400-600/year** - plus you own everything with no vendor lock-in or data mining.

## Challenges & Solutions

The primary challenge was designing a system that balances simplicity with flexibility while maintaining true user sovereignty:

*   **Problem:** Most self-hosting solutions either require deep DevOps expertise or lock you into proprietary platforms
*   **Solution:** Created convention-driven approach with opinionated defaults (like Rails) that "just works" while keeping everything transparent and customizable. All infrastructure is generated as readable Terraform/Docker Compose that users can inspect, modify, or take over.

Another key challenge was achieving extreme cost efficiency across multiple services:

*   **Problem:** Running all these services traditionally costs $40-100+/month
*   **Solution:** Designed multi-cloud architecture that uses the cheapest provider for each service layer. Compute on Hetzner ($5-10/month), storage on Backblaze B2 ($0.50/month for 100GB), DNS on Cloudflare (free). This separation of concerns is both more cost-effective and more resilient than single-provider solutions.

## Service Stack

OpenHaven deploys a comprehensive suite of best-in-class open source services:

- **Keycloak** - Enterprise-grade OAuth/OIDC SSO
- **Nextcloud** - Files, calendar, contacts, notes with S3 backend
- **Mailcow** - Complete mail server (Postfix, Dovecot, Rspamd, SOGo)
- **Vaultwarden** - Bitwarden-compatible password manager
- **Gitea** - Lightweight Git hosting with CI/CD
- **OnlyOffice** - Microsoft Office-compatible document editing
- **WireGuard** - Modern VPN with QR code setup
- **Ollama + Open WebUI** - Self-hosted AI chat (privacy-first)
- **Traefik** - Automatic SSL and reverse proxy

## Current Status

OpenHaven is in early development (v0.1.0 - Documentation Phase). Currently establishing vision, architecture, and roadmap with comprehensive Architecture Decision Records (ADRs) and technical specifications.

**Roadmap:**
- v0.2.0: Minimal control plane (Keycloak, Vaultwarden, Gitea)
- v0.3.0: File storage & productivity (Nextcloud, OnlyOffice, WireGuard)
- v0.4.0: Email & communication (Mailcow)
- v0.5.0: AI & developer tools (Ollama, Open WebUI)
- v1.0.0: Production-ready with comprehensive monitoring

The vision: Make OpenHaven the "Rails of personal cloud infrastructure" - the obvious choice for anyone who wants to self-host with SaaS-level convenience.
