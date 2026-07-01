---
title: "How to Remove the Connect Your Store Notice in WordPress | CM"
slug: remove-woocommerce-connect-store-notice
description: "Remove the persistent WooCommerce.com connection notice from the admin interface. Reduces admin clutter for stores that don't need the marketplace connection."
last_updated: 2026-06-24
author: Joy
reading_time: 2 min
canonical: https://classicmonks.com/docs/remove-woocommerce-connect-store-notice/
---

# How to Remove the Connect Your Store Notice in WordPress

> Remove the persistent WooCommerce.com connection notice from the admin interface to reduce clutter and eliminate unnecessary promotional content.

## Key Takeaways

- Single toggle, no nested options
- Removes the persistent admin notice
- Cleaner admin interface for stores that don't need marketplace features
- No functional impact (the connection is optional)

## What Is the Remove 'Connect your store' notice feature?

WooCommerce displays a persistent 'Connect your store' notice in the admin that prompts store owners to connect their store to WooCommerce.com for marketplace features. For stores that don't need the marketplace connection, this feature removes the notice, eliminating the persistent admin clutter.

## Why You Need It

The 'Connect your store' notice is a persistent admin reminder that appears on every WooCommerce admin page. For stores that don't need the marketplace connection, the notice is just clutter. Removing it improves the admin experience without affecting any WooCommerce functionality.

---

## How to Remove the Connect Your Store Notice in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Optimization** subtab.

### Step 3: Enable the Feature

Toggle on **Remove 'Connect your store' notice**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Go to any WooCommerce admin page. The 'Connect your store' notice should not appear.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Remove 'Connect your store' notice** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- The 'Connect your store' notice is hidden on all WooCommerce admin pages
- The admin interface is cleaner
- No functional impact (the connection is still available via the Settings menu)

## What Does NOT Get Affected

- The actual WooCommerce.com connection (if you want to set it up later, the option is in the Settings menu)
- Any WooCommerce functionality (the notice is informational only)
- The customer-facing shop

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Actions:**

- `init` calls `cm_remove_woocommerce_connect_store_notice()` (Removes WooCommerce connect store notice)

```php
// Hooked in woocommerce-functions.php
add_action( 'init', 'cm_remove_woocommerce_connect_store_notice' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Common Use Cases

### Migration from WooCommerce.com

If you're migrating away from WooCommerce.com integrations (e.g., switching to a different payment processor or shipping service), the connection notice is no longer relevant. Disabling it keeps the admin focused on the new integrations. The notice can be re-enabled if you decide to reconnect later.

### Migration or staging sites

For sites that are being migrated or used as staging, the WC.com connection notice is irrelevant. Disabling it cleans up the admin during the migration process.

### Wholesale-only stores

Stores that don't sell through the WC marketplace don't need the connection notice. Removing it is a quick admin win.

### Stores not using WooCommerce.com services

If you don't use the WooCommerce.com marketplace, the connection notice is irrelevant. Removing it reduces admin clutter.

### Independent / standalone stores

Stores that don't integrate with WooCommerce.com don't need the connection notice. Removing it simplifies the admin.

### Custom-built stores

Stores with custom integrations (not via WooCommerce.com) don't need the connection notice. Removing it is a quick admin win.

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
