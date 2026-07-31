---
title: "Classic Monks gaps roadmap against ASE"
date: 2026-07-30
type: comparison-roadmap
status: internal-prioritization
---

# Classic Monks gaps roadmap against ASE

This is a prioritization of current CM `No`, `Partial`, `Different approach`, and `Unknown` results from the ASE comparison matrix. It is **not an approved product roadmap** and contains no ship-date promise.

Priority reflects migration risk for freelancers and agencies:

- **P1:** A missing capability can block an agency from removing ASE or another critical plugin.
- **P2:** The core job exists, but important workflow, scope, provider, or Pro-depth differences remain.
- **P3:** Narrow utilities and low-frequency admin conveniences.

## P1: replacement blockers

| ASE module | Current CM status | CM feature or related surface | Gap to close | Why P1 |
|---|---|---|---|---|
| Custom Content Types | No | None confirmed | Register/edit CPTs, taxonomies, custom field groups, and options pages. | This is a foundational content-model dependency. It can also overlap with ACF-style workflows. |
| Form Builder | Different approach | Form Desk | Add a real form builder, or clearly position Form Desk as a submission manager only. | Agencies cannot migrate a form-building workflow to an entries dashboard. |
| Site Backup and Migration | Different approach | Export Settings, Import Settings | Full scheduled backup, restore, migration, sync, and recovery workflows. | Settings export does not protect a site or replace backup infrastructure. |
| File Manager | Different approach | Download File to WordPress, plugin/theme downloads, secure downloads | General file and folder operations, editing, permissions, compression, extraction, and safe mode. | File operations are a direct Pro dependency on some client sites. |
| Code Snippets Manager | Partial | Code Manager | Confirm or add HTML/SCSS, revisions, execution scope, and automatic PHP safe mode parity. | A code manager that cannot safely recover a fatal PHP snippet is not a drop-in replacement for every agency workflow. |
| Redirect Manager | Partial | Redirection & Logging, Global 404 Redirect | Full redirect rules with regex/wildcards, status codes, groups, notes, cache behavior, and loop detection. | Redirects are migration, SEO, and revenue-critical. |

## P2: important parity gaps

| ASE module or group | Current CM status | Main gap |
|---|---|---|
| Media Files Visibility Control | No | Add uploader and role-based Media Library visibility limits. |
| Media Categories | Different approach | Decide whether folders can cover the actual category and insertion-filter workflow, or document the boundary clearly. |
| AVIF Upload | Different approach | Distinguish AVIF conversion from direct AVIF MIME upload and document the supported workflow. |
| Public Preview for Drafts | Partial | Confirm scheduled previews, public post-type scope, and password behavior. |
| Admin Logo | Partial | Confirm admin-menu logo placement and site-icon/home-icon behavior beyond the documented admin-bar logo and custom menu icons. |
| Enhance List Tables | Partial | Confirm broader media, comment, user, and non-column list-table enhancements beyond CM’s Admin Columns Manager. |
| Various Admin UI Enhancements | Partial | Confirm media infinite scrolling, active-plugin ordering, taxonomy hierarchy, dashboard columns, and admin body-class controls. |
| Site Identity on Login Page | Partial | Confirm site icon replacement and destination URL behavior beyond CM’s documented custom login logo. |
| Custom Admin CSS and Custom Frontend CSS | Partial | Document exact Code Manager placement, role scope, conditions, and recovery behavior. |
| Insert <head>, <body> and <footer> Code | Unknown | Confirm whether Code Manager supports the required insertion points and HTML/meta/script/style injection. |
| Disable Comments | Partial | Confirm selected/excepted post-type scope beyond CM’s documented global disable behavior. |

| CAPTCHA Protection | Partial | Expand or document provider coverage beyond Turnstile and Math Captcha, especially ALTCHA and Google reCAPTCHA. |
| Two-Factor Authentication (2FA) | Partial | Confirm recovery codes, per-role settings, grace periods, and enrollment/recovery workflows. |
| Image Upload Control | Partial | Confirm JPEG/WebP quality, original-file handling, upload-context scope, and intermediate-size controls. |
| Multiple User Roles | Different approach | Confirm assigning multiple roles to one user, not only creating and managing roles. |

## P3: narrow utilities

| ASE module or group | Current CM status | Main gap |
|---|---|---|
| External Permalinks | No | Assign external URLs as post/page permalinks with scope controls. |
| Allow Custom Navigation Menu Items to Open in New Tab | No | Add target behavior to custom menu items. |
| Auto-Publish Posts with Missed Schedule | No | Publish missed scheduled posts when the site is visited. |
| Hide Admin Bar | No | Hide the frontend/backend admin bar by role and preserve administrator visibility rules. |
| Login ID Type | No | Restrict authentication to username or email. |
| Log In/Out Menu | No | Add dynamic login/logout menu items and labels. |
| Redirect After Login | No | Role-specific post-login redirects. |
| Disable User Account | No | Disable an individual user account without deleting it or its content. |
| Custom Body Class | Unknown | Confirm whether Code Manager supports a dedicated body-class control by singular post type. |
| Manage ads.txt and app-ads.txt | No | Edit and validate advertising files. |
| Manage robots.txt | No | Edit and validate robots.txt content. |
| Disable Feeds | Partial | CM lists Disable RSS Feeds and Remove RSS Feed Links, but Atom/RDF parity is not established. |
| Disable Embeds | Partial | CM lists Disable Embeds, but related JavaScript and external-embedding scope are not established. |
| Disable Author Archives | No | Return 404 and remove author-archive links/sitemap entries. |
| Disable Smaller Components | Partial | CM covers several bundled controls, but not every ASE component or ancillary behavior. |
| Obfuscate Author Slugs | Different approach | Replace public author slugs and author REST exposure, rather than only preventing username discovery. |
| Image Sizes Panel | No | Display all generated image sizes with direct URLs and copy controls. |
| Maintenance Mode | No | Provide a customizable maintenance page with administrator bypass. |
| Display System Summary | No | Provide the dashboard system summary widget and storage details. |

## Product decision rules

1. Do not call a P1 or P2 item “covered” because a nearby feature exists.
2. Keep the exact CM feature name in the comparison page and documentation.
3. If a gap is intentionally out of scope, say so publicly rather than implying parity.
4. Before building a new module, test whether the need is better served by a stable dedicated plugin, WordPress core, or a narrow CM enhancement.
5. Do not duplicate concerns already handled by the existing CM stack without checking hook conflicts and settings ownership.
6. Treat roadmap priority as a product decision input, not a promise to ASE users.
