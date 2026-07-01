---
title: "How to Disable Marketplace Suggestions in WordPress | CM"
slug: woocommerce/disable-marketplace-suggestions
description: "Remove WooCommerce marketplace suggestions from the admin interface. Reduces clutter for stores that don't need the marketplace recommendations."
last_updated: 2026-06-24
author: Joy
reading_time: 2 min
canonical: https://classicmonks.com/docs/woocommerce/disable-marketplace-suggestions/
---

# How to Disable Marketplace Suggestions in WordPress

> Disable marketplace suggestions and promotional content from the WooCommerce admin interface for a cleaner admin experience.

## Key Takeaways

- Single toggle, no nested options
- Cleaner WooCommerce admin interface
- Reduced visual clutter from promotional content
- Faster admin page loads (less content to render)

## What Is the Disable marketplace suggestions feature?

WooCommerce's admin interface includes marketplace suggestions and promotional content (e.g., extension recommendations, theme suggestions, service promotions). For stores that don't need these recommendations, this feature removes them from the admin, providing a cleaner interface.

## Why You Need It

WooCommerce's marketplace suggestions are designed to help new store owners discover extensions and services. For established stores with their own stack, the suggestions are noise. Disabling them simplifies the admin interface and removes distracting promotional content.

---

## How to Disable Marketplace Suggestions in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Optimization** subtab.

### Step 3: Enable the Feature

Toggle on **Disable marketplace suggestions**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Go to the WooCommerce admin. The marketplace suggestions should not be visible.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable marketplace suggestions** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- Marketplace suggestions and promotional content are removed
- The WooCommerce admin interface is cleaner
- Admin pages load slightly faster

## What Does NOT Get Affected

- WooCommerce's core functionality (orders, products, etc.)
- The ability to install extensions manually (via Plugins > Add New)
- The WooCommerce data and settings

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Filters:**

- `woocommerce_allow_marketplace_suggestions` calls `__return_false()` (Disables WooCommerce marketplace suggestions (priority 999))

```php
// Hooked in woocommerce-functions.php
add_filter( 'woocommerce_allow_marketplace_suggestions', '__return_false' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Common Use Cases

### Multi-Author Content Sites

For sites that have a large content team (multi-author blogs with a shop section), the marketplace suggestions appear for every author. Removing them keeps the author experience focused on content creation. The shop managers can re-enable the suggestions on their own admin views via a small custom plugin if needed.

### Multi-store Networks

If you run a WordPress network (multisite) with multiple WooCommerce stores, the marketplace suggestions appear on every store's admin. Disabling the suggestions on the network level (via a small custom plugin) provides a cleaner admin experience for the network administrators. The suggestions can be re-enabled per-store if needed for new stores that want to discover extensions.

### Multi-language stores

For stores that serve customers in multiple languages via WPML or Polylang, the marketplace suggestions add noise to the localized admin experience. Disabling them keeps the admin focused on the localized workflow.

### Independent brands

Brands that want to control which extensions their customers see (rather than the WC marketplace recommendations) disable the suggestions for a cleaner admin.

### White-label stores

If you build sites for clients and the WC marketplace suggestions would distract from your client's own recommended tools, disable them.

### Established stores

Stores with a stable extension stack don't need marketplace recommendations. Disabling them reduces admin clutter.

### Custom-built stores

Stores with custom themes and custom plugins don't need suggestions for third-party extensions. Disabling them improves focus.

### High-volume admin users

For staff processing many orders per day, every admin interaction counts. Removing marketplace suggestions speeds up the admin workflow.

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
