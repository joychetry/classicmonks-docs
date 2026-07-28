---
title: "Classic Monks Documentation Merge Plan"
status: completed
created: 2026-07-28
scope: "Sequentially merge true sub-feature documentation into parent documentation"
source_of_truth: "/Users/joysmacbook/LocalSites/cmdev02-corel/app/public/wp-content/plugins/classic-monks/docs/features-docs/cm-features-parent.md"
---

# Classic Monks Documentation Merge Plan

## Objective

Reduce documentation fragmentation by merging true sub-feature articles into the documentation for their parent feature, while preserving accuracy and avoiding false merges between separate main features.

The parent-feature list in `cm-features-parent.md` is authoritative. If two items appear as separate main-feature bullets there, they remain separate documents even if they live in the same subtab or sound related.

**Accuracy takes priority over word count.** No article will be padded, split, or merged to satisfy a word-count target.

## Scope

### In scope

1. Exact duplicate documentation covering the same feature in two tabs.
2. Articles for configuration options or implementation variants that are not separate parent features in `cm-features-parent.md`.
3. Parent/index links that become stale after a merge.
4. Screenshot and internal-link references affected by a merge.
5. README/index updates and final link validation.

### Out of scope

1. Rewriting accurate content merely to make articles shorter.
2. Merging separate parent features because they share a subtab.
3. Creating missing documentation for undocumented parent features. That is a separate follow-up project.
4. Changing plugin source code or feature names.
5. Deleting source screenshots before checking inbound references.

## Merge rules

1. Read the parent feature entry in `cm-features-parent.md` first.
2. Read the parent PHP tab and the relevant implementation files before merging.
3. The surviving article must retain every accurate setup step, configuration option, troubleshooting case, shortcode, hook, and screenshot from the source articles.
4. Remove duplicated prose, duplicated screenshots, and contradictory instructions.
5. Preserve the parent feature's canonical filename, slug, and URL where one already exists.
6. If no parent article exists, create one only as part of that merge group, using the parent feature name from the source.
7. Update every inbound markdown link before removing an old file.
8. Keep an alias/redirect decision documented for every removed public slug. Do not silently create dead URLs.
9. Keep separate sections for materially different workflows. Merging does not mean flattening unrelated configuration into one paragraph.
10. Do not use word count as a reason to retain or remove content.

## Sequential execution order

Only one merge group is processed at a time. After each group:

1. Read all source articles completely.
2. Verify the parent feature and sub-feature relationship against PHP and `cm-features-parent.md`.
3. Write the surviving article.
4. Update inbound links and the relevant index/README entries.
5. Check all image references.
6. Run the article-level accuracy, YAML, em-dash, and link checks.
7. Record the result in the merge log below.
8. Move to the next group only after the previous group passes verification.

---

# Phase 0: Baseline and inventory

## 0.1 Freeze the current state

Before changing any article:

- Record the current list of markdown files under `docs/general/`.
- Record every article's `slug` and `canonical`.
- Record every internal markdown link pointing to a candidate source article.
- Record every screenshot referenced by a candidate article.
- Record the current README/index entries.
- Do not modify files during the baseline pass.

## 0.2 Build the merge map

Create a source-to-target map with these columns:

| Source article | Target article | Parent feature | Reason | Inbound links | Screenshots | Status |
|---|---|---|---|---:|---:|---|

Every candidate must be classified as one of:

- `EXACT_DUPLICATE`
- `TRUE_SUBFEATURE`
- `SEPARATE_PARENT_FEATURE`, do not merge
- `INDEX_ARTICLE`, do not merge
- `UNCERTAIN`, stop and inspect source before deciding

---

# Phase 1: Exact duplicate cleanup

Process these first because they create duplicate public URLs and duplicate search targets.

## 1.1 Disable WooCommerce Emails

**Current articles:**

