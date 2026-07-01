---
title: "How to Enable URL Coupons in WordPress | CM"
slug: enable-url-coupons
description: "Apply WooCommerce coupons via shareable URL parameters in Classic Monks. Supports UTM tracking, source attribution, and customizable redirect destinations."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/enable-url-coupons/
---

# How to Enable URL Coupons in WordPress

> Enable URL Coupons lets customers apply coupons via a shareable URL parameter. Perfect for email campaigns, affiliate links, and marketing automation with UTM tracking and source attribution.

## Key Takeaways

- Single toggle, master switch for the feature
- 2 sub-options: track source, support UTM parameters
- URL format: `?coupon=CODE` automatically applies the coupon
- Supports UTM tracking (`?utm_source=email`) for marketing attribution
- Customizable redirect destination (cart, checkout, or shop page)

## What Is the Enable URL Coupons feature?

By default, customers must enter a coupon code at checkout manually. The Enable URL Coupons feature lets customers receive a URL with the coupon code as a parameter, which is automatically applied when they visit:

`https://yoursite.com/cart/?coupon=SUMMER10`

The feature also supports UTM parameters for marketing attribution, so the URL `https://yoursite.com/cart/?coupon=SUMMER10&utm_source=email&utm_campaign=july4` applies the coupon and tracks the source as "email / july4".

## Why You Need It

URL-based coupons are a powerful marketing tool:

- **Email campaigns**: Include the URL in emails for one-click discount application
- **Affiliate links**: Affiliates can share URLs that auto-apply their custom coupons
- **Social media**: Share URLs on social platforms that auto-apply the coupon
- **QR codes**: Physical marketing materials with QR codes for in-store promotions

For most stores, URL coupons are a small but high-ROI feature.

---

## How to Enable URL Coupons in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Coupons** subtab.

### Step 3: Enable URL Coupons

Toggle on **Enable URL Coupons**. Nested options expand.

### Step 4: Configure Sub-Options

The 2 sub-options include:

- **Track Coupon Sources**: Record the source of the URL for analytics
- **Support UTM Parameters**: Pass UTM parameters through to the redirect URL

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Create URL Coupons

Use the URL format `https://yoursite.com/cart/?coupon=CODE` where `CODE` is the actual coupon code. Add UTM parameters as needed.

### Step 7: Test

Click a URL coupon in a private/incognito browser. The coupon should be applied automatically.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable URL Coupons** | Master toggle. | Off |
| **Track Coupon Sources** | Record source for analytics. | Off |
| **Support UTM Parameters** | Pass UTM through to redirect. | Off |
| **Default Redirect After** | (configured in URL Coupons meta) | Cart page |
| **URL Parameter Name** | (configured in URL Coupons meta) | "coupon" |

The Default Redirect After and URL Parameter Name are configured in the URL Coupons metabox (when editing the URL Coupons post type).

---

## What Gets Affected

- The cart: the coupon is applied when the URL is visited
- The redirect: the customer is sent to the configured page (cart, checkout, or shop)
- The analytics: the source is recorded (if Track Coupon Sources is enabled)
- The UTM parameters: passed through to the redirect URL (if Support UTM Parameters is enabled)

## What Does NOT Get Affected

- Manual coupon code entry: customers can still enter codes manually
- Coupon eligibility: determined by the coupon's existing restrictions
- The coupon's effect on the order: the URL-applied discount is the same as a manually-applied one
- The order meta: the source and UTM are stored separately (if enabled)

---

## Advanced Options (Developers)

This feature registers 3 WordPress hooks in `url-coupons.php`:

**Actions:**

- `template_redirect` calls `cm_process_url_coupon()` (Processes URL coupon activation (priority 20))
- `wp_enqueue_scripts` calls `cm_url_coupons_enqueue_scripts()` (Enqueues URL coupon scripts)
- `add_meta_boxes` calls `cm_add_url_coupon_meta_box()` (Adds URL coupon metabox to coupons)

```php
// Hooked in url-coupons.php
add_action( 'template_redirect', 'cm_process_url_coupon' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The URL coupon is not being applied

**Cause:** The toggle is off, the coupon doesn't exist, or the URL is malformed.
**Fix:** Verify the toggle is on. Verify the coupon code exists in WooCommerce > Coupons. Verify the URL format is `?coupon=CODE` (case-sensitive).

### The customer is redirected but the coupon is not applied

**Cause:** The redirect happened before the coupon was applied, or the coupon's conditions are not met.
**Fix:** Verify the cart meets the coupon's conditions. The redirect happens after the coupon is applied; if the coupon fails (e.g., minimum spend not met), the redirect still happens but the coupon is not in the cart.

### The UTM parameters are not being tracked

**Cause:** The "Support UTM Parameters" option is off, or the parameters are not in the URL.
**Fix:** Verify the option is on. Verify the URL includes the UTM parameters (e.g., `?coupon=CODE&utm_source=email`).

### The source is not recorded in the order

**Cause:** The "Track Coupon Sources" option is off.
**Fix:** Verify the option is on. The source is stored as order meta. Configure in the plugin settings to customize the data being stored.

---

## Related Articles

- [How to Enable Maximum Discount Amount in WordPress](woocommerce-enable-coupon-max-discount.md)
- [How to Enable Auto-Apply Coupons in WordPress](woocommerce-enable-auto-apply-coupons.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
