---
title: "How to Turn Off the Built-in WooCommerce Widgets You Skip"
slug: disable-woocommerce-widgets
description: "Remove WooCommerce's built-in cart, product, filter, and review widgets together. Keep the available widgets focused with a single Classic Monks toggle."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-woocommerce-widgets/
---

# How to Turn Off the Built-in WooCommerce Widgets You Skip

> Remove WooCommerce's built-in widgets from the widget admin so only the areas you use remain. Classic Monks disables the cart, product, filter, and review widgets in one toggle.

## Key Takeaways

- Unregister WooCommerce's built-in widgets together
- Disable the cart, products, filters, reviews, and related widgets
- Preserve widgets that are actively used if you choose not to
- One toggle, no nested options
- Clean up the widget admin and widget areas

## What Does the Feature Do?

WooCommerce registers a set of widgets for the cart, product lists, filters, reviews, and related content. The **Disable All WooCommerce Widgets** feature unregisters these built-in widgets, so they no longer appear in the widget admin or render in your sidebars.

When enabled, the built-in WooCommerce widgets are removed as a group. The store and its widgets' data are unaffected; the widgets just stop being available.

## Why You Need It

The default store widgets may not fit every layout:

- A design may not use product filter, cart, or review widgets
- Removing unneeded widgets keeps the widget selection focused
- It reduces the number of widget blocks available in page builders
- Sites that rely on custom sidebars keep only the widgets they use

---

## How to Disable All WooCommerce Widgets

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Optimization** settings area.
3. Toggle on **Disable All WooCommerce Widgets**.

### Step 2: Save and Test

Click **Save Changes**. Open **Appearance > Widgets** and confirm the WooCommerce widgets no longer appear among the available widgets.

---

## Configuration Options

| Option | Default |
|--------|---------|
| **Disable All WooCommerce Widgets** | Off |

There are no nested options. The feature is a single on/off control.

---

## What Gets Affected

- WooCommerce's built-in widgets: unregistered from the widget system
- The widget admin: the disabled widgets no longer appear
- Widget areas that used them: those widgets stop rendering

## What Does NOT Get Affected

- WooCommerce products, cart, and orders: fully functional
- Custom widgets from themes or other plugins: unaffected
- Any widgets currently in use on a sidebar if this is toggled on: they are no longer available for new placements

---

## Advanced Options (Developers)

The feature is wired in `functions/woocommerce/woocommerce-functions.php`:

```php
add_action( 'widgets_init', 'cm_disable_woocommerce_widgets' );
```

**`widgets_init`** calls `cm_disable_woocommerce_widgets()`, which unregisters the built-in WooCommerce widget classes, including the cart, products, layered/nav filter, price filter, rating filter, recent reviews, product search, recently viewed, tag cloud, categories, top rated, and layered/nav filter widgets.

---

## Common Use Cases

**Clean widget admin.** Stores that do not use filter or review widgets get a focused widget selection.

**Custom sidebar designs.** Layouts built with specific widgets only keep the widgets they actually place.

**Lightweight themes.** Simpler themes benefit from not exposing the full WooCommerce widget set.

---

## Troubleshooting

### Widgets are still showing

**Cause:** The toggle is off, or a theme re-registers the widget classes.
**Fix:** Confirm the toggle is on. If a theme or plugin re-registers the same widget classes, those appear independently.

### Removing a widget I use

**Cause:** The toggle unregisters all built-in WooCommerce widgets together.
**Fix:** Only enable the toggle if you do not need the built-in widget set. For individual control, use WooCommerce or theme widget management instead.

### The cart or products still appear

**Cause:** Those may come from a theme block or shortcode rather than the widget.
**Fix:** Widgets and shortcode/block-based output are different. Disabling widgets does not prevent shortcode or block markup from appearing where it is placed.

---

## Frequently Asked Questions

### Which widgets are disabled?

The built-in WooCommerce widgets: cart, products, layered/nav filter, price filter, rating filter, recent reviews, product search, recently viewed, tag cloud, categories, top rated, and layered/nav filter. These are unregistered together.

### Does it remove active sidebar widgets?

The feature unregisters the widget classes, so widgets already placed are no longer available to render and cannot be placed anew. This is a global action.

### Does it affect the store?

No. Products, cart, orders, and checkout work normally. Only the widget availability changes.

### Can I restore them?

Yes. Disable the toggle to re-register the WooCommerce widgets.

---

## Keeping It Set Up

Set the toggle once and it stays active across the site. To change behavior, return to the WooCommerce settings, adjust the option, and save again. The store continues to run normally throughout, and you can turn the feature off at any time to restore the previous default behavior. For teams managing multiple environments, confirm the setting on staging first, then apply it to production and verify a real page load before treating it as live.

---

## Related Articles

- [How to Disable WooCommerce Scripts and Styles on Non-WooCommerce Pages](woocommerce-disable-woocommerce-scripts.md)
- [How to Disable WooCommerce Blocks Styles](woocommerce-disable-woocommerce-blocks-styles.md)
- [How to Remove All WooCommerce Notices](woocommerce-remove-all-woocommerce-notices.md)