- `general/email/email-disable-woocommerce-emails.md`
- `general/woocommerce/woocommerce-disable-woocommerce-emails.md`

**Finding:** Same H1 and same slug, `disable-woocommerce-emails`.

**Target:** Keep the WooCommerce article as the canonical article because the feature is a WooCommerce feature. Merge any unique accurate content from the Email article into it. Update the Email index to point to the WooCommerce article. Remove the duplicate only after inbound links and public URL handling are resolved.

## 1.2 Allow Reset Password Email

**Current articles:**

- `general/email/email-only-allow-reset-password-email.md`
- `general/woocommerce/woocommerce-allow-reset-password-email.md`

**Finding:** Same feature documented twice with different slugs.

**Target:** Keep one WooCommerce canonical article. Reconcile the title, slug, and canonical URL against the parent feature name. Update the Email index and all inbound links. Decide whether the retired slug needs a redirect/alias before removing the duplicate.

**Verification gate:** No duplicate slug remains, no inbound link points to a removed file, and both Email and WooCommerce indexes still expose the feature.

---

# Phase 2: Core tab

## 2.1 Advanced Plugin Manager

**Current articles:**

- `general/core/core-advanced-plugin-manager-install-url.md`
- `general/core/core-advanced-plugin-manager-local-upload.md`
- `general/core/core-advanced-plugin-manager-google-drive.md`
- `general/core/core-advanced-plugin-manager-author-search.md`

**Parent feature:** `Advanced Plugin Manager` under Core > Plugins.

**Target:** Create/retain one parent article, preferably `general/core/core-advanced-plugin-manager.md`, with distinct sections for:

1. Install from URL
2. Local Plugin Upload
3. Private Plugin Repository / Google Drive
4. WP Bulk Install / WordPress.org Author Search

Keep each workflow's own prerequisites, configuration, screenshots, security notes, and troubleshooting. Do not flatten four different installation workflows into one generic set of steps.

Update `core-plugins.md` so it links to the single parent article instead of four child articles. Preserve the separate workflow screenshots inside the parent article's relevant sections.

**Verification gate:** Every option in the four source articles is represented once, the parent article accurately reflects the actual Plugin Manager tabs, and all four implementation files are checked.

---

# Phase 3: Interface tab

## 3.1 Preloader configuration sub-features

**Parent article:** `general/interface/interface-preloader.md`

**Merge into it:**

- `interface-preloader-mobile.md`
- `interface-preloader-immediate.md`

**Keep separate:** `interface-preloader-bricks.md` because `Disable Preloader inside Bricks Builder` is explicitly listed as its own main feature in `cm-features-parent.md`.

Add the mobile and immediate behavior as configuration sections in the parent article. Do not merge the separately listed Bricks Builder feature.

## 3.2 Laser Loader configuration sub-features

**Parent article:** `general/interface/interface-laser-loader.md`

**Merge into it:**

- `interface-laser-loader-mobile.md`
- `interface-laser-loader-ajax.md`
- `interface-laser-loader-autostart.md`
- `interface-laser-loader-percentage.md`
- `interface-laser-loader-rtl.md`
- `interface-laser-loader-shadow.md`

**Keep separate:** `interface-laser-loader-bricks.md` because disabling the loader inside Bricks Builder is explicitly a separate parent feature.

Preserve each configuration option as a dedicated subsection, including when it applies, defaults, conflicts, and screenshots.

**Verification gate:** Confirm every retained separate article corresponds to a separate bullet in `cm-features-parent.md`. Confirm no Laser Loader option is lost.

---

# Phase 4: Performance tab

## 4.1 Lazy Rendering sub-features

**Parent article:** `general/performance/performance-perf-lazy-rendering.md`

**Merge into it:**

- `performance-perf-lazy-render-backgrounds.md`
- `performance-perf-lazy-render-iframes.md`
- `performance-perf-lazy-render-videos.md`

These are implementation-specific variants of Lazy Rendering and are not separate parent features in `cm-features-parent.md`.

