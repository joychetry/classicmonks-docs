---
title: "Migrate from ASE or Perfmatters to Classic Monks"
slug: migrate-from-ase-perfmatters
description: "Move your ASE or Perfmatters setup into Classic Monks in one click. What transfers, what stays behind, and how to verify the switch."
last_updated: 2026-09-10
author: Joy
reading_time: 8 min
canonical: "https://classicmonks.com/docs/migrate-from-ase-perfmatters/"
---

# How to Migrate from ASE or Perfmatters in WordPress

> Switching plugins used to mean rebuilding every setting by hand. Classic Monks scans your old plugin and carries the active setup across for you.

> **IMAGE PLACEHOLDER (name: migration-hero)**
>
> **Why:** Featured and OG image, sets the switch narrative before any steps.
> **Type:** Illustration, side-by-side ASE and Perfmatters marks pointing into the Classic Monks dashboard.
> **Title:** Switch to Classic Monks in one click
> **Suggested alt:** "Migrate from ASE or Perfmatters to Classic Monks"
> **Placement:** Directly under the H1 block, article hero. Future file: docs/images/options/migration/migration-hero.png.

## Key Takeaways

- The Migration assistant lives under Classic Monks, Options, Migration, and it handles ASE (free or Pro) and Perfmatters.
- Nothing moves until you review the scan and confirm. Matched settings stay checked by default, and anything without an equivalent is listed with a reason.
- SMTP connections, redirect rules, admin column layouts, and avatar images move with their data, not just their on/off toggle.
- A few things never transfer, like snippet code, script optimization, and per-user 2FA enrollment. The guide names each one so nothing surprises you.
- There is no undo button, so export your Classic Monks settings first. The whole pass takes about five minutes.

## Why This Exists

The hard part of switching plugins was never the install. It was the afternoon lost re-entering settings you had already configured once. v2.3.0 removes that cost for anyone moving off ASE or Perfmatters. The import assistant reads the stored options of the old plugin, shows you exactly what it found, and writes the equivalents into Classic Monks when you approve. Switching from ASE moves 70-plus settings in one pass: email, redirects, columns, avatars. Switching from Perfmatters adds per-category checkboxes and an instant summary.

Use it when you are consolidating. If ASE or Perfmatters is still active on the site and you plan to run Classic Monks instead, migrate first and deactivate the old plugin after. If you are still deciding, read [Classic Monks vs ASE](../../comparison/classic-monks-vs-ase.md) and [Classic Monks vs Perfmatters](../../comparison/classic-monks-vs-perfmatters.md) for an honest breakdown of what each plugin does best.

## Recommendations Before Enabling

- Export your current Classic Monks settings under Options, Export. The drawer warns you and it means it: there is no undo for a migration write.
- Keep the source plugin installed and active until the migration is verified. The Migrate button stays disabled when no source data is found, so an early deactivation locks you out of the scan.
- You need an administrator account. Both scan and apply check the manage_options capability.
- Know that Overwrite Existing Settings starts checked. When it is on, imported values replace what Classic Monks already holds. Uncheck it when you have tuned Classic Monks already and only want to fill the gaps.

## Migrate in Six Steps

### Step 1: Open the Migration subtab

Go to Classic Monks, Options, Migration. You will see one card per source plugin with a Migrate button. A greyed-out button means that plugin left no data on this site.

> **IMAGE PLACEHOLDER (name: migration-provider-cards)**
>
> **Why:** Readers must recognize the subtab on sight, including the disabled-button state.
> **Type:** UI screenshot of Options, Migration with both provider cards visible.
> **Title:** Migration subtab with ASE and Perfmatters cards
> **Suggested alt:** "Classic Monks Migration subtab showing ASE and Perfmatters Migrate buttons"
> **Placement:** End of Step 1. Future file: docs/images/options/migration/migration-provider-cards.png.

### Step 2: Open the drawer and scan

Click Migrate on the source you are leaving. A slide-in drawer opens. Click Scan. Classic Monks reads the source options and reports back, usually within seconds.

### Step 3: Review what matched

Matched Features lists every active source setting that has a Classic Monks equivalent, grouped by area (Performance, Security, Interface, and so on). Each row starts checked. Uncheck anything you want to keep as-is. Notes under some rows flag when stored data travels with the toggle.

> **IMAGE PLACEHOLDER (name: migration-matched-features)**
>
> **Why:** The grouped checkbox list is the core review moment, show it exactly.
> **Type:** UI screenshot of the drawer Matched Features card with groups and checked rows.
> **Title:** Matched features grouped by area
> **Suggested alt:** "Migration drawer showing matched ASE features grouped by area"
> **Placement:** End of Step 3. Future file: docs/images/options/migration/migration-matched-features.png.

