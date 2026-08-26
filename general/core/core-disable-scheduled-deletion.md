---
title: "How to Disable Scheduled Deletion in Classic Monks"
slug: disable-scheduled-deletion
description: "Disable Scheduled Deletion in Classic Monks prevents WordPress from auto-deleting trashed posts after 30 days. Gives you a longer recovery window for accidentally deleted content."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-scheduled-deletion/
---

# How to Disable Scheduled Deletion in WordPress

> Disable Scheduled Deletion prevents WordPress from automatically deleting posts that have been in the trash for 30 days. Posts stay in the trash indefinitely until you restore or permanently delete them manually.

## Key Takeaways

- Single toggle, no nested options
- Affects all post types globally
- Posts in trash stay there until you restore or delete manually
- Useful for sites where editors frequently "undo" deletions
- No performance impact (trash is just a flag on the post)

## What Is Disable Scheduled Deletion?

WordPress automatically empties the trash after 30 days. Posts that have been in the trash for 30+ days are permanently deleted by a scheduled cron event (`wp_scheduled_delete`). Disable Scheduled Deletion prevents that cron from running on Classic Monks-managed posts, so the trash never auto-empties.

## Why You Need It

The default 30-day auto-empty is fine for most sites, but some scenarios call for a longer recovery window:

- **Multi-author sites**: An editor might trash a post by accident, not realize it for weeks, and then need to restore it
- **High-stakes content**: Pages or posts that represent significant work, where accidental permanent deletion is a real risk
- **Compliance**: Some industries require a longer audit trail of deleted content

Disable Scheduled Deletion is a single toggle that removes the auto-empty behavior. The trash still works normally (trash, restore, permanently delete); only the automatic cleanup is disabled.

---

## How to Use Disable Scheduled Deletion in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Content Subtab

Click on the **Core** menu, then click the **Content** subtab.

### Step 3: Enable Disable Scheduled Deletion

Scroll to the **Editorial Workflow** section and toggle on **Disable Scheduled Deletion**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Verify

Go to **Posts > All Posts** and click the **Trash** link at the top of the list. Note any posts in the trash. After 30 days, check again. With Disable Scheduled Deletion on, those posts will still be in the trash.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable Scheduled Deletion** | Master toggle. Prevents the auto-empty cron. | Off |

No nested options. The feature is site-wide.

---

## Manual Cleanup

With Disable Scheduled Deletion on, the trash grows over time. Periodically clean it manually:

1. Go to **Posts > All Posts** and click **Trash**
2. Review the trashed posts (sort by date deleted)
3. For each one: click **Restore** (if it was a mistake) or **Delete Permanently** (if it's truly unwanted)

For bulk operations, use WordPress CLI:

```bash
# Delete all posts in trash that are more than 90 days old
wp post delete $(wp post list --post_status=trash --format=ids) --force
```

Or use the standard WordPress bulk action: select posts, choose **Delete Permanently** from Bulk Actions, click Apply.

---

## Developer Notes

Disable Scheduled Deletion prevents WordPress from auto-deleting trashed posts after 30 days. No developer hooks are currently exposed.

**Options used:**
| Option | Type | Default |
|--------|------|---------|
| `disable_scheduled_deletion` | Boolean | `false` |
---

## Troubleshooting

### Posts are still being auto-deleted after 30 days

**Cause:** A different plugin or hosting provider is enforcing the auto-empty independently of Classic Monks. Some backup or security plugins run their own cleanup tasks.
**Fix:** Check your other plugins for "trash empty" or "auto-delete" settings. Some hosts (Kinsta, WP Engine) have server-level cron overrides.

### The trash shows hundreds of old posts

**Cause:** Disable Scheduled Deletion has been on for a long time and old trash has accumulated.
**Fix:** Use the manual cleanup pattern above. Filter by date, restore anything important, delete the rest.

### I want to enable Disable Scheduled Deletion only for specific post types

**Cause:** The toggle is global. Some post types (e.g., comments) shouldn't be affected.
**Fix:** Use the `cm_disable_scheduled_deletion_post_types` filter to scope the disable to specific post types. Comments and other internal post types are unaffected by the standard auto-empty anyway (the cron runs on `post`, `page`, and other public post types), so this filter is rarely needed.

### The toggle is on but the cron is still running

**Cause:** The cron is scheduled by WordPress core. Disabling the toggle only prevents Classic Monks from filtering the deletion. Other code paths (e.g., `wp_delete_auto_drafts` cron for drafts) may still run.
**Fix:** The toggle specifically affects the `wp_scheduled_delete` event for trashed posts. For full control over all auto-cleanup, use a custom plugin that hooks into all relevant cron events.

---

## Related Articles

- [How to Use Content Management in Classic Monks](core-content-management.md)
- [How to Use Logs in Classic Monks](core-logs.md)