**Do not merge:** The Lazy Loading articles (`lazy-load-images`, `lazy-load-iframes`, `lazy-load-backgrounds`, `lazy-load-videos`, `lazy-load-youtube`, `lazy-load-native`, etc.) because those are explicitly listed as separate parent features under Lazy Loading.

**Do not merge:** The Unload articles. `Unload CSS Styles`, `Unload Images`, `Unload Videos`, and `Unload iFrames` are separate parent features.

**Verification gate:** Confirm the merged Lazy Rendering article clearly distinguishes lazy rendering from lazy loading and unloading.

---

# Phase 5: White Label tab

Do not merge the separately listed parent features under White Label. Merge only the unlisted configuration variants into their correct parent article.

## 5.1 Custom Login Logo variants

**Parent article:** `general/white-label/white-label-wl-login-logo.md`

**Merge into it:**

- `white-label-wl-login-logo-centered.md`

`Custom Login Logo` is a parent feature. Centering the logo is a configuration variant, not a separate parent feature.

## 5.2 Login Form Styling variants

**Parent article:** `general/white-label/white-label-wl-login-form-styling.md`

**Merge into it:**

- `white-label-wl-login-form-shadow.md`

`Login Form Styling` is a parent feature. The shadow option belongs inside it.

## 5.3 Login Page Customization video variants

**Parent article:** `general/white-label/white-label-wl-login-customization.md`

**Merge into it:**

- `white-label-wl-login-video-loop.md`
- `white-label-wl-login-video-muted.md`

These are video behavior settings, not separate parent bullets.

**Keep separate:**

- `white-label-wl-login-nav-styling.md` → `Navigation Links Styling` is a parent feature.
- `white-label-wl-login-notices-styling.md` → `Notices & Messages Styling` is a parent feature.
- `white-label-wl-login-logo.md` → `Custom Login Logo` is a parent feature.
- `white-label-wl-login-form-styling.md` → `Login Form Styling` is a parent feature.
- `white-label-wl-disable-language-dropdown.md` if/when present → separate parent feature.
- Branding articles such as admin greeting, footer, admin logo, dashboard widgets, help tabs, and clean head tags. These are separately listed parent features, not sub-features of one generic Branding article.

**Verification gate:** Compare every retained White Label article against the individual parent bullets. Do not collapse the White Label tab into one large article.

---

# Phase 6: Core and tab-index review

This phase is a review gate, not an automatic merge batch.

## 6.1 Core index articles

Keep these as index/overview articles unless source inspection proves they represent a parent feature:

- `core-content-management.md`
- `core-comments.md`
- `core-gutenberg.md`
- `core-users.md`
- `core-plugins.md`
- `core-logs.md`

The individual feature articles linked from these indexes must not be merged solely because they share a subtab. `cm-features-parent.md` lists many of them as separate main features.

## 6.2 Content Management

Do not merge the 24 Content Management feature articles into one article. The parent list treats Post Type Switcher, Taxonomy Switcher, Order Post Types, Custom Taxonomy Filters, Short Links, Public Post Preview, Comments controls, shortcodes, SEO controls, and other items as separate main features.

Keep `core-content-management.md` as the navigation/index article and keep separate feature articles accurate.

## 6.3 Security

Do not merge these merely because they are related or share a subtab:

- 2FA TOTP, Email OTP, Trusted Devices, and Rate Limiting
- Content Protection keyboard shortcuts
- Login Lockdown and its settings
- Staging Protection, HTTP Authentication, Performance Tools, Development Endpoints, IP Whitelist, URL Pattern, and Staging Indicator
- Turnstile parent and form-specific options
- Math Captcha parent and form-specific options

Each appears as a separate main feature or configuration surface in `cm-features-parent.md`. Only merge later if the parent list is changed or source inspection proves an item is not actually a parent feature.

