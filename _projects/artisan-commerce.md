---
layout: page
title: Artisan Commerce
permalink: /projects/artisan-commerce/
repo_url: https://github.com/funkybooboo/artisan-commerce
description: Serverless e-commerce platform with queue-based capacity management for made-to-order artisan goods.
---

**Repository:** [github.com/funkybooboo/artisan-commerce](https://github.com/funkybooboo/artisan-commerce)

Artisan Commerce is an open-source platform for artisan e-commerce with queue-based capacity management that brings transparency to handmade production. Unlike traditional e-commerce platforms, it manages finite production capacity through a queue-based system, giving customers realistic delivery estimates and artisans control over their workload.

## Key Features

*   **Queue-Based Capacity Management:** Revolutionary system that tracks finite production capacity and provides transparent delivery estimates for made-to-order goods
*   **Serverless Edge Architecture:** Built on Cloudflare Workers for global performance with <$5/month operational costs
*   **Zero Vendor Lock-In:** Comprehensive adapter pattern architecture with migration paths to PostgreSQL, AWS S3, and traditional hosting
*   **Infrastructure as Code:** Complete Terraform deployment achieving 99.9% uptime SLA
*   **SLSA Level 3 Security:** Supply chain security with 12-Factor App compliance

## Technology Stack

*   **Frontend:** SvelteKit with TypeScript, deployed to Cloudflare Pages
*   **Backend:** Hono on Cloudflare Workers (serverless functions at the edge)
*   **Database:** Drizzle ORM + Cloudflare D1 (distributed SQLite)
*   **Storage:** Cloudflare R2 (S3-compatible object storage)
*   **Infrastructure:** Terraform with comprehensive IaC
*   **Testing:** TDD with Vitest + Playwright targeting 85%+ coverage

## Challenges & Solutions

The core challenge was designing a queue-based capacity management system that could handle the complexities of made-to-order production while maintaining a simple user experience. The solution involved:

*   **Problem:** Traditional e-commerce platforms assume infinite inventory, but handmade goods have finite production capacity
*   **Solution:** Implemented a queue system that tracks production time per item, artisan availability, and provides realistic delivery estimates. The system automatically manages order queues and notifies customers of their position and estimated completion date.

Another significant challenge was achieving extreme cost efficiency while maintaining production-grade reliability:

*   **Problem:** Most e-commerce platforms cost $30-100+/month for hosting alone
*   **Solution:** Leveraged Cloudflare's serverless edge platform with D1 database and R2 storage, utilizing free tiers that cover 100x expected traffic. Designed comprehensive adapter patterns to prevent vendor lock-in, ensuring the platform can migrate to traditional infrastructure if needed.

## Architecture Highlights

The platform follows modern cloud-native principles:

- **Edge-First:** Runs globally on Cloudflare's network (200+ locations) for low latency
- **Cost-Optimized:** Free tiers cover expected traffic, with paid tiers remaining cheap at scale
- **Portable:** Everything defined in Terraform + Git, fully exportable
- **Secure:** SLSA Level 3 provenance, automated security scanning, principle of least privilege

Monthly cost: ~$1-5 (domain + transaction fees) - everything else runs on free tiers.
