---
title: "How to Disable WooCommerce Status Meta Box in WordPress | CM"
slug: disable-woocommerce-status-meta-box
description: "Remove the WooCommerce status widget from the WordPress admin dashboard. Simplifies the admin interface by removing WooCommerce-specific widgets."
last_updated: 2026-06-24
author: Joy
reading_time: 2 min
canonical: https://classicmonks.com/docs/disable-woocommerce-status-meta-box/
---

# How to Disable WooCommerce Status Meta Box in WordPress

> Disable the WooCommerce status meta box in the WordPress admin dashboard to simplify the admin interface for sites where WooCommerce is not the primary focus.

## Key Takeaways

- Single toggle, no nested options
- Simplified admin dashboard for non-WooCommerce-focused sites
- Faster dashboard load time (one less widget to render)
- Cleaner admin interface for users who don't need WooCommerce data on the dashboard

## What Is the Disable WooCommerce status meta box feature?

WordPress's admin dashboard includes a WooCommerce status widget that shows recent orders, sales summary, and other WooCommerce-specific information. For sites where WooCommerce is not the primary function (e.g., a blog with a small shop), this widget adds clutter to the dashboard. This feature removes the WooCommerce status widget from the dashboard.

## Why You Need It

For sites where WooCommerce is not the primary function, the WooCommerce status widget adds clutter to the admin dashboard. The same information is available in the WooCommerce Reports area, so removing the widget from the dashboard simplifies the admin interface without losing access to the data.

---

## How to Disable WooCommerce Status Meta Box in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Optimization** subtab.

### Step 3: Enable the Feature

Toggle on **Disable WooCommerce status meta box**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Go to the WordPress admin dashboard. The WooCommerce status widget should not be visible.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable WooCommerce status meta box** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- The WooCommerce status widget is hidden on the admin dashboard
- The dashboard loads faster (one less widget)
- The admin interface is cleaner for non-WooCommerce-focused sites

## What Does NOT Get Affected

- The WooCommerce Reports area (where the data is available in detail)
- The WooCommerce admin menu (the menu items still appear)
- The WooCommerce data (orders, products, etc.)

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Actions:**

- `wp_dashboard_setup` calls `cm_disable_woocommerce_status_meta_box()` (Removes WooCommerce status dashboard widget)

```php
// Hooked in woocommerce-functions.php
add_action( 'wp_dashboard_setup', 'cm_disable_woocommerce_status_meta_box' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Common Use Cases

### Custom Admin Dashboard Widgets

For stores that have built their own custom dashboard widgets (e.g., custom sales reports, support ticket summaries, social media feeds), the WC status widget is redundant. Removing it provides more visual real estate for the custom widgets. Use a custom plugin to hide the WC widget and add your own in its place.

### Many admin users

For stores with many admin users (e.g., agencies, multi-staff stores), the WC status widget loads for every admin login. Disabling it speeds up logins.

### Multi-vendor stores

Multi-vendor stores have their own vendor dashboards. The WC status widget is redundant.

### B2B-only stores

B2B stores have custom reporting. The WC status widget is rarely used.

### Multi-author blogs with a small shop

When the shop is a secondary feature, the WooCommerce status widget adds clutter to the dashboard for non-shop users.

### High-volume stores with custom reports

Stores that have their own reporting (custom dashboards, third-party analytics) don't need the WooCommerce widget.

### Simplified admin for clients

Client sites benefit from a clean dashboard. Removing the widget reduces the learning curve for non-technical users.

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