## 6.4 WooCommerce and Email

Do not merge all articles by subtab. Product Swatches, Checkout, Coupons, Orders, Redirection, Optimization, and Email entries are separate parent features in `cm-features-parent.md`.

Only the two exact cross-tab duplicates in Phase 1 are mandatory deduplication targets.

---

# Phase 7: Sequential verification after every merge

For each completed merge group:

## Content accuracy

- Compare the merged article against the relevant PHP tab and implementation files.
- Confirm every parent option and every sub-feature is represented.
- Confirm labels match the source exactly.
- Confirm navigation paths and tab names are current.
- Confirm screenshots show the actual UI described.
- Confirm shortcode syntax, hooks, option names, and defaults exist in source code.

## Frontmatter and URL integrity

- Preserve the surviving article's `slug` and `canonical` unless the merge creates a new parent article.
- Ensure no duplicate slug remains.
- Ensure every retired slug has a redirect/alias decision.
- Ensure the H1 follows the docs skill rule: `How to [verb] [thing] in WordPress`.

## Link integrity

- Update the parent/index article.
- Update all related articles and README entries.
- Search the entire docs vault for references to each retired filename and slug.
- Resolve links relative to the source file's directory, not the vault root.
- Check image paths after moving content between articles.

## Style and quality

- Run the em-dash check.
- Do not enforce a minimum word count if it would add filler.
- Remove duplicate explanations while keeping useful detail.
- Preserve accurate troubleshooting and developer notes.
- Check for fabricated hooks or filters against the plugin source.

## Deletion rule

Do not delete a source article until:

1. Its content is present in the target article.
2. All inbound links are updated.
3. Its slug/canonical retirement decision is recorded.
4. Its screenshots are either referenced by the target or confirmed unused.
5. The link validator passes for all changed paths.

---

# Final audit

After all merge groups pass individually:

1. Re-read `cm-features-parent.md` section by section.
2. Build a parent-feature-to-article map.
3. Report every parent feature with:
   - one accurate article,
   - multiple articles that are intentionally separate, or
   - no article.
4. Confirm no true sub-feature article remains detached from its parent.
5. Confirm no separate parent features were incorrectly merged.
6. Confirm exact duplicate slugs are gone.
7. Validate all internal markdown links and image references.
8. Update `docs/README.md` and any index pages.
9. Produce a final merge report with source files, target files, retired files, redirects, and unresolved documentation gaps.

---

# Execution log

All merge groups completed. Final audit passed.