### Step 4: Read what did not match

The Not Migrated list names everything staying behind and says why. Check it before you continue. If something on that list matters to you, plan the manual step now instead of discovering it later.

> **IMAGE PLACEHOLDER (name: migration-not-migrated)**
>
> **Why:** The honest skip list is the trust moment, readers should see its shape.
> **Type:** UI screenshot of the drawer Not Migrated card with two or three reasoned rows.
> **Title:** Not Migrated list with reasons
> **Suggested alt:** "Migration drawer Not Migrated list showing skipped features with reasons"
> **Placement:** End of Step 4. Future file: docs/images/options/migration/migration-not-migrated.png.

### Step 5: Set the overwrite toggle and apply

Leave Overwrite Existing Settings on for a fresh switch. Turn it off when Classic Monks already holds values you want to keep. Click Migrate Selected. Applied rows flip to a migrated state right in the drawer, so you can move a subset now and the rest later.

> **IMAGE PLACEHOLDER (name: migration-overwrite-apply)**
>
> **Why:** The overwrite default (on) is the riskiest control, show where it sits.
> **Type:** UI screenshot of the overwrite toggle and the Migrate Selected footer button.
> **Title:** Overwrite toggle and Migrate Selected button
> **Suggested alt:** "Migration drawer overwrite toggle and Migrate Selected button"
> **Placement:** End of Step 5. Future file: docs/images/options/migration/migration-overwrite-apply.png.

### Step 6: Reload and verify

Confirm the reload prompt so the settings screens reflect the new values. Then spot-check the areas that matter (the verification list below). Only deactivate the old plugin once the checks pass.

## What Moves from ASE

ASE stores its setup in one flat option array, and the assistant maps the settings you actually switched on: the cleanup toggles (emojis, embeds, XML-RPC, jQuery Migrate, RSD link, shortlink, hiding the WordPress version, feeds, comments, updates), the interface toggles (dashboard widgets, admin notices, wider menu, media infinite scroll, last login column), duplication, media replacement, SVG support, Gutenberg controls, file-editor lockdown, email obfuscation, password protection, login lockdown, revisions, heartbeat, REST API, the custom login URL and slug, image size caps, the admin logo, login page layout, and content and term ordering.

Four modules carry their stored data along with the toggle.

- SMTP Email Delivery becomes a connection named Imported from ASE in Email Manager, with host, port, encryption, username, from name, and from email. The password decrypts server-side in most cases. When it cannot, you get an empty password field and a note telling you to re-enter it under [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md). Reply-to, BCC, SSL bypass, and debug flags have no Classic Monks column and are named in the report.
- Redirect Manager imports literal redirect rules (301, 302, 307, 308) into Classic Monks redirects. Regex rules, wildcards, error-page rules, and odd statuses are skipped by name because the Classic Monks engine matches exact paths.
- Admin Columns Manager imports per-post-type column layouts, including extra columns, custom fields, and freeze settings. Post types you already configured in Classic Monks are left alone unless overwrite is on. The layout editor itself is covered in [the custom columns guide](../core/core-custom-columns.md).
- Local User Avatar copies each user's avatar attachment id. Re-runs stay safe: users who already have a Classic Monks avatar are skipped unless overwrite is on.

One deliberate exception: 2FA carries the enable flag but never the enrollment. Every user re-enrolls and gets a fresh QR code in Classic Monks. Migrating stale secrets would risk locking people out, so the drawer says this plainly.

## What Moves from Perfmatters

Perfmatters settings arrive grouped by area, and you pick with the same per-row checkboxes. Performance covers the optimization toggles (emojis, Dashicons, embeds, XML-RPC, RSD link, jQuery Migrate, version hiding, shortlink, feeds, feed links, self-pingbacks, Google Maps, comments, comment URLs, Google Fonts, global styles, REST API links). Security covers the REST API restriction. Lazy Loading covers images, iframes, YouTube previews, exclusions, threshold, fade animation, background images, and critical image preload. Preloading covers instant page and speculative mode. CDN covers the enable flag, URL, directories, and exclusions. Analytics covers local hosting, tracking id, script type, and the admin-tracking inversion. The WooCommerce controls move too, including the script-unloading toggles described in [How to Disable WooCommerce Scripts in WordPress](../woocommerce/woocommerce-disable-woocommerce-scripts.md), plus cart fragmentation and the status meta box. Revisions, autosave interval, heartbeat, the custom login URL, and the blank favicon round out the set.

## Value Conversions Worth Knowing

A few settings do not copy verbatim because the two plugins measure differently. Classic Monks converts them instead of writing values its own sanitizer would reject.

