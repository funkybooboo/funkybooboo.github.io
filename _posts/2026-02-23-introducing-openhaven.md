---
layout: post
title:  "Introducing OpenHaven: Your Personal Cloud, Your Rules"
date:   2026-02-23 14:00:00 -0700
categories: selfhosting cloud infrastructure devops
---

You pay $10/month for email. Another $5 for file storage. $3 for a password manager. $7 for git hosting. $10 for a VPN. $20 for AI chat. Before you know it, you're spending $50-70/month on basic digital services - and you don't own any of it.

What if you could run all of these services yourself, on infrastructure you control, for **$5-10/month**? What if deployment was as simple as signing up for Gmail, but you kept complete sovereignty over your data?

That's the vision behind **OpenHaven** - a convention-driven cloud orchestrator that makes self-hosting as simple as using SaaS.

## The Problem with SaaS

Don't get me wrong - SaaS is convenient. But it comes with costs beyond the monthly subscription:

1. **Vendor Lock-In:** Your data is trapped in proprietary formats
2. **Privacy Concerns:** Companies mine your data for profit
3. **Mounting Costs:** $5 here, $10 there - it adds up fast
4. **Loss of Control:** Features change, prices increase, services shut down
5. **Data Silos:** Your information scattered across dozens of platforms

Self-hosting solves these problems. But traditional self-hosting has its own issues:

- **Complexity:** Manually configuring dozens of services
- **Maintenance:** Security updates, backups, monitoring
- **Cost:** Expensive VPS or dedicated hardware
- **Expertise:** Requires deep DevOps knowledge

**OpenHaven bridges this gap.** Convention-driven simplicity meets complete control.

## The OpenHaven Approach

OpenHaven is built on three core principles:

### 1. User-Owned Infrastructure

**You own the cloud accounts, not OpenHaven.**

- Create AWS, GCP, or Hetzner accounts yourself
- Grant OpenHaven limited IAM permissions
- OpenHaven provisions infrastructure in your accounts
- You control billing and can revoke access anytime
- If OpenHaven disappears, your infrastructure keeps running

This is fundamentally different from traditional SaaS. You're not a tenant - you're the owner.

### 2. Convention Over Configuration

Like Ruby on Rails for cloud infrastructure:

- **Opinionated defaults** automatically select the lowest-cost providers
- **Best-in-class open source** software for each service
- **Zero config to start** - just choose your domain
- **Fully customizable** - override any default

Example: OpenHaven defaults to Hetzner Cloud for compute (cheapest), Backblaze B2 for storage (no egress fees), and Cloudflare for DNS (free). But you can swap any provider.

### 3. Zero Vendor Lock-In

Everything is open source and exportable:

- **Terraform** for all cloud resources
- **Docker Compose** for service orchestration
- **YAML configs** for service configuration

All generated code is human-readable, version-controlled, and forkable. You can inspect, modify, or take over manual management anytime.

## The Service Stack

OpenHaven deploys a comprehensive personal cloud:

| Service | Software | Purpose |
|---------|----------|---------|
| **Identity/SSO** | Keycloak | Single sign-on for all services |
| **Email** | Mailcow | Full mail server (SMTP, IMAP, webmail) |
| **Files** | Nextcloud | File storage, calendar, contacts, notes |
| **Passwords** | Vaultwarden | Bitwarden-compatible password manager |
| **Git** | Gitea | GitHub-like git hosting with CI/CD |
| **Office** | OnlyOffice | Microsoft Office-compatible editing |
| **VPN** | WireGuard | Modern VPN with QR code setup |
| **AI** | Ollama + Open WebUI | Self-hosted AI chat (privacy-first) |

All services integrate with Keycloak for centralized authentication. One login, access everything.

## Multi-Cloud Cost Optimization

Here's where OpenHaven gets interesting: **it doesn't lock you to a single VPS**.

Traditional self-hosting: Rent a $20-50/month VPS, run everything on it.

OpenHaven approach: Use the **cheapest provider for each service layer**:

- **Compute:** Hetzner Cloud CX21 ($5/month) - best price/performance
- **Storage:** Backblaze B2 ($0.50/month for 100GB) - cheapest S3-compatible
- **DNS:** Cloudflare (free) - excellent API, DDoS protection

**Total: $5-10/month** for a complete personal cloud.

Compare to SaaS equivalents:

| Service | SaaS Cost | OpenHaven |
|---------|-----------|-----------|
| Email + Calendar | $5-10/month | Included |
| File Storage (100GB) | $2-5/month | $0.50/month |
| Password Manager | $1-3/month | Included |
| Git Hosting | $4-7/month | Included |
| VPN | $5-10/month | Included |
| AI Chat | $20/month | Included |
| Office Suite | $7-10/month | Included |
| **Total** | **$44-65/month** | **$5-10/month** |

