---
title: "How to Disable All WooCommerce Admin Features in WordPress | CM"
slug: woocommerce/disable-woocommerce-admin-features
description: "Completely disable WooCommerce 4.0+ admin features. Reverts to the classic admin interface for improved performance and compatibility."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/woocommerce/disable-woocommerce-admin-features/
---

# How to Disable All WooCommerce Admin Features in WordPress

> Disable all WooCommerce 4.0+ admin features to revert to the classic admin interface for improved performance and compatibility with older admin workflows.

## Key Takeaways

- Single toggle, no nested options
- Faster admin performance (no React or modern JavaScript overhead)
- Familiar classic interface for long-time WooCommerce users
- Better compatibility with older admin customizations

## What Is the Disable all WooCommerce admin features feature?

WooCommerce 4.0+ introduced a new admin interface built on React and modern JavaScript. While this provides a more modern experience, it can be slow on low-end servers and is incompatible with some older admin workflows. This feature completely disables the new admin features, reverting to the classic interface.

## Why You Need It

The WooCommerce 4.0+ admin interface is built on modern JavaScript (React, custom routing, REST API). For stores on low-end servers, this can be slow. For admins used to the classic interface, the new interface adds a learning curve. This feature reverts to the classic interface for better performance and familiarity.

---

## How to Disable All WooCommerce Admin Features in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Optimization** subtab.

### Step 3: Enable the Feature

Toggle on **Disable all WooCommerce admin features**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Go to the WooCommerce admin. The interface should look like the classic WooCommerce admin (pre-4.0).

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable all WooCommerce admin features** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- The new React-based admin interface is disabled
- The classic admin interface is restored
- Faster admin performance (no modern JavaScript)

## What Does NOT Get Affected

- The customer-facing shop (WooCommerce is still a fully functional e-commerce platform)
- The admin data (orders, products, settings are all preserved)
- The WooCommerce admin menu structure (some items may be moved, but all are present)

---

## Advanced Options (Developers)

This feature registers 3 WordPress hooks in `woocommerce-functions.php`:

**Filters:**

- `woocommerce_admin_disabled` calls `__return_true()` (Disables WooCommerce admin features)
- `woocommerce_marketing_menu_items` calls `__return_empty_array()` (Removes WooCommerce marketing menu items)
- `woocommerce_admin_features` calls `anonymous()` (Removes WooCommerce admin features (priority 90))

```php
// Hooked in woocommerce-functions.php
add_filter( 'woocommerce_admin_disabled', '__return_true' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Common Use Cases

### Custom Reporting and Analytics

Stores that use third-party reporting (Metorik, WooCommerce Reports Pro, custom analytics dashboards) don't need the WC admin reporting. Disabling the new admin removes the built-in reports and provides a faster, more focused admin experience. The third-party reports work as expected, unaffected by this toggle.

### White-label admin experiences

If you provide white-label WooCommerce services to clients, the classic admin is more familiar and easier for non-technical users to navigate.

### WordPress 5.x legacy sites

If you're still using an older WordPress admin theme (pre-5.0), the new WC admin may conflict. Disabling it uses the classic interface.

### Multi-vendor marketplaces

Some multi-vendor plugins (Dokan, WCFM) have their own admin. Disabling the WC admin prevents confusion and conflicts.

### Low-end server hosting

The React-based admin is heavy. On shared hosting or low-CPU servers, the classic admin loads faster and is more reliable.

### Custom admin workflows

Some stores use custom admin interfaces (e.g., WP Admin UI plugins, custom dashboard widgets). Disabling the new admin prevents conflicts.

### Long-time WooCommerce users

If your team is used to the pre-4.0 admin interface, disabling the new admin provides a familiar workflow.

## Troubleshooting

### The feature is not taking effect

**Cause:** The toggle is off, or a caching plugin is serving the old page.
**Fix:** Verify the toggle is on. Clear all caching layers (page cache, object cache, CDN).

### I want the feature to apply only to specific pages

**Cause:** The toggle is global.
**Fix:** Use a small custom plugin that checks the current page and conditionally enables the feature (e.g., via the filter above).

### A third-party plugin is breaking after enabling

**Cause:** Some plugins depend on the disabled feature.
**Fix:** Disable the toggle and find an alternative (e.g., conditional loading via a performance plugin).

### The change is not visible to customers

**Cause:** The feature is admin-only or affects specific page types that the customer doesn't visit.
**Fix:** Verify the feature is working in the appropriate context (e.g., admin pages, non-WooCommerce pages, etc.).

---

## Related Articles

- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
- [How to Use Logs in WordPress](../core/core-logs.md)