- Revision limits clamp to the Classic Monks cap of 5.
- Heartbeat migrates only when every context was disabled at the source. A partial heartbeat setup has no honest equivalent and is skipped with a reason.
- The REST API restriction maps to the closest Classic Monks mode rather than copying the source value.
- The analytics script type translates (gtag becomes gtag.js), and lazy load thresholds drop the px suffix.
- The login URL behavior maps redirect-style values to the Classic Monks redirect options.

## What Stays Behind

Nothing on these lists fails silently. Each appears in the Not Migrated section with its reason.

From ASE: snippet code and headers (the toggle moves, the code does not, so paste snippets into Code Manager by hand), the admin menu order (redo it in Admin Menu Organizer), custom content types and field groups (use a dedicated CPT or fields plugin), maintenance mode, file manager, contact form and form builder data, captcha keys (Classic Monks ships Turnstile plus a math captcha, and keys are never shared), AVIF upload (WordPress core accepts AVIF natively since 6.0, so the toggle is redundant), and the WLW manifest tag (covered only inside the clean head bundle).

From Perfmatters: header, body, and footer code (Code Manager is a snippet system, so re-enter them by hand), the script optimization pipeline (defer, delay, minify, and unused CSS have no equivalent in Classic Monks), Script Manager per-post rules, the database optimizer and its scheduled cleanups, manual preload rows, preconnect, DNS prefetch, early hints, fetch priority, image dimensions, DOM monitoring, custom lazy elements, and parent exclusions.

## Verification

- Matched counts look right: the drawer tells you how many of the mapped features were enabled at the source. A suspiciously low number usually means the source plugin was already deactivated.
- Email still sends: open Email Manager and confirm the Imported from ASE connection, then send a test mail to yourself.
- Redirects fire: open two or three imported redirects in a private window and confirm the destination and status.
- Columns look right: open Posts and Pages list tables and confirm the order and visibility match the old layout.
- Avatars survived: check two or three user profiles for their images.
- Performance behaves: view source on the frontend and confirm the expected removals (emojis, embeds, version string) actually took effect.

> **IMAGE PLACEHOLDER (name: migration-verified-smtp)**
>
> **Why:** Show what success looks like on the highest-risk import.
> **Type:** UI screenshot of Email Manager with the Imported from ASE connection row.
> **Title:** Imported SMTP connection in Email Manager
> **Suggested alt:** "Email Manager showing the Imported from ASE SMTP connection"
> **Placement:** End of Verification. Future file: docs/images/options/migration/migration-verified-smtp.png.

## Troubleshooting

### The Migrate button is disabled

Cause: no source data exists in the database. Either the plugin was never active here or it was deleted with data removal on. Fix: reinstall the source plugin, or restore its settings from backup, then return to the Migration subtab.

### The scan finds zero features

Cause: the source plugin is installed but everything mapped is switched off there. Fix: enable the features in the source plugin first, then re-scan. The drawer message says exactly this.

### SMTP imported but mail fails

Cause: the password could not be decrypted and the field is empty. Fix: open Email Manager, open the Imported from ASE connection, re-enter the password, and send a test mail.

### Some redirects are missing

Cause: regex, wildcard, error-page, or unsupported-status rules do not import. Fix: recreate those specific rules in the Classic Monks format or keep them in a dedicated redirect plugin, and confirm the skipped reasons name them.

### Avatars did not carry over

Cause: the avatar toggle was off at the source, or users already hold Classic Monks avatars with overwrite off. Fix: enable Local User Avatar at the source and re-run, or switch overwrite on for the avatar row only.

### Snippets and menu order are gone

Cause: these never migrate, only their toggles do. Fix: copy snippet code into Code Manager manually and rebuild the menu order in Admin Menu Organizer before deactivating ASE.

## Frequently Asked Questions

### Does migration delete or change the source plugin

No. The scan only reads. Your ASE or Perfmatters settings stay untouched, so you can compare side by side and roll back by reactivating the old plugin.

### Can I re-run a migration

Yes. Writes are idempotent: values that already match are skipped, SMTP connections dedupe on host, and redirects dedupe on path. Re-running after enabling more features at the source picks up just the new ones.

### Should overwrite stay on

For a first-time switch, yes. When Classic Monks is already tuned and you only want to fill unset options, turn it off. The toggle sits in the drawer above the apply button with its behavior spelled out.

### Do I need the source plugin active

For the scan, the plugin's stored data must be present. Deleting the plugin with data removal wipes that. Keep it installed until verification passes, then deactivate and remove it.

## Related Articles

- [How to Export Settings in WordPress](options-opt-export.md)
- [How to Import Settings in WordPress](options-opt-import.md)
- [How to Use the Options Tab in WordPress: Feature Index](../options.md)

Written by Joy. Last updated 2026-09-10. 8 min read. Tested with WordPress 7.1 and Classic Monks 2.3.0.
