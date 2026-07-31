---
title: "ASE vs Classic Monks: Overlap, Gaps, and When to Use Both | CM"
description: "A feature-by-feature comparison for freelancers and agencies deciding whether Classic Monks can replace Admin and Site Enhancements Free or Pro."
date: 2026-07-30
type: comparison
last_updated: 2026-07-30
---

# ASE vs Classic Monks: Overlap, Gaps, and When to Use Both

If you use Admin and Site Enhancements (ASE), the useful question is not “Which plugin has more features?” It is:

> Which ASE modules are actually enabled on this site, and does Classic Monks cover those exact jobs well enough to remove ASE?

The honest answer is mixed. Classic Monks covers a substantial part of ASE’s WordPress admin, security, performance, email, and workflow territory. It does not replace every ASE module. ASE Pro still has important modules that Classic Monks does not currently match, especially Custom Content Types, Form Builder, full Site Backup and Migration, File Manager, and several narrower admin utilities.

## Version and date note

This comparison was verified on **July 30, 2026** using the official ASE feature and pricing pages, the local Classic Monks feature library, the Classic Monks pricing page, the Classic Monks features page, and the Classic Monks changelog.

- **ASE:** The official feature page reports 76 modules, 58 free modules, 31 modules with Pro features, and 18 Pro modules.
- **ASE matrix method:** The 76 visible feature cards were counted and mapped using their individual tier badges. Those badges currently resolve to 28 Free, 31 Free with Pro features, and 17 Pro cards. The page summary and visible card labels therefore have a one-module discrepancy. The matrix uses the per-module badges, not the summary counter.
- **Classic Monks:** The live marketing page claims 393+ features. The local parent feature library uses a different inventory method and currently lists 448+ main feature bullets across 59 subtabs. These counts are not directly comparable.
- **CM count caveat:** The live feature page also exposes non-additive category figures and currently shows a conflicting Bricks promotional figure versus its category figure. Those numbers are not safe to sum into a unique module count, so this comparison uses the official 393+ headline only.
- **Latest Classic Monks changelog found:** v2.1.0, July 28, 2026.

## One-line positioning

**ASE** is a focused WordPress enhancement suite. It is especially strong when you need precise admin controls, content-type tools, code snippets, forms, redirects, backups, or narrowly scoped WordPress switches.

**Classic Monks** is a broader modular core stack. It covers many of those admin jobs, then adds deep Performance, WooCommerce, Bricks, AI, White Label, media, email, and setup tooling in the same plugin.

Neither product is a universal replacement for the other.

## Quick verdict

| Your situation | Recommendation |
|---|---|
| You use ASE Free mainly for Post Type Switcher, Gutenberg/comments controls, XML-RPC, revisions, Heartbeat, SVG, login URL, 2FA, or basic admin cleanup | Test Classic Monks on staging. You may be able to remove ASE. |
| You use ASE Pro Custom Content Types | Keep ASE or replace it with a dedicated CCT/fields product. CM does not currently match this module. |
| You use ASE Pro Form Builder | Keep ASE or your form plugin. CM Form Desk manages submissions, it does not build the forms. |
| You use ASE Pro Site Backup and Migration | Keep a real backup/migration system. CM settings export is not a site backup. |
| You use ASE Pro File Manager | Keep ASE if you need file operations inside WordPress. CM download tools are not a general file manager. |
| You use ASE for one narrow feature CM does not cover | Keep ASE. Do not remove a working tool to reduce a plugin count by one. |
| You want Bricks, WooCommerce, performance, AI, setup, or White Label features beyond ASE | CM adds a separate layer of value. ASE does not need to match those areas for CM to be useful. |
| You run both | Disable overlapping modules. One plugin should own each concern. |

## How this comparison was made

The full matrix is in [`matrix-full.csv`](matrix-full.csv). It includes every one of the 76 feature cards currently listed on the ASE page.

A CM match was accepted only when the feature name was present in the local Classic Monks parent feature library or was explicitly supported by the official changelog. Similar wording was not treated as proof of equivalence.

### Legend

- **Yes:** CM has a named feature covering the core ASE job. Check scope before removing ASE.
- **Partial:** CM covers the core idea, but an important scope, provider, role, workflow, or Pro-depth difference remains.
- **Different approach:** CM has related functionality, but it solves a different problem.
- **No:** No matching CM feature was found.
- **Unknown:** A related CM surface exists, but the supplied docs do not establish the required scope or behavior. It is not a guess or an implicit Yes.

