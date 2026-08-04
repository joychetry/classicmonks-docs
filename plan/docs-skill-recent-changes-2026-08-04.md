---
title: "Docs Skill: Recent Changes (Aug 4, 2026)"
type: session-notes
project: classic-monks
created: 2026-08-04
tags: [classic-monks, docs, skill, seo, keyword-research]
---

# Docs Skill — Recent Changes (Aug 4, 2026)

Record of the recent changes to the **classic-monks-docs** skill so the current docs rewrite session (and any future session) knows what changed. The `classic-monks-docs` skill is loaded fresh from disk (`~/.hermes/skills/content-creation/classic-monks-docs/SKILL.md`) each session, so reload it to pick up these changes.

## What changed in the skill

### 1. New body section: "Using SEO skills while writing content"
Added to `SKILL.md` (before the style guide). Three parts:

- **Which SEO skill to load, and when** — a routing table mapping task → skill: `seo` umbrella (always), `seo` → Content Briefs (primary keyword + related questions), `seo` → Semantic Topic Clustering (pillar/hub-and-spoke), `seo` → SXO (page-type mismatch), `ai-seo` (AI citation/AEO), `seo-audit` (on-page audit), `seo-geo-blog` (long-form), `schema-markup` (JSON-LD).
- **The write-time workflow** — load `seo` → run keyword research → shape H1/SEO title/meta/slug to the highest-volume query family → write → run pre-publish checks.
- **Keyword research (mandatory before drafting a new doc)** — 6-step method: identify primary query, expand into the query family (`web_search` primary + 2-3 long-tail variants, skim SERP/PAA), classify intent, pick the winner, lock the fields, and use cluster method for pillar-level planning.

### 2. Cross-link in `references/seo-checklist.md`
Added a note at the top of the "Pre-write research" section pointing back to the new SKILL.md body section, clarifying the division of labor (reference = field-level checklist; skill body = skill-selection + workflow).

### 3. SEO correctness fixes (from the upstream `seo` skill sync)
- **FAQPage rich results retired May 7, 2026** — no longer a Google SERP feature. Do not add FAQPage schema for a rich-result benefit; keep FAQ content for users/AI. Use `QAPage` for genuine user Q&A.
- **HowTo schema deprecated** (Sept 2023) — no featured snippet. Use `TechArticle` for how-to content instead.
- **Core Web Vitals use INP, never FID** (INP replaced FID March 2024).
- These facts were applied to `schema-markup`, the CM docs `seo-checklist.md` schema hints, and the `seo` umbrella hard rules.

## Why this matters for the rewrite session

- When rewriting a doc (login-customization, Admin Menu Manager, Toolbar, etc.), **run real keyword research first** using the `seo` skill — target the highest-volume query family, not the feature name alone. This is Joy's explicit expectation (see `references/seo-checklist.md`).
- The schema hints in the docs should use `Article`/`TechArticle`/`BreadcrumbList`/`SoftwareApplication` — **not** `FAQPage`/`HowTo`.
- The `seo` skill now has the SXO, content-brief, and cluster methodology absorbed into it, plus 12 reference files under `~/.hermes/skills/seo/references/`.

## Files touched

- `~/.hermes/skills/content-creation/classic-monks-docs/SKILL.md` (new section)
- `~/.hermes/skills/content-creation/classic-monks-docs/references/seo-checklist.md` (cross-link + schema facts)
- `~/.hermes/skills/marketing/schema-markup/SKILL.md` (FAQPage/HowTo facts)
- `~/.hermes/skills/seo/SKILL.md` (correctness fixes + SXO/content-brief/cluster methodology + 12 reference files)