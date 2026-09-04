# Classic Monks — Docs CPT Source

Feature documentation for the Classic Monks WordPress plugin (the Docs custom post type). Per-tab guides live in the subfolders (`ai/`, `bricks/`, `core/`, `email/`, `interface/`, `options/`, `performance/`, `security/`, `white-label/`, `woocommerce/`); standalone guides (`code-manager.md`, `short-links-tracking.md`) sit at this root. Screenshots live in `images/`.

Part of the publish tree: see [`../README.md`](../README.md) for the full structure (comparisons, blog, use-cases) and the 2026-09-04 rename mapping (`docs/` → `publish/`, `general/` → `docs/`).

## Writing a new article

1. Copy the article template (see `../README.md` § Writing a New Article).
2. Save in the appropriate tab folder with flat slug frontmatter (`advanced-plugin-manager`, not `core/advanced-plugin-manager`).
3. Images go in `images/<tab>/<feature>/` and are referenced relatively (`../images/<tab>/…` from tab files, `images/<tab>/…` from root files).