## Section-by-section comparison

The tables below summarize the decision points. The CSV contains the complete 76-row mapping, including every module, tier, Pro extra, CM feature name, limitation, and verdict.

### Content Management

| ASE module                | Tier     | CM result                                   | Practical answer                                                                                                                       |
| ------------------------- | -------- | ------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Custom Content Types      | Pro      | No                                          | Not currently in Classic Monks core. A full-featured external Custom Content Types plugin is on the CM roadmap and is awaiting WordPress.org repository approval. It is not a current replacement. |
| Post Type Switcher        | Pro      | Yes: Post Type Switcher                     | Direct match.                                                                                                                          |
| Content Duplication       | Free+Pro | Yes: Enable Content Duplication             | Core duplication matches. Compare role, post-type, and placement controls before removing ASE Pro.                                     |
| Content Order             | Free+Pro | Yes: Order Post Types, Order Taxonomy Terms | CM documents post-type ordering, including attachments, frontend menu_order behavior, and hierarchical taxonomy ordering.              |
| Media Categories          | Pro      | Different approach: Enable Folder Manager   | Folders are not the same as media taxonomy categories.                                                                                 |
| Media Replacement         | Free+Pro | Yes: Enable Media Replacement               | CM preserves the attachment ID and existing URLs. ASE Pro’s grid-view control is an extra UI surface not separately stated in CM docs. |
| Public Preview for Drafts | Pro      | Yes: Public Post Preview                | CM covers secure unpublished-post previews with temporary URLs, expiration, and optional password protection. Scheduled-preview behavior remains a separate workflow to test if required. |
| SVG Upload                | Free     | Yes: SVG Support, SVG Security Sanitization | CM documents SVG upload support, previews, and sanitization. Role-specific upload scope is not separately stated.                      |
| AVIF Upload               | Free     | Different approach: Image Converter         | CM converts to AVIF. It is not confirmed as a standalone AVIF MIME-upload module.                                                      |
| External Permalinks       | Free+Pro | No                                          | Keep ASE if you assign external URLs as post or page permalinks.                                                                       |

**Content verdict:** CM can replace several ASE content utilities, but not ASE Pro’s Custom Content Types. That one module alone is enough to block a full ASE Pro replacement for many agencies.

### Admin Interface

| ASE module                | Tier     | CM result                                                    | Practical answer                                                                                                                                        |
| ------------------------- | -------- | ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Clean Up Admin Bar        | Free+Pro | Yes: Top Toolbar Manager                                     | CM documents rearranging, hiding, visibility control, and custom toolbar placement for admin-bar items.                                                 |
| Admin Bar Custom Elements | Pro      | Yes: Admin Menu Manager, Top Toolbar Manager                 | CM supports custom top-level and child toolbar items, custom sidebar menu/submenu items, icons, separators, spacers, capabilities, and role visibility. |
| Hide Admin Notices        | Free+Pro | Yes: Admin Notices Manager                                   | CM supports selective notice management, hide-all mode, and dismiss controls. Its workflow differs from ASE’s notices panel.                            |
| Disable Dashboard Widgets | Free     | Yes: Remove Dashboard Widgets                                | Direct match.                                                                                                                                           |
| Hide Admin Bar            | Free+Pro | No                                                           | Moving or managing the toolbar is not the same as hiding it by role and surface.                                                                        |
| Admin Logo                | Pro      | Yes: Replace WordPress Admin Bar Logo, Custom Login Logo | CM covers the admin-bar and login logo surfaces. ASE's admin-menu and home-icon branding extras are additional scope differences. |
| Admin Menu Organizer      | Free+Pro | Yes: Admin Menu Manager                                      | Strong match for hiding, renaming, reordering, and visibility control.                                                                                  |
| Admin Columns Manager     | Pro      | Yes: Admin Columns Manager                                   | CM documents post/page/CPT columns, custom fields, taxonomy columns, global search, frozen columns, and inline featured-image editing.                  |
| Enhance List Tables       | Free     | Partial: targeted CM column features                         | CM does not present one broad equivalent for every ASE list-table enhancement.                                                                          |
| Custom Admin Footer Text  | Free+Pro | Yes: Customize Admin Footer                                  | Direct match.                                                                                                                                           |

