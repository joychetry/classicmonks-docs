---
title: "How to Remove All WooCommerce Notices in WordPress | CM"
slug: remove-all-woocommerce-notices
description: "Suppress all WooCommerce admin notices. Provides the cleanest admin interface for stores that don't need WooCommerce's promotional or informational content."
last_updated: 2026-06-24
author: Joy
reading_time: 2 min
canonical: https://classicmonks.com/docs/remove-all-woocommerce-notices/
---

# How to Remove All WooCommerce Notices in WordPress

> Suppress all WooCommerce admin notices for the cleanest admin interface, eliminating all informational and promotional content from WooCommerce.

## Key Takeaways

- Single toggle, no nested options
- Cleanest admin interface (no WooCommerce notices)
- Reduced admin clutter for established stores
- Faster admin page loads (fewer notices to render)

## What Is the Remove all notices feature?

WooCommerce displays various admin notices for promotions, new features, and informational messages. This feature suppresses all of them, providing the cleanest admin interface. Use this only if you have a stable, well-configured store and don't need WooCommerce's notifications.

## Why You Need It

WooCommerce's admin notices can be helpful for new store owners but are noise for established stores with stable configurations. Removing all notices provides the cleanest admin experience, but you also lose informational messages about updates and issues.

---

## How to Remove All WooCommerce Notices in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Optimization** subtab.

### Step 3: Enable the Feature

Toggle on **Remove all notices**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Go to various WooCommerce admin pages. No notices should be visible.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Remove all notices** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- All WooCommerce admin notices are suppressed
- The admin interface is the cleanest possible
- Faster admin page loads

## What Does NOT Get Affected

- Critical error messages (these are still shown; the feature only suppresses informational notices)
- WooCommerce's core functionality (orders, products, etc.)
- The customer-facing shop

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Actions:**

- `init` calls `cm_remove_all_woocommerce_notices()` (Removes all WooCommerce notices)

```php
// Hooked in woocommerce-functions.php
add_action( 'init', 'cm_remove_all_woocommerce_notices' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Common Use Cases

### Production Sites in Maintenance Mode

For sites that are in maintenance mode or have been recently migrated, the WC admin notices may be stale or irrelevant. Disabling them provides a clean admin while the site is being stabilized. Re-enable after the site is fully operational.

### New Staff Onboarding

For stores that frequently onboard new staff, the WC admin notices can be confusing. New staff may think notices are errors or warnings about the site. Removing all notices provides a clean admin that's easier to learn. Use the WooCommerce status report (WooCommerce > Status) for actual diagnostics.

### Headless e-commerce

If your store uses a custom frontend (Next.js, Gatsby, custom React) with WordPress as a backend, WC admin notices are irrelevant. Disabling them keeps the admin focused on data management.

### Multi-store networks

Network sites that have multiple stores may have stable configurations. Notices are noise across the network.

### Compliance-required admin

Stores that must keep the admin interface minimal for compliance or accessibility reasons can disable all notices.

### Established stores with stable config

Stores that have been configured for a long time don't need WooCommerce's notices. Removing them reduces admin clutter.

### High-volume admin workflows

For staff processing many orders, every admin interaction counts. Removing notices speeds up the workflow.

### Client sites

Client sites benefit from a clean admin. The fewer notices, the more confidence the client has in the site stability.

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
