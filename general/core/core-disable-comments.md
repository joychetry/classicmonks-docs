---
title: "How to Disable Comments in Classic Monks | CM"
slug: disable-comments
description: "Globally disable WordPress comments in Classic Monks. Hides comment forms, prevents new submissions, and disables comment-related admin sections site-wide."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/disable-comments/
---

# How to Disable Comments in WordPress

> Disable Comments globally turns off the WordPress comment system on all post types. The comment form is hidden, new submissions are blocked, and comment-related admin sections are removed.

## Key Takeaways

- Single toggle, site-wide effect
- Hides comment form, blocks new submissions, removes comment admin sections
- Existing comments remain in the database (not deleted)
- The Discussion meta box and Recent Comments widget are affected
- Useful for business sites, portfolios, landing pages, and any site that does not need comments

## What Is the Disable Comments feature?

Disable Comments is a Classic Monks feature that uses a single toggle to suppress the entire WordPress comment system. Once enabled, the comment form does not appear on any post or page, new comment submissions are blocked at the server level, and comment-related admin UI elements (Discussion meta box, Recent Comments widget, comment counts in the post list) are hidden or removed.

Existing comments remain in the database but are not displayed on the front-end (unless the post's comment status is manually set to "open" via direct database edit, which is rare).

## Why You Need It

Many WordPress sites do not need comments:

- **Business sites**: Contact forms, not comment threads
- **Portfolios**: Showcase work, not solicit feedback via comments
- **Landing pages**: Conversion-focused, not discussion
- **Documentation sites**: Information delivery, not conversation
- **Internal sites**: Comments would be a security risk

Disabling comments in WordPress is awkward by default: you have to disable comments for each post type individually, then disable pings, then disable the comment form in your theme, then disable comment-related widgets, then block comment subscription emails. Disable Comments does it all with one toggle.

---

## How to Use Disable Comments in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Content Subtab

Click on the **Core** menu, then click the **Content** subtab.

### Step 3: Enable Disable Comments

Scroll to the **Comment System Overrides** section and toggle on **Disable Comments**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Verify

Open any post on the front-end. The comment form should not appear. Open a post edit screen in the admin. The Discussion meta box should be hidden or read-only.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable Comments** | Master toggle. Site-wide effect. | Off |

No nested options.

---

## What Gets Disabled

| Element | Behavior |
|---------|----------|
| Comment form on posts/pages | Hidden |
| "Leave a Reply" heading | Hidden |
| Existing comments display | Hidden (unless manually set to open in DB) |
| New comment submissions | Blocked at the server level (returns 403) |
| Discussion meta box (post edit screen) | Hidden |
| Recent Comments widget | Hides the widget, but does not delete its configuration |
| Comment counts in post list | Hidden |
| Comment RSS feed | Disabled (returns 404) |
| Comment subscription emails | Stopped |
| Comment count in Activity dashboard widget | Hidden |
| "Comments" submenu in admin | Hidden |
| Existing comments in the database | Preserved (not deleted) |

---

## What Does NOT Get Disabled

- Trackbacks and pingbacks from other sites: still accepted unless the related settings are also disabled
- WooCommerce product reviews: separate system, not affected (use WooCommerce settings to disable)
- bbPress or other forum plugin comment systems: not affected

---

## Developer Notes

Disable Comments suppresses the entire WordPress comment system. No developer hooks are currently exposed.

**Options used:**
| Option | Type | Default |
|--------|------|---------|
| `disable_comments` | Boolean | `false` |
---

## Troubleshooting

### The comment form is still appearing after enabling

**Cause:** A caching plugin is serving a cached version of the page with the form still embedded. The CSS is hiding it, but the form HTML is still being sent.
**Fix:** Clear all caching layers. The form HTML is hidden, not removed, until the cache is cleared.

### Existing comments are still showing on the front-end

**Cause:** The post's comment status is set to "open" in the database. Disable Comments hides the form, but posts with `comment_status = 'open'` may still display existing comments.
**Fix:** Bulk-update the comment status via WordPress CLI: `wp post update --comment_status=closed $(wp post list --format=ids)`. Or use a small custom plugin to force `comment_status = 'closed'` on all posts.

### Trackbacks and pingbacks are still being received

**Cause:** Trackbacks have a separate setting (Settings > Discussion > "Allow link notifications from other blogs (pingbacks and trackbacks)"). Disable Comments does not affect this setting.
**Fix:** Disable pingbacks/trackbacks separately in Settings > Discussion, or via a small custom plugin that filters `pingback_url`.

### Comments are disabled on the front-end but show in the admin

**Cause:** The admin still shows the Comments submenu and the Comments count in the post list, even when front-end comments are disabled. This is intentional: the admin still needs to manage existing comments (mark as spam, delete, etc.).
**Fix:** To fully hide the admin comments UI, add a custom plugin: `add_action( 'admin_menu', function() { remove_menu_page( 'edit-comments.php' ); } );`. Note this is a separate decision from disabling front-end comments.

### I want to re-enable comments for specific posts

**Cause:** The toggle is global, but you want exceptions.
**Fix:** Use the `cm_disable_comments_post_ids` filter to specify a list of post IDs that should still allow comments. Or use a custom post meta `_cm_force_comments_open` and filter `comments_open` to honor it (see Advanced Options).

---

## Related Articles

- [How to Configure Comments in Classic Monks](core-comments.md)
- [How to Manage Content in Classic Monks](core-content-management.md)
- [How to Use Logs in Classic Monks](core-logs.md)