**Admin verdict:** CM is credible for admin cleanup and menu management. ASE remains useful for specialized list-table, admin-bar, and admin-surface behavior.

### Log In/Out and Register

| ASE module | Tier | CM result | Practical answer |
|---|---|---|---|
| Change Login URL | Free | Yes: Enable Custom Login URL | CM documents the custom slug, default wp-login.php redirection, URL whitelist support, and secure access through the custom URL. |
| Login ID Type | Free | No | No confirmed CM setting to restrict login to username or email. |
| Login Page Customizer | Pro | Yes: Login Page Customization plus the named login styling features | CM spreads the same surface across White Label modules. |
| Site Identity on Login Page | Free | Partial: Custom Login Logo | Logo replacement matches, but site-icon and destination-link behavior is not confirmed. |
| Log In/Out Menu | Free+Pro | No | Keep ASE if you use its dynamic login/logout menu item. |
| Last Login Column | Free+Pro | Yes: Show Last Login Column | CM documents the last-login date/time column. ASE Pro sortable behavior is an additional presentation option. |
| Registration Date Column | Free+Pro | Yes: Show Registration Date Column | Direct match. |
| Redirect After Login | Free+Pro | No | No confirmed role-specific CM equivalent. |
| Redirect After Logout | Free+Pro | Yes: Redirect after logout | Core redirect behavior is listed in CM. Verify scope on the target site. |
| Disable User Account | Free | No | No confirmed CM equivalent for disabling individual user login. |

**Login verdict:** CM covers the login URL, login design, 2FA, CAPTCHA, and lockout territory, but it does not cover every login workflow utility ASE offers.

### Custom Code

| ASE module                        | Tier | CM result             | Practical answer                                                                                                                                    |
| --------------------------------- | ---- | --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| Code Snippets Manager             | Pro  | Yes: Code Manager | CM Code Manager supports PHP, JavaScript, CSS, HTML/PHP Content, TXT files, conditional execution, syntax validation, safe mode, automatic fatal-error recovery, hook placement, and CodeMirror editing. ASE-specific UI and execution options are additional scope details. |
| Custom Admin CSS                  | Free | Yes: Code Manager | CM Code Manager supports CSS snippets with conditional loading and admin-side execution contexts. |
| Custom Frontend CSS               | Free | Yes: Code Manager | CM Code Manager supports CSS snippets with conditional loading and frontend execution contexts. |
| Insert head, body and footer Code | Free | Yes: Code Manager | CM supports HTML/PHP Content and hook placement at wp_head, wp_body_open, wp_footer, before_content, after_content, login_message, and login_footer. |
| Custom Body Class                 | Free | Unknown: Code Manager | A dedicated body-class control is still not confirmed. |
| Manage ads.txt and app-ads.txt    | Free | Yes: Code Manager | CM Code Manager supports virtual ads.txt and app-ads.txt file editing from the admin. |
| Manage robots.txt                 | Free | Yes: Code Manager | CM Code Manager supports virtual robots.txt file editing from the admin. |

**Code verdict:** CM Code Manager is the stronger core snippet workflow for many agencies. Compare ASE-specific editor or execution options only when the site depends on them.

### Disable Components

