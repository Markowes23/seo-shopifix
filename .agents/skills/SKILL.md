---
name: shopify-store-orchestrator
description: End-to-end Shopify dropshipping store orchestration for agents. Use when Codex needs to autonomously research a profitable niche, validate demand and competition, source niche-related best-selling products, create or configure a Shopify store, import products via Shopify Admin API or import manifests, write SEO-safe product pages, and optimize a Shopify theme for mobile-first conversion rate, Core Web Vitals, trust, accessibility, and affiliate-style purchase intent.
---

# Shopify Store Orchestrator

## Overview

Operate as the top-level workflow for launching or improving a niche Shopify dropshipping store. Coordinate niche research, product sourcing, SEO optimization, product import, collection setup, and theme conversion work without copying supplier descriptions.

Use the existing sibling skills when available:
- `product-sourcer` for DSers, AliExpress, and CJ Dropshipping product discovery and margin validation.
- `seo-optimizer` for human-written Shopify product copy, metadata, FAQs, and long-tail keyword targeting.

Read `references/shopify-automation-runbook.md` when you need Shopify Admin API payload details, import sequencing, theme optimization checks, or autonomous-operation boundaries.

## Inputs

Accept partial user input and infer reasonable defaults:

```json
{
  "niche": "optional string",
  "target_market": "United States",
  "budget": "optional number",
  "product_count": 8,
  "preferred_supplier": "DSers | CJ Dropshipping | Both",
  "store_positioning": "premium, problem-solving, mobile-first",
  "theme": "existing theme name or Shopify default",
  "credentials_available": true
}
```

If no niche is provided, research 5-7 candidate niches and select one using demand, margin, competition, shipping feasibility, content depth, and compliance risk.

## Workflow

### 1. Discover the Niche

Research current demand using search results, trend signals, marketplace signals, social intent, and competitor stores. Prefer niches with:
- Evergreen pain points plus recent trend lift.
- Products with at least 3x landed-cost markup potential.
- Low trademark, medical, safety, supplement, or regulated-product risk.
- Multiple product angles for collections, bundles, and internal links.
- Clear long-tail SEO opportunities with commercial intent.

Output a concise niche decision table before proceeding.

### 2. Source Products

Use `product-sourcer` logic to find 8-20 products mapped to DSers or CJ Dropshipping. For each product, verify:
- Supplier URL, SKU or product ID, cost, shipping, and delivery estimate.
- Total landed cost with contingency buffer.
- Retail price, gross margin, and markup multiplier.
- Unbranded image availability.
- No obvious trademark, counterfeit, copyright, or restricted claims.

Reject products below 3x markup unless the user explicitly accepts a lower-margin traffic or bundle strategy.

### 3. Build the Store Architecture

Create a store plan before import:
- Brand name, positioning, value proposition, and voice.
- Collections and navigation.
- Homepage section order.
- Product-page template strategy.
- Trust elements: shipping, returns, guarantees, payment icons, reviews, contact, and FAQ.
- SEO structure: handles, title tags, meta descriptions, collection copy, internal links, and blog topics.

### 4. Generate Shopify Product Payloads

Use `seo-optimizer` logic for each selected product. Produce Shopify-ready JSON with:
- `title`, `handle`, `body_html`, `vendor`, `product_type`, `tags`, `status`.
- `variants` with SKU, price, compare-at price when justified, inventory policy, and fulfillment service assumptions.
- `images` from permitted supplier or generated/owned assets only.
- SEO metafields or page title/description fields supported by the available Shopify tool/API.

Never paste supplier descriptions. Rewrite from user intent, benefits, objections, specs, and FAQs.

### 5. Create or Configure Shopify

If authenticated Shopify tools, Admin API credentials, or CLI access are available, create the store resources directly:
- Products, variants, collections, navigation, pages, policies, and metafields.
- Theme settings and section content.
- Redirects and SEO fields when supported.

If credentials are missing, produce import-ready JSON/CSV manifests and exact Shopify Admin steps. Do not claim resources were created unless the API/tool confirms success.

### 6. Optimize the Theme

Prioritize mobile-first conversion and Core Web Vitals:
- Hero with niche-specific value proposition and primary CTA.
- Product cards with clear price, benefit, trust marker, and quick path to product page.
- Product pages with sticky CTA, benefit bullets, reviews/social proof area, FAQ, shipping/returns, and comparison or use-case section.
- Collection pages with short SEO intro, filters, scannable cards, and internal links.
- Minimal JavaScript, optimized images, lazy loading, semantic HTML, accessible labels, and stable layout dimensions.

Avoid generic AI-looking sections, bloated animations, oversized decorative cards, and one-note color palettes.

### 7. Verify and Report

Before final output, verify what changed:
- Confirm API responses or generated file paths.
- Check product count, collection count, theme files/settings touched, and any failed imports.
- Run available lint/build/theme checks when a local theme repo exists.
- Report remaining manual steps, especially payment, domain, app billing, and supplier fulfillment setup.

## Autonomous Boundaries

Proceed autonomously for research, manifests, product copy, theme code, non-billing configuration, and draft/import-ready artifacts.

Pause for explicit user approval before:
- Purchasing domains, apps, paid themes, products, or subscriptions.
- Publishing a live theme over an existing production theme.
- Changing payment, tax, legal, or bank settings.
- Making medical, safety, financial, or guaranteed-results claims.
- Importing products that appear trademarked, counterfeit, restricted, or compliance-sensitive.

## Output Contract

When completing a full run, return:

```json
{
  "niche": {},
  "store_strategy": {},
  "products": [],
  "collections": [],
  "theme_optimizations": [],
  "seo_plan": {},
  "shopify_actions_completed": [],
  "files_created": [],
  "manual_steps_remaining": []
}
```

Keep the final user-facing summary brief, but preserve detailed manifests in files or structured JSON when the task creates store assets.