**Savings: $400-600/year** - and you own everything.

## Architecture: How It Works

OpenHaven consists of three layers:

### 1. Control Plane (Future)

The orchestration engine that:
- Provisions cloud resources via Terraform
- Deploys services via Docker Compose
- Generates configuration files
- Monitors health and status
- Manages updates

**Deployment options:**
- Hosted (SaaS) - OpenHaven-managed control plane
- Self-hosted - Run control plane yourself

### 2. Infrastructure Layer

Your cloud resources:
- **VM:** Hetzner Cloud (or DigitalOcean, GCP, AWS)
- **Storage:** Backblaze B2 (or AWS S3, Cloudflare R2)
- **DNS:** Cloudflare (automated records and SSL)

All provisioned via Terraform, fully exportable.

### 3. Service Stack

Docker Compose orchestration of:
- Traefik (reverse proxy with automatic SSL)
- Keycloak (SSO)
- Nextcloud (files)
- Mailcow (email)
- Vaultwarden (passwords)
- Gitea (git)
- OnlyOffice (office suite)
- WireGuard (VPN)
- Ollama + Open WebUI (AI)

All services configured to work together seamlessly.

## Current Status: v0.1.0 - Documentation Phase

OpenHaven is in early development. We're currently:

- ✅ Establishing vision and architecture
- ✅ Writing comprehensive documentation
- ✅ Creating Architecture Decision Records (ADRs)
- ✅ Defining technical specifications
- 🔄 Planning onboarding flow
- 🔄 Designing user experience

**Roadmap:**

- **v0.2.0:** Minimal control plane (Keycloak, Vaultwarden, Gitea)
- **v0.3.0:** File storage & productivity (Nextcloud, OnlyOffice, WireGuard)
- **v0.4.0:** Email & communication (Mailcow)
- **v0.5.0:** AI & developer tools (Ollama, Open WebUI)
- **v1.0.0:** Production-ready with comprehensive monitoring

## The Vision: Rails for Personal Cloud

OpenHaven aims to be the **Rails of personal cloud infrastructure** - the obvious choice for anyone who wants to self-host with SaaS-level convenience.

Just as Rails made web development accessible without sacrificing power, OpenHaven makes self-hosting accessible without sacrificing control.

**Convention over configuration.** Opinionated defaults that just work. Full transparency and customization when you need it.

## Why This Matters

Self-hosting shouldn't require a DevOps degree. Privacy shouldn't be a luxury. Data sovereignty shouldn't be complicated.

OpenHaven makes these things accessible:

- **For individuals:** Take control of your digital life
- **For families:** Secure, private services for everyone
- **For small teams:** Affordable collaboration tools
- **For developers:** Learn modern cloud architecture hands-on

## Get Involved

OpenHaven is open source (GPL-3.0) and needs contributors:

- **Developers:** Help build the control plane and service integrations
- **DevOps:** Improve Terraform modules and deployment automation
- **Writers:** Enhance documentation and guides
- **Testers:** Validate deployment on different cloud providers
- **Designers:** Create beautiful, intuitive interfaces

**Check out the project on [GitHub](https://github.com/funkybooboo/openhaven).**

Read the documentation. Review the Architecture Decision Records. Join the discussion.

Let's build the future of personal cloud infrastructure - together.

---

## Frequently Asked Questions

**Q: Is this production-ready?**  
A: Not yet. We're in v0.1.0 (documentation phase). Production-ready target is v1.0.0.

**Q: What if I don't want to manage infrastructure?**  
A: Future hosted control plane option will handle everything - you just connect your cloud accounts.

**Q: Can I migrate from existing services?**  
A: Yes. Migration guides will be provided for common services (Gmail → Mailcow, Dropbox → Nextcloud, etc.).

**Q: What about email deliverability?**  
A: Mailcow includes automated SPF/DKIM/DMARC setup. Deliverability takes time to build, but OpenHaven provides tools and documentation to help.

**Q: Is this really cheaper than SaaS?**  
A: Yes. Hetzner CX21 ($5/month) + Backblaze B2 ($0.50/month for 100GB) = $5.50/month. SaaS equivalents cost $40-65/month.

**Q: What about backups?**  
A: Automated encrypted backups to S3 using Restic. Daily incremental, weekly full, 30-day retention.

**Q: Can I use different cloud providers?**  
A: Absolutely. OpenHaven supports AWS, GCP, Azure, Hetzner, DigitalOcean, and more. Swap providers anytime.