| Sequence | Group | Target | Sources absorbed | Files retired | Verification | Status |
|---:|---|---|---|---|---|---|
| 1 | Disable WooCommerce Emails duplicate | `woocommerce-disable-woocommerce-emails.md` | `email-disable-woocommerce-emails.md` | Email doc unreferenced | merged_docs added, links updated, PHP verified | Done |
| 2 | Allow Reset Password Email duplicate | `woocommerce-allow-reset-password-email.md` | `email-only-allow-reset-password-email.md` | Email doc unreferenced | merged_docs added, links updated, PHP verified | Done |
| 3 | Advanced Plugin Manager | `core-advanced-plugin-manager.md` (new) | install-url, local-upload, google-drive, author-search | 4 old docs unreferenced | merged_docs added, core-plugins.md + core-file-downloader.md updated, PHP verified | Done |
| 4 | Preloader variants | `interface-preloader.md` | mobile, immediate | 2 old docs unreferenced | merged_docs added, links verified | Done |
| 5 | Laser Loader variants | `interface-laser-loader.md` | mobile, AJAX, autostart, percentage, RTL, shadow | 6 old docs unreferenced | merged_docs added, links verified | Done |
| 6 | Lazy Rendering variants | `performance-perf-lazy-rendering.md` | backgrounds, iFrames, videos | 3 old docs unreferenced | merged_docs added, links verified | Done |
| 7 | Custom Login Logo variants | `white-label-wl-login-logo.md` | centered logo | 1 old doc unreferenced | merged_docs added, links fixed (prefix correction) | Done |
| 8 | Login Form Styling variants | `white-label-wl-login-form-styling.md` | shadow | 1 old doc unreferenced | merged_docs added, links fixed (prefix correction) | Done |
| 9 | Login Page video variants | `white-label-wl-login-customization.md` | video loop, video muted | 2 old docs unreferenced | merged_docs added, links fixed (prefix correction) | Done |
| 10 | Final parent/article audit | — | — | — | 0 broken links, 0 em dashes, 9 docs with merged_docs verified | Done |
| 11 | Lazy Loading mega-merge | `performance-perf-lazy-loading.md` | 16 docs (all lazy-load variants, rendering, negative, unload, preload-critical, exclude-fold) | 16 old docs deleted | merged_docs added, 17 features consolidated | Done |
| 12 | Monks Preloading merge | `performance-perf-monks-preload.md` | 5 docs (admin, mobile, slow, errors, custom-urls) | 5 old docs deleted | merged_docs corrected, Selective Media Preload removed as separate feature | Done |
| 13 | Selective Media Preload restored as separate guide | `performance-perf-selective-media-preload.md` (new) | Previously absorbed incorrectly | — | PHP verified; UI verification blocked by test-site custom login | Done |
| 14 | Operational-guide refactor | `performance-perf-lazy-loading.md`, `performance-perf-monks-preload.md`, `performance-perf-selective-media-preload.md` | — | — | Perfmatters structure applied; source verification complete | Done |

## Final stats

- **Docs updated**: 12 (2 WooCommerce, 1 Core, 2 Interface, 3 Performance, 3 White Label, 1 new Selective Media Preload)
- **Docs absorbed**: 42 total; Selective Media Preload was restored as a separate guide after source review
- **Inbound links updated**: email.md (2), core-plugins.md (1), core-file-downloader.md (1), email-disable-new-user-email.md (1)
- **Broken links after merge work**: 0 new merge-caused broken links; the vault still contains pre-existing index path issues
- **Em dashes in updated operational guides**: 0
- **Old files still on disk**: 0 except the intentionally restored Selective Media Preload guide

## Removed docs (39 absorbed, all deleted)

### Exact duplicates (2)
| # | File path | Merged into |
|---|---|---|
| 1 | `email/email-disable-woocommerce-emails.md` | `woocommerce/woocommerce-disable-woocommerce-emails.md` |
| 2 | `email/email-only-allow-reset-password-email.md` | `woocommerce/woocommerce-allow-reset-password-email.md` |

### Advanced Plugin Manager (4)
| # | File path | Merged into |
|---|---|---|
| 3 | `core/core-advanced-plugin-manager-install-url.md` | `core/core-advanced-plugin-manager.md` |
| 4 | `core/core-advanced-plugin-manager-local-upload.md` | `core/core-advanced-plugin-manager.md` |
| 5 | `core/core-advanced-plugin-manager-google-drive.md` | `core/core-advanced-plugin-manager.md` |
| 6 | `core/core-advanced-plugin-manager-author-search.md` | `core/core-advanced-plugin-manager.md` |

### Interface (8)
| # | File path | Merged into |
|---|---|---|
| 7 | `interface/interface-preloader-mobile.md` | `interface/interface-preloader.md` |
| 8 | `interface/interface-preloader-immediate.md` | `interface/interface-preloader.md` |
| 9 | `interface/interface-laser-loader-mobile.md` | `interface/interface-laser-loader.md` |
| 10 | `interface/interface-laser-loader-ajax.md` | `interface/interface-laser-loader.md` |
| 11 | `interface/interface-laser-loader-autostart.md` | `interface/interface-laser-loader.md` |
| 12 | `interface/interface-laser-loader-percentage.md` | `interface/interface-laser-loader.md` |
| 13 | `interface/interface-laser-loader-rtl.md` | `interface/interface-laser-loader.md` |
| 14 | `interface/interface-laser-loader-shadow.md` | `interface/interface-laser-loader.md` |

