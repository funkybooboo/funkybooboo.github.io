---
layout: post
title:  "Building Artisan Commerce: Queue-Based E-Commerce on the Edge"
date:   2026-02-23 12:00:00 -0700
categories: sveltekit cloudflare serverless ecommerce
---

E-commerce platforms assume infinite inventory. Click "Add to Cart," and the system expects the product to exist, ready to ship. But what about handmade goods? What about artisans who craft each item to order, where production capacity is finite and delivery times are real?

Traditional e-commerce breaks down for made-to-order businesses. Artisans either oversell and burn out, or they manually manage orders in spreadsheets. Customers get vague "2-4 weeks" estimates that breed uncertainty and support tickets.

There had to be a better way. Enter **Artisan Commerce** - an e-commerce platform built from the ground up for the realities of handmade production.

## The Core Problem: Capacity Management

The fundamental challenge is simple but profound: **handmade goods have finite production capacity**.

If an artisan can make 5 crochet blankets per week, and they receive 10 orders, traditional e-commerce has no way to communicate this reality. The customer sees "In Stock" and expects immediate shipment. The artisan sees a backlog and stress.

Artisan Commerce solves this with **queue-based capacity management**:

1. Artisans define production time per item (e.g., "crochet blanket takes 8 hours")
2. System tracks available production hours per week
3. When customers order, they see their **exact position in the queue** and **realistic delivery estimate**
4. As items complete, the queue automatically updates

Transparency replaces uncertainty. Customers know what to expect. Artisans maintain control.

## Why Serverless Edge?

Building this platform required making hard choices about architecture. The requirements were clear:

- **Low traffic initially** (<10 concurrent users, <10 orders/month)
- **Real business** (needs 99.9% uptime, not a toy)
- **Cost-sensitive** (budget-conscious startup)
- **Long-term maintainable** (solo developer, minimal ops overhead)

Traditional hosting (VPS, managed PostgreSQL) would cost $30-100+/month. Overkill for the scale, and expensive for a bootstrapped business.

The solution? **Cloudflare's serverless edge platform**.

### The Stack

- **Frontend:** SvelteKit (simpler than React, smaller bundles)
- **Backend:** Cloudflare Workers (serverless functions at the edge)
- **Database:** Cloudflare D1 (distributed SQLite)
- **Storage:** Cloudflare R2 (S3-compatible object storage)
- **Infrastructure:** Terraform (everything as code)

**Monthly cost: ~$1-5** (just the domain and transaction fees). Everything else runs on free tiers.

### Why This Works

Cloudflare's free tiers aren't toy limits - they're genuinely generous:

- **Workers:** 100k requests/day (we expect ~3k/month)
- **D1:** 5M reads/day, 100k writes/day (we expect ~100 reads/day, ~10 writes/day)
- **R2:** 10GB storage, 10GB egress/month (we expect ~100MB storage, ~1GB egress)

That's **100x headroom** on free tiers. Perfect for a low-traffic business that needs production-grade reliability.

## The Vendor Lock-In Problem

"But wait," you might say, "isn't Cloudflare vendor lock-in?"

Fair question. The answer: **comprehensive adapter patterns**.

Every external service in Artisan Commerce is wrapped in an adapter:

```typescript
// Database adapter
interface DatabaseAdapter {
  query(sql: string, params: any[]): Promise<any[]>
  execute(sql: string, params: any[]): Promise<void>
}

// Cloudflare D1 implementation
class D1Adapter implements DatabaseAdapter { ... }

// PostgreSQL implementation (for migration)
class PostgresAdapter implements DatabaseAdapter { ... }
```

Same pattern for storage (R2 → S3), email (Resend → SMTP), payments (Stripe → any processor).

**Migration paths are documented and tested.** If Cloudflare changes pricing or we outgrow the platform, we can migrate to PostgreSQL + traditional hosting in 1-2 days.

This isn't theoretical - the adapter pattern is implemented from day one, not bolted on later.

## SvelteKit: The Right Tool for the Job

React dominates the frontend landscape, but for this project, **SvelteKit was the clear choice**:

1. **Smaller bundles** (50-70% smaller than React) - critical for edge deployment
2. **Simpler mental model** - less "magic" than Next.js, easier to debug
3. **Better form handling** - progressive enhancement built-in
4. **Faster development** - less boilerplate, more productive

For a solo developer building a business, developer experience matters. SvelteKit delivers.

## Infrastructure as Code: Everything in Git

One of the core principles: **everything is version-controlled**.

The entire infrastructure is defined in Terraform:

```hcl
# Cloudflare Pages site
resource "cloudflare_pages_project" "artisan_commerce" {
  account_id        = var.cloudflare_account_id
  name              = "artisan-commerce"
  production_branch = "main"
}

# D1 database
resource "cloudflare_d1_database" "main" {
  account_id = var.cloudflare_account_id
  name       = "artisan-commerce-db"
}

# R2 bucket
resource "cloudflare_r2_bucket" "storage" {
  account_id = var.cloudflare_account_id
  name       = "artisan-commerce-storage"
}
```

Deployment is a single command: `terraform apply`

No clicking through dashboards. No manual configuration. Everything is reproducible, auditable, and documented.

## Test-Driven Development: 85%+ Coverage Target

Quality matters. Artisan Commerce follows strict TDD:

1. **Write failing test** (RED)
2. **Implement minimum code to pass** (GREEN)
3. **Refactor for quality**
4. **Repeat**

Target: **85%+ code coverage** with unit, integration, and E2E tests.

Testing framework:
- **Vitest** for unit/integration tests
- **Playwright** for E2E tests
- **GitHub Actions** for CI/CD

Every pull request must pass all tests. No exceptions.

## SLSA Level 3: Supply Chain Security

Security isn't an afterthought. Artisan Commerce implements **SLSA Level 3 provenance**:

- Cryptographically signed build artifacts
- Verifiable build process
- Tamper-proof supply chain

This is enterprise-grade security for a small business platform. Why? Because **security breaches destroy trust**, and trust is everything in e-commerce.

## The Road Ahead

Artisan Commerce is in active development. Current milestone: v0.2.0 (Core E-Commerce Features).

**Completed:**
- ✅ Architecture and technology decisions
- ✅ Infrastructure as code setup
- ✅ Comprehensive documentation (ADRs, specs)

**In Progress:**
- 🔄 Product catalog with queue integration
- 🔄 Shopping cart and checkout flow
- 🔄 Stripe payment integration
- 🔄 Order management dashboard

**Upcoming:**
- Queue-based capacity management UI
- Customer delivery estimate calculator
- Artisan production scheduling tools
- Pattern sales (digital products)

## Why This Matters

Artisan Commerce isn't just another e-commerce platform. It's purpose-built for a specific problem: **managing finite production capacity with transparency**.

The technology choices (serverless edge, IaC, adapter patterns) aren't trendy buzzwords - they're deliberate decisions to build a sustainable, maintainable, cost-effective platform that serves real businesses.

If you're an artisan tired of spreadsheets and vague delivery estimates, or a developer interested in modern serverless architecture, **check out the project on [GitHub](https://github.com/funkybooboo/artisan-commerce)**.

The code is open source (GPL-3.0). The architecture is documented. The vision is clear.

Let's build something better for makers and their customers.