| ASE module                 | Tier     | CM result                                                                                                                                                              | Practical answer                                                                                                                                                                             |
| -------------------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Disable Gutenberg          | Free+Pro | Yes: Disable Gutenberg Editor                                                                                                                                          | Direct match.                                                                                                                                                                                |
| Disable Comments           | Free+Pro | Partial: Disable Comments                                                                                                                                              | CM lists global disabling. ASE supports more selective post-type scope, especially in Pro.                                                                                                   |
| Disable REST API           | Free+Pro | Yes: REST API Access, REST API Exclusions, Remove REST API Links                                                                                                       | CM documents admin-only, logged-in-only, and fully disabled access levels, namespace exclusions, and REST URL/link removal.                                                                  |
| Disable Feeds              | Free     | Yes: Disable RSS Feeds, Remove RSS Feed Links | CM disables RSS feeds and removes feed discovery links. Atom/RDF behavior should be tested only if the site depends on those formats. |
| Disable Embeds             | Free     | Yes: Disable Embeds | CM disables oEmbed scripts, generation, discovery, and endpoints. ASE's related JavaScript and external-embedding controls are additional scope details. |
| Disable All Updates        | Free     | Yes: Disable All Updates                                                                                                                                               | CM’s implementation disables core, plugin, theme, translation, and automatic updates, plus update checks, cron hooks, update emails, notices, transients, and WordPress.org update requests. |
| Disable Author Archives    | Free     | Yes: Disable User Enumeration, Disable Author Archives | CM blocks author enumeration through author query parameters, REST user endpoints, and author archive pages. |
| Disable Smaller Components | Free     | Partial: Hide WP Version, Remove RSD Link, Remove Shortlink, Disable Emojis, Disable Dashicons, Remove jQuery Migrate, Enable Classic Widgets, and related CM controls | CM covers several bundled ASE subcomponents, but not every component or ancillary behavior in the broad ASE module.                                                                          |

**Disable verdict:** CM covers Gutenberg, comments, REST, and updates well enough to be a serious replacement candidate. It does not cover every smaller WordPress switch in ASE.

### Security

| ASE module                      | Tier     | CM result                                                | Practical answer                                                                                                                                         |
| ------------------------------- | -------- | -------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Limit Login Attempts            | Free+Pro | Yes: Enable Login Lockdown, Enable Extended Lockout      | CM documents maximum failed attempts, lockout duration, extended lockouts, username-validity hiding, form hiding, IP whitelisting, and activity logging. |
| CAPTCHA Protection              | Pro      | Yes: Cloudflare Turnstile and Math Captcha features | CM covers the core CAPTCHA protection job across WordPress, WooCommerce, comment, and frontend post-submission forms. ASE offers additional providers such as ALTCHA and Google reCAPTCHA. |
| Two-Factor Authentication (2FA) | Pro      | Yes: TOTP, Email OTP, Trusted Devices, Rate Limiting | CM covers the core 2FA job with TOTP, email OTP, trusted devices, rate limiting, grace periods, and enrollment controls. ASE-specific recovery-code or role-scope behavior should still be checked if required. |
| Obfuscate Author Slugs          | Free     | Yes: Disable User Enumeration, Disable Author Archives | CM blocks author enumeration through author query parameters, REST user endpoints, and author archive pages. It protects the author-discovery surface without claiming random slug rewriting unless that workflow is specifically required. |
| Email Address Obfuscator        | Free+Pro | Yes: Email & Phone Protection                            | CM documents content-filter and full-page protection, multiple methods, shortcodes, no-JavaScript fallbacks, and phone protection.                       |
| Disable XML-RPC                 | Free     | Yes: Disable XML-RPC                                     | CM completely disables XML-RPC and documents protection against pingback abuse.                                                                          |

**Security verdict:** CM has broad security coverage, including login lockdown, Turnstile, math CAPTCHA, 2FA, XML-RPC, REST, staging protection, and content protection. Keep ASE when you depend on a specific provider or a specific author/email behavior.

### Optimizations

| ASE module           | Tier     | CM result                                                                                                       | Practical answer                                                                                                                                |
| -------------------- | -------- | --------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| Image Upload Control | Free+Pro | Yes: Auto Resize Images After Upload, Skip Smaller Images, Image Converter, Disable Unnecessary Image Sizes | CM covers the core upload-control job through resize, skip-smaller, WebP/AVIF conversion, and intermediate image-size controls. ASE's quality and upload-context options are additional scope details. |
| Revisions Control    | Free     | Yes: Limit Post Revisions                                                                                       | CM documents setting a maximum revision count or disabling revisions. ASE’s extra post-type include/exclude controls are not separately stated. |
| Heartbeat Control    | Free     | Yes: Disable Heartbeat, Heartbeat Frequency                                                                     | Direct match in the CM library.                                                                                                                 |

**Optimization verdict:** CM is a strong ASE replacement candidate for these three rows, but CM’s broader Performance tab is a separate advantage, not proof that every ASE optimization switch exists.

### Utilities