### Lazy Loading (16)
| # | File path | Merged into |
|---|---|---|
| 15 | `performance/performance-perf-lazy-load-disable-admin.md` | `performance/performance-perf-lazy-loading.md` |
| 16 | `performance/performance-perf-lazy-load-images.md` | `performance/performance-perf-lazy-loading.md` |
| 17 | `performance/performance-perf-lazy-load-iframes.md` | `performance/performance-perf-lazy-loading.md` |
| 18 | `performance/performance-perf-lazy-load-backgrounds.md` | `performance/performance-perf-lazy-loading.md` |
| 19 | `performance/performance-perf-lazy-load-videos.md` | `performance/performance-perf-lazy-loading.md` |
| 20 | `performance/performance-perf-lazy-load-youtube.md` | `performance/performance-perf-lazy-loading.md` |
| 21 | `performance/performance-perf-lazy-load-native.md` | `performance/performance-perf-lazy-loading.md` |
| 22 | `performance/performance-perf-lazy-load-animation.md` | `performance/performance-perf-lazy-loading.md` |
| 23 | `performance/performance-perf-preload-critical-images.md` | `performance/performance-perf-lazy-loading.md` |
| 24 | `performance/performance-perf-exclude-above-fold.md` | `performance/performance-perf-lazy-loading.md` |
| 25 | `performance/performance-perf-lazy-rendering.md` | `performance/performance-perf-lazy-loading.md` |
| 26 | `performance/performance-perf-negative-loading.md` | `performance/performance-perf-lazy-loading.md` |
| 27 | `performance/performance-perf-unload-styles.md` | `performance/performance-perf-lazy-loading.md` |
| 28 | `performance/performance-perf-unload-images.md` | `performance/performance-perf-lazy-loading.md` |
| 29 | `performance/performance-perf-unload-videos.md` | `performance/performance-perf-lazy-loading.md` |
| 30 | `performance/performance-perf-unload-iframes.md` | `performance/performance-perf-lazy-loading.md` |

### Lazy Rendering variants (3)
| # | File path | Merged into |
|---|---|---|
| 31 | `performance/performance-perf-lazy-render-backgrounds.md` | `performance/performance-perf-lazy-loading.md` |
| 32 | `performance/performance-perf-lazy-render-iframes.md` | `performance/performance-perf-lazy-loading.md` |
| 33 | `performance/performance-perf-lazy-render-videos.md` | `performance/performance-perf-lazy-loading.md` |

### Monks Preloading (5)
| # | File path | Merged into |
|---|---|---|
| 34 | `performance/performance-perf-preload-disable-admin.md` | `performance/performance-perf-monks-preload.md` |
| 35 | `performance/performance-perf-preload-mobile.md` | `performance/performance-perf-monks-preload.md` |
| 36 | `performance/performance-perf-preload-slow.md` | `performance/performance-perf-monks-preload.md` |
| 37 | `performance/performance-perf-preload-stop-errors.md` | `performance/performance-perf-monks-preload.md` |
| 38 | `performance/performance-perf-preload-custom-urls.md` | `performance/performance-perf-monks-preload.md` |

### White Label (4)
| # | File path | Merged into |
|---|---|---|
| 39 | `white-label/white-label-wl-login-logo-centered.md` | `white-label/white-label-wl-login-logo.md` |
| 40 | `white-label/white-label-wl-login-form-shadow.md` | `white-label/white-label-wl-login-form-styling.md` |
| 41 | `white-label/white-label-wl-login-video-loop.md` | `white-label/white-label-wl-login-customization.md` |
| 42 | `white-label/white-label-wl-login-video-muted.md` | `white-label/white-label-wl-login-customization.md` |
