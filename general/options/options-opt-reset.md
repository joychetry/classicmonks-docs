---
title: "How to Reset Classic Monks Settings in WordPress | CM"
slug: options/opt-reset
description: "Reset all Classic Monks settings to defaults. Useful for starting fresh without reinstalling the plugin."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/options/opt-reset/
---

# How to Reset Classic Monks Settings in WordPress

> Reset all Classic Monks settings to defaults. Useful for starting fresh without reinstalling the plugin.

## Key Takeaways

- Administrative feature for plugin management
- Does not affect frontend functionality
- Reversible where applicable
- Use with caution (some actions are irreversible)

## Why You Need It

If your configuration is broken or you want to start fresh, resetting to defaults is faster than reinstalling the plugin.

---

## How to Use This Feature

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings, then the **Options** tab.

### Step 2: Select the Feature

Click the relevant subtab and follow the on-screen instructions.

---

## Common Use Cases

### Site migration

When migrating a Classic Monks configuration to a new site, use Export on the old site and Import on the new site.

### Clean start

If the configuration is broken, use Reset to restore defaults. For a completely clean slate, use Uninstall.

### License management

Keep your license key active for updates and support. Deactivate before migrating to a new domain.

---

## Troubleshooting

### Import is not working

**Cause:** The import file may be corrupted or from an incompatible version.
**Fix:** Verify the file is a valid JSON export from Classic Monks. Check the PHP error log for import errors.

### Reset didn't work

**Cause:** The reset may require a page refresh or database flush.
**Fix:** Clear all caching. Check the WordPress error log. If the reset didn't complete, try again after clearing the cache.

### Uninstall is not removing all data

**Cause:** Some data may be stored in options that the uninstall doesn't clean.
**Fix:** After uninstalling, manually check the `wp_options` table for `cm_*` prefixed options and remove them.

---

## Related Articles

- [How to Use Content Management in WordPress](../core/core-content-management.md)
- [How to Use the Email Tab in Classic Monks: Feature Index](../email.md)
- [How to Use the Security Tab in Classic Monks: Feature Index](../security.md)


### Developer integration

The Options tab provides programmatic access to settings via core functions.

**Settings functions:**

- `cm_get_option( $key, $default )` retrieves a setting value from the `cm_options` table
- `cm_update_option( $key, $value )` saves a setting value
- `cm_import_settings( $settings_array )` imports settings from an array

**WP Reset hooks:**

- `wp_ajax_cm_reset_database` handles database reset requests
- `wp_ajax_cm_delete_content` handles content deletion
- `wp_ajax_cm_empty_wp_content` handles emptying wp-content
- `wp_ajax_cm_delete_plugins` handles plugin deletion
- `wp_ajax_cm_delete_themes` handles theme deletion
- `wp_ajax_cm_complete_reset` handles complete reset

**White Label hooks:**

- `all_plugins` filter modifies plugin data display
- `plugin_row_meta` filter modifies plugin row metadata
