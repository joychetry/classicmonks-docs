---
title: "How to Turn Off WooCommerce Marketplace Suggestions"
slug: disable-marketplace-suggestions
description: "Stop WooCommerce from showing marketplace extension suggestions in the admin. Remove the promotional prompts you do not need with a Classic Monks toggle."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-marketplace-suggestions/
---

# How to Turn Off WooCommerce Marketplace Suggestions

> Stop WooCommerce from showing marketplace extension suggestions in the admin dashboard. Classic Monks turns off the promotional suggestions so the admin stays focused.

## Key Takeaways

- Disable WooCommerce marketplace suggestions
- Hide the extension recommendation prompts in the admin
- One toggle, no nested options
- Does not affect the store or its extensions
- Reduce admin clutter from promotional suggestions

## What Does the Feature Do?

WooCommerce recommends extensions from its marketplace through in-admin suggestions. The **Disable Marketplace Suggestions** feature suppresses those recommendations, so the admin no longer shows the promotional suggestion prompts.

Existing extensions and Marketplace access are unaffected. The feature only hides the suggestion prompts WooCommerce would otherwise display.

## Why You Need It

Marketplace suggestions can be an unwelcome distraction:

- Promotional prompts add noise to the admin
- Not every store plans to extend through the marketplace
- Removing them keeps staff focused on orders and products
- The marketplace connection remains available if you want it later

---

## How to Disable Marketplace Suggestions

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Optimization** settings area.
3. Toggle on **Disable Marketplace Suggestions**.

### Step 2: Save and Test

Click **Save Changes**. Reload the WooCommerce admin and confirm the marketplace suggestion prompts no longer appear.

---

## Configuration Options

| Option | Default |
|--------|---------|
| **Disable Marketplace Suggestions** | Off |

There are no nested options. The feature is a single on/off control.

---

## What Gets Affected

- The admin: WooCommerce marketplace suggestions are suppressed

## What Does NOT Get Affected

- Installed WooCommerce extensions: these remain active
- The Marketplace connection: still available in the admin
- Products, orders, and shop functions: unchanged

---

## Advanced Options (Developers)

The feature registers one hook in `functions/woocommerce/woocommerce-functions.php`:

```php
add_filter( 'woocommerce_allow_marketplace_suggestions', '__return_false', 999 );
```

**`woocommerce_allow_marketplace_suggestions`** returns false at priority 999 when the feature is enabled, which disables the marketplace suggestion prompts.

---

## Common Use Cases

**Focused admin.** Stores that do not plan marketplace extensions benefit from a quieter admin.

**Lean teams.** Teams managing the store through orders and products skip the promotional prompts.

**Custom tooling.** When the stack is built from a specific set of extensions, suggestion prompts are irrelevant.

---

## Troubleshooting

### Suggestions are still showing

**Cause:** The toggle is off, or a WooCommerce update re-enables suggestion prompts by another path.
**Fix:** Confirm the toggle is on and clear caches. If suggestions are shown from a different source (for example, a themes or extensions promo), check that source separately.

### Installing extensions still works

**Cause:** Disabling suggestions does not block the marketplace.
**Fix:** Confirm the toggle only hides prompts. Extensions can still be added manually or via the marketplace.

---

## Frequently Asked Questions

### What exactly is suppressed?

WooCommerce's in-admin marketplace suggestion prompts that recommend extensions are hidden when the feature is on.

### Can I still add extensions?

Yes. Disabling suggestions does not block installing extensions, either manually or from the marketplace.

### Does this affect the store?

No. Products, orders, and shop functions are unchanged.

---

## Keeping It Set Up

Set the toggle once and it stays active across the site. To change behavior, return to the WooCommerce settings, adjust the option, and save again. The store continues to run normally throughout, and you can turn the feature off at any time to restore the previous default behavior. For teams managing multiple environments, confirm the setting on staging first, then apply it to production and verify a real page load before treating it as live.

---

## Market Place Access Still Available

The toggle only hides the suggestion prompts. You can still open the WooCommerce marketplace, install extensions, and manage your existing plugins at any time. The feature does not block any part of the marketplace itself, so nothing is lost by turning suggestions off. If you later decide to see suggestions again, switch the toggle back on and they return. For a store that has already chosen its extension stack, keeping this on removes a source of admin noise without affecting functionality.

---**Compare before changing.** The feature affects only the suggestion prompts, so there is no functional downside to enabling it on a store that already has its extensions chosen. Teams that prefer a strictly promotional-free admin often keep this on permanently. A quick test on a staging site confirms that the marketplace and installed extensions continue to work, which is useful before applying the change to a production environment.

---

## Related Articles

- [How to Disable WooCommerce Admin Features](woocommerce-disable-woocommerce-admin-features.md)
- [How to Remove All WooCommerce Notices](woocommerce-remove-all-woocommerce-notices.md)
- [How to Disable WooCommerce Scripts and Styles on Non-WooCommerce Pages](woocommerce-disable-woocommerce-scripts.md)