| ASE module | Tier | CM result | Practical answer |
|---|---|---|---|
| Site Backup and Migration | Pro | Different approach: Export Settings, Import Settings | CM settings export is not full-site backup, restore, migration, or sync. Keep ASE or a dedicated backup product. |
| Email Delivery | Free+Pro | Yes: Enable SMTP Settings, Enable Email Logging, Customize WP Emails | CM documents SMTP with backup-server options, email history/resending, and centralized WordPress email customization. Pick one SMTP owner. |
| Form Builder | Pro | Different approach: Form Desk, Frontend Post Submission | CM manages submissions and supports frontend post submission. It does not document a general drag-and-drop form builder with ASE’s field types, autoresponders, and webhooks. |
| File Manager | Pro | Different approach: download and secure-download tools | CM can download files, plugins, themes, and media. It is not a general server file manager. |
| Local User Avatar | Pro | Yes: Local User Avatar | CM documents local custom profile pictures instead of Gravatars. The source image-selection UI differs from ASE’s wording. |
| Multiple User Roles | Free | Different approach: Role Manager | CM manages custom roles and capabilities. Assignment of multiple roles to one user is not stated. |
| Image Sizes Panel | Free+Pro | No | CM has image-size optimization controls, not a confirmed panel listing every generated image URL. |
| View Admin as Role | Free | Yes: View Admin as Role | Direct match. |
| Password Protection | Free+Pro | Yes: Site-Wide Password Protection, Global Password Protection | CM documents site-wide password protection with optional IP bypass and separate public-preview password protection. ASE’s URL-bypass and login-customizer integration are additional options. |
| Maintenance Mode | Free+Pro | No | CM’s maintenance-message control is not a maintenance-mode page builder. |
| Redirect Manager | Pro | Partial: Redirection & Logging, Global 404 Redirect | CM has a redirect-rule editor in the v1.2.1 changelog, but ASE’s regex, status-code, grouping, caching, notes, and loop-detection depth is not confirmed here. |
| Redirect 404 | Free+Pro | Yes: Global 404 Redirect | Direct core match. |
| Display System Summary | Free+Pro | No | No confirmed CM equivalent for the ASE dashboard system summary widget. |
| Search Engines Visibility Status | Free+Pro | Yes: Enable Search Engine Visibility Status | Direct match, including CM’s documented staging visibility protection. |

**Utilities verdict:** This is where the “CM replaces ASE Pro” claim fails most clearly. CM has related settings export, SMTP, Form Desk, downloads, redirects, and password protection, but several of them are different products or narrower workflows.

## What you can often remove ASE for

This is a shortlist, not a blanket instruction. Confirm each enabled module on staging first.

- Post Type Switcher
- Basic SVG upload and sanitization
- Disable Gutenberg
- Basic update disabling
- XML-RPC blocking, if trackback and pingback behavior is not part of the requirement
- Basic revision limiting
- Heartbeat Control
- Basic local avatar support
- View Admin as Role
- Registration Date Column
- Disable Dashboard Widgets
- Wider Admin Menu
- Admin Menu Organizer
- Custom Admin Footer Text
- Basic login URL control
- Basic 404 redirect
- Search Engines Visibility Status
- Basic content duplication

Even here, check the details. A match at the feature-name level does not guarantee identical role rules, post-type scope, frontend behavior, or fallback behavior.

## ASE modules you should usually keep

Keep ASE, or replace it with another dedicated product, when the site depends on:

- **Custom Content Types:** The current core plugin does not include CPTs, custom taxonomies, field groups, or options pages. A full-featured external CM plugin is on the roadmap and awaiting WordPress.org repository approval.
- **Form Builder:** CM Form Desk is an entries manager, not a form builder.
- **Site Backup and Migration:** CM settings export is not a backup and restore system.
- **File Manager:** CM download tools do not replace file editing, permissions, compression, extraction, and copy/move operations.
- **Redirect Manager:** Keep ASE if regex, status codes, groups, notes, cache behavior, or loop detection are important.
- **Media Categories:** Keep ASE if taxonomy categories and insertion filtering matter. CM folders are a different model.
- **External Permalinks, login/logout menus, role-specific login redirects, multiple user roles, maintenance mode, custom body class, or image sizes panel:** These are not confirmed CM matches in the current library.

## CM-only strengths

These are not gaps in ASE. They are areas where Classic Monks adds value outside the direct replacement question.

