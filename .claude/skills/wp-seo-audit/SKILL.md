---
name: wp-seo-audit
description: Run a read-only SEO audit of a WordPress site through its MCP/Abilities connection and produce a prioritized punch list. Use when asked to audit, review, or find SEO issues/opportunities on a WordPress site you manage (single site or one site in a portfolio). Hosting- and SEO-plugin-agnostic: detects Rank Math/Yoast/none, Elementor, and available abilities first. Audit only — never writes changes.
---

# WordPress SEO Audit (read-only)

A repeatable, portfolio-friendly SEO audit you point at one WordPress site's MCP
server. It inventories the site through the Abilities/REST layer, runs a fixed
checklist of SEO checks, and returns a prioritized punch list. It does NOT modify
the site — fixes are a separate, explicitly-requested follow-up.

## Arguments

Parse these from the invocation (ask only if truly ambiguous):

- `SITE` — a label for the site being audited (e.g. `client-a`, `hellmann`). Used in the report header and the issues table.
- `MCP_SERVER` — the MCP server/connection for that specific site. If only one WordPress MCP server is connected, use it. If several are connected and `SITE` doesn't clearly map to one, ask which to target.
- `FOCUS` (optional) — narrow the scope, e.g. `blog-only`, `top-20-pages`, `metadata-only`. Default: full site.

If NO WordPress MCP server is connected, stop and tell the user: this skill
needs the site reachable over MCP (e.g. the `mcp-adapter` plugin + an auth
plugin such as Royal MCP / Vibe AI, or a managed-host MCP). Don't fabricate
findings.

## Hard rules

- **Read-only.** Only call list/get/read abilities. Never call create/update/delete/write abilities. If a check would require a write to verify, note it as "needs manual check" instead.
- **No guessing.** If an ability or data point isn't available on this site, mark the related check "not available" rather than inventing a result.
- **Per-site.** Audit exactly one site per run. To cover a portfolio, run once per site and keep the issues-table columns identical so results can be aggregated later.

## Phase 0 — Connect & detect

1. List the abilities the target MCP server exposes. Do not assume a fixed set.
2. Detect and record:
   - WordPress version.
   - SEO plugin in use: Rank Math, Yoast, both, or none. This determines how meta title / meta description / primary keyword / canonical are read.
   - Whether Elementor is active (affects content parsing and Core Web Vitals risk).
   - Object/page caching, XML sitemap URL, robots accessibility.
   - Post types present (posts, pages, and custom post types worth auditing).
3. Summarize what's available vs missing so the rest of the audit adapts. If no SEO plugin manages meta centrally, note that metadata lives in the theme/Elementor and metadata checks are best-effort.

## Phase 1 — Inventory

Paginate through all indexable content (respect `FOCUS`). For each URL capture:
title tag, meta description, slug, H1(s), word count, published date, modified
date, canonical, index/noindex, set primary keyword (if exposed), image count,
and alt-text count.

## Phase 2 — Audit checklist

Run every applicable check; skip (and label) ones the site can't support.

- **Metadata** — missing, duplicate, too-long (titles >60 chars, descriptions >160), or too-short title tags & meta descriptions.
- **Headings** — missing H1, multiple H1s, no H2 structure.
- **Thin content** — indexable pages under ~300 words.
- **Cannibalization** — multiple URLs targeting the same primary term.
- **Internal linking** — orphan pages (no inbound internal links) and high-value internal link opportunities.
- **Indexability** — important pages set to noindex; missing or incorrect canonicals.
- **Image SEO** — alt-text coverage gap.
- **Schema** — pages missing relevant structured data (Article / FAQ / Product / HowTo).
- **Content decay** — high-value pages not updated in 12+ months.
- **Technical** — sitemap present & valid, robots sanity, broken internal links, and Core Web Vitals risk on Elementor-built pages (flag the heaviest templates; Elementor bloat is the common CWV drag).

## Phase 3 — Prioritize

Score each issue by impact x effort and bucket it:

- **Quick wins** — metadata fixes, alt text, accidental noindex.
- **Medium** — internal linking, content refresh.
- **Structural** — cannibalization, architecture/URL issues.
- **Technical / CWV** — Elementor performance, caching, sitemaps.

## Phase 4 — Report

Output two things:

1. A short markdown summary: site label, detected stack (WP version, SEO plugin, Elementor y/n), top findings, and the prioritized punch list.
2. A flat issues table with identical columns every run, so portfolio results aggregate cleanly:

   `URL | issue | check | severity | bucket | recommended action`

## Fixes are a separate step

Do not apply fixes in this skill. If the user approves the punch list, treat the
fix run as its own task: staging copy + DB backup first, apply in reviewed
batches, verify, then promote. Surface that as the recommended next step.