- **AI:** AI Features, AI Agent, multiple providers, AI tools, image generation/editing, and alt-text workflows.
- **Bricks:** A large native Bricks Builder set covering elements, dynamic data, conditions, interactions, controls, animations, import/export, and optimization.
- **Quick Setup:** Quick WordPress Setup and Bricks setup workflows for new sites.
- **Media:** Image Converter, Folder Manager, media cleanup, renaming, replacement, and media workflow tools.
- **Performance:** Assets Manager, CDN rewrite, lazy loading, intelligent preloading, selective media preload, image optimization, and related controls.
- **WooCommerce:** Product swatches, checkout controls, coupons, order utilities, redirects, email controls, and product price history.
- **Security breadth:** Staging Protection, HTTP Authentication, Cloudflare Turnstile, Math Captcha, 2FA, login lockdown, REST controls, content protection, and other hardening features.
- **White Label:** Broad admin and login branding. The official pricing page lists the full white-label plugin capability under Enterprise.
- **Email workflow:** Email logging, SMTP settings, WordPress email customization, notifications, and WooCommerce email controls.

These strengths can justify using CM even when ASE remains installed for one or two Pro-only workflows.

## Running ASE and Classic Monks together

Running both is reasonable during migration. Running overlapping modules from both is not.

Give one plugin ownership of each concern:

- **SMTP and email delivery:** Use CM or ASE, not both.
- **Login lockdown:** Use CM or ASE for failed-login blocking.
- **2FA:** Use one 2FA implementation.
- **CAPTCHA:** Use one provider and one form integration per form.
- **Code snippets:** Use one snippet manager for a given snippet.
- **Redirects:** Do not create the same redirect rule in both plugins.
- **Media replacement:** Do not let two tools intercept the same replacement action.
- **Admin menu and toolbar cleanup:** Choose one owner for hide, rename, and reorder rules.
- **Password protection and maintenance mode:** Avoid stacking two frontend access gates without documenting the intended order.

Duplicate modules increase the risk of double hooks, conflicting settings, duplicate email delivery, confusing login behavior, and difficult support cases.

## Migration checklist

1. **Inventory enabled ASE modules.** Do not compare installed modules that are switched off.
2. **Mark each module in `matrix-full.csv`.** Separate Free, Free+Pro, and Pro behavior.
3. **Back up the site first.** If you use ASE Pro’s settings export, keep that file. Also make a real full-site backup before deactivation.
4. **Install CM on staging.** Do not test a replacement by switching plugins on a production client site.
5. **Enable one CM equivalent at a time.** Record the exact setting, scope, and expected behavior.
6. **Test the workflows that matter:** admin roles, frontend output, login and logout, scheduled posts, forms, email delivery, redirects, WooCommerce checkout, Bricks editing, cache behavior, and cron jobs.
7. **Disable overlapping ASE modules individually.** Do not remove the entire plugin until the No and Partial rows are accounted for.
8. **Choose one owner for shared concerns.** Especially SMTP, 2FA, CAPTCHA, login lockdown, redirects, code snippets, and admin menus.
9. **Clear caches and retest.** Check page cache, object cache, CDN behavior, browser console, and server logs.
10. **Keep ASE for unresolved gaps.** Plugin-count reduction is not worth losing a required workflow.
11. **After the soak period, remove only what is genuinely redundant.** Keep the migration backup and a record of the old ASE settings.

## Pricing context

Pricing changes, so treat these as the values found during this review rather than permanent claims.

### ASE Pro

The official ASE pricing page currently lists annual licenses at:

- 1 site: **$39/year**
- 5 sites: **$99/year**
- 25 sites: **$149/year**
- 100 sites: **$199/year**
- 200 sites: **$299/year**
- 500 sites: **$399/year**

Lifetime licenses currently range from **$99 for 1 site** to **$1,499 for 500 sites**. Lifetime licenses include one year of support, with separate support renewal pricing shown on the pricing page. ASE also advertises a 14-day money-back guarantee.

### Classic Monks

The official Classic Monks pages currently show yearly pricing of:

- Personal: **$39/year** for 1 site
- Professional: **$119/year** for 25 sites
- Agency: **$199/year** for 100 sites
- Enterprise: **$299/year** for unlimited sites

The current LTD options shown are:

- Agency: **$299 one-time** for 100 sites
- Enterprise: **$599 one-time** for unlimited sites

The CM pricing page also advertises unlimited staging sites, a 15-day money-back guarantee, and Enterprise-only white-label and priority-support benefits. Taxes are calculated at checkout.

The price comparison is not apples-to-apples. ASE has a large set of narrow admin modules and a separate Pro tier. CM bundles a much broader stack, including WooCommerce, Bricks, Performance, AI, and White Label. Buy based on the enabled workflows you need, not the headline feature count.

## FAQ

### Can I drop ASE today after installing Classic Monks?

Usually not without an audit. If your ASE setup is mostly covered modules such as Post Type Switcher, Gutenberg/comments controls, XML-RPC, revisions, Heartbeat, basic admin cleanup, Code Manager workflows, and login URL control, CM may replace it. If you use CCTs, Form Builder, full backup/migration, File Manager, or detailed redirect rules, keep ASE or another dedicated product.

### Does Classic Monks replace ACF or an ASE Custom Content Types setup?

No confirmed current core replacement is available. A full-featured external Custom Content Types plugin is on the Classic Monks roadmap and is awaiting WordPress.org repository approval. The current core plugin has Post Type Switcher, Taxonomy Switcher, Folder Manager, and related content utilities, but not the external CCT plugin yet.

### Does Classic Monks replace Form Builder?

No. CM’s Form Desk manages submissions from supported systems such as Bricks Forms and Fluent Forms. It is not the same as a drag-and-drop form builder with fields, layouts, notifications, entries, and webhooks.

### Can I use Classic Monks with ASE Free?

Yes. Install CM on staging, inventory the enabled ASE modules, and disable only the overlapping module after verification. The free ASE modules that CM does not cover are still valid reasons to keep ASE.

### Can I use Classic Monks without Bricks?

Yes. CM’s Bricks modules are additional features. The core, performance, security, WooCommerce, email, media, setup, and White Label features are separate. Bricks-specific modules simply do not apply when Bricks is not installed.

### How do I find the CM equivalent if the name is different?

Use the search field on the [Classic Monks Features Library](https://classicmonks.com/features/), then use the in-plugin `/` search. Search concepts as well as exact names. For example, search `post type`, `login`, `redirect`, `SMTP`, or `media replacement`. If no named match appears, treat it as No or Unknown rather than assuming a nearby feature is equivalent.

### Should both plugins handle SMTP, 2FA, login lockdown, or redirects?

No. Pick one owner per concern. Running both can create duplicate hooks, conflicting settings, or unclear behavior. Keep both plugins only when each owns a genuinely different job.

## Final answer

Classic Monks can replace a meaningful part of ASE, especially for agencies that also want Performance, WooCommerce, Bricks, AI, media, email, setup, and White Label features. It is not an honest 100% ASE Pro replacement based on the current matrix.

The practical decision is simple:

- **Drop ASE** when your enabled modules are covered and staging tests pass.
- **Keep ASE** when you depend on CCTs, forms, full backups, file operations, detailed redirects, or a narrow ASE-only utility.
- **Use both** when CM is your broader core stack and ASE fills a small, clearly documented gap.

If you have an ASE setup that is not covered here, paste the enabled module list in the Classic Monks Facebook group. The exact list is more useful than a generic plugin comparison.

[View the full Classic Monks feature library](https://classicmonks.com/features/)  
[Read the Classic Monks documentation](https://classicmonks.com/docs/)  
[View the ASE feature list](https://www.wpase.com/features/)  
[Join the Classic Monks Facebook group](https://www.facebook.com/groups/611315455344242/)

---

**Last updated:** July 30, 2026  
**Sources:** [ASE Features](https://www.wpase.com/features/), [ASE Pricing](https://www.wpase.com/pricing/), [ASE Documentation](https://www.wpase.com/documentation/), [Classic Monks Features](https://classicmonks.com/features/), [Classic Monks Pricing](https://classicmonks.com/pricing/), [Classic Monks Changelog](https://classicmonks.com/changelog/), [v2.1.0 release](https://classicmonks.com/changelog/classic-monks-v2-1-0/), [Classic Monks Docs](https://classicmonks.com/docs/), and the local CM feature library at `LocalSites/cmdev02-corel/.../docs/features-docs/cm-features-parent.md`.
