---
title: "How to Enable WooCommerce Direct Checkout Links in WordPress"
slug: enable-woocommerce-direct-checkout
description: "Create WooCommerce direct checkout links that skip the cart and go straight to checkout with a product pre-added. Set quantity from the product edit screen."
last_updated: 2026-08-06
author: Joy
reading_time: 5 min
canonical: https://classicmonks.com/docs/enable-woocommerce-direct-checkout/
---

# How to Enable WooCommerce Direct Checkout Links in WordPress

> WooCommerce direct checkout links skip the cart page and send customers straight to checkout with a product pre-added. Generate them from the product edit screen, set a fixed or custom quantity, and use them in email campaigns, affiliate links, and landing pages to cut checkout friction.

## Key Takeaways

- Generate a direct checkout link for any published, purchasable product
- Links clear the customer's cart and add the selected product with a chosen quantity
- Set a global maximum quantity limit to control bulk orders
- Copy or test links directly from the **Direct Checkout Link** product sidebar metabox
- Use links in email, social, affiliate, and QR-code campaigns to reduce checkout steps
- Forwards coupon, UTM, and affiliate query parameters to the checkout page

## What Is WooCommerce Direct Checkout Links?

By default, clicking **Add to Cart** leaves customers on the product page or the cart page, and a "Buy Now" flow usually still requires landing on the product page first. The Classic Monks **Enable WooCommerce Direct Checkout Links** feature removes those intermediate steps. Each published product gets a generated checkout URL in its edit screen. When a customer clicks it, their cart is cleared and the product is added with the specified quantity, then they are redirected straight to the checkout page, so the entire purchase is a "skip cart" buy-now flow.

A direct checkout URL uses the checkout page with three parameters:

```
https://yoursite.com/checkout/?direct=1&product_id=456&quantity=3
```

- `direct=1` signals Classic Monks to process the link
- `product_id=456` is the product to add
- `quantity=3` is how many to add (defaults to 1)

You do not hand-write these URLs. The plugin generates them for you in a **Direct Checkout Link** metabox on each product's edit screen, with a **Copy Link** button for convenience.

## Why You Need It

Direct checkout links remove an entire step from the purchasing journey:

- **Email campaigns.** A newsletter "Buy Now" button that lands on a product page needs a second click to add to cart. A direct checkout link skips both.
- **Affiliate and influencer links.** Affiliates can send traffic straight to checkout with the right product pre-added, lifting conversion rates on shared links.
- **Landing pages.** Campaign-specific landing pages can deep-link to checkout so the visitor never has to search for the product.
- **QR codes.** Business cards, flyers, and packaging QR codes can point to a direct checkout link.
- **Coupon and campaign tracking.** Any coupon codes, UTM parameters, or affiliate IDs appended to the link are forwarded to the checkout page, so tracking still works.

For stores running email and paid-social campaigns, this is a measurable conversion improvement: every skipped page is a skipped chance to abandon.

---

## How to Enable WooCommerce Direct Checkout Links in WordPress

### Step 1: Enable the Feature

1. Open **Classic Monks** in your WordPress admin sidebar.
2. Open the **WooCommerce** tab.
3. Open the **One Click Checkout** subtab.
4. Toggle on **Enable WooCommerce Direct Checkout Links**. The nested options expand below the toggle.

### Step 2: Set the Quantity Options

- **Show Custom Quantity Generator** (On by default) shows a quantity box in the product's **Direct Checkout Link** metabox so you can generate links for quantities other than 1. Turn it off to always generate links for a quantity of 1.
- **Maximum Quantity Limit** sets the global cap for custom-quantity links. The effective limit for any product is the lower of this global value and the product's own maximum purchase quantity.

### Step 3: Save Changes

Click **Save Changes** in the Classic Monks settings toolbar.

### Step 4: Generate a Direct Checkout Link

1. Edit a **published** product in **WooCommerce > Products**.
2. In the sidebar, find the **Direct Checkout Link** metabox. Direct checkout links are only available for published, purchasable products, so the metabox shows a note for drafts or unpurchasable items.
3. If **Show Custom Quantity Generator** is on, enter the quantity you want (capped at **Maximum Quantity Limit**).
4. The URL is generated automatically in the metabox text area.
5. Click **Copy Link** to copy it to your clipboard, or **Test Link** to open it in a new tab.

### Step 5: Use the Link

Paste the link into your email campaign, affiliate dashboard, social post, or QR code. When a customer clicks it, the link clears any existing cart contents, adds the product, and redirects to checkout.

---

## Configuration Options

| Option | Behavior | Default |
|--------|----------|---------|
| **Enable WooCommerce Direct Checkout Links** | Master toggle for the whole feature. | Off |
| **Show Custom Quantity Generator** | Shows a quantity input in the product metabox for generating links with a custom quantity; off forces quantity 1. | On |
| **Maximum Quantity Limit** | Global cap on the quantity used in generated links (1-9999). The effective limit is the lower of this value and the product's max-purchase quantity. | 999 |

---

## What Gets Affected

- The product edit screen: a **Direct Checkout Link** sidebar metabox appears on published products
- Checkout behavior: a URL with `direct=1` clears the cart, adds the product, and redirects to checkout
- Query parameters: `direct`, `product_id`, and `quantity` are consumed; all other parameters (coupons, UTM, affiliate IDs) are forwarded to checkout
- The cart: existing contents are cleared before the direct-checkout product is added

## What Does NOT Get Affected

- The standard **Add to Cart** button on product and archive pages (unchanged)
- The cart and checkout pages for normal shopping (a direct checkout only triggers when `direct=1` is in the URL)
- Product stock and inventory rules (standard WooCommerce limits and stock status still apply)
- The SKU (the feature uses product ID, not SKU, as its identifier)

---

## Advanced Options (Developers)

The feature registers three hooks in `functions/woocommerce/one-click-checkout/direct-checkout-link.php`:

```php
add_action( 'wp_loaded', array( $this, 'process_direct_checkout' ), 5 );
add_action( 'add_meta_boxes', array( $this, 'add_direct_checkout_metabox' ) );
add_action( 'admin_enqueue_scripts', array( $this, 'enqueue_admin_assets' ) );
```

- **`wp_loaded`** (priority 5) runs `process_direct_checkout()`, which reads the `direct`, `product_id`, and `quantity` parameters, validates the product and quantity limits, clears the cart, adds the product, and safely redirects to checkout.
- **`add_meta_boxes`** registers the **Direct Checkout Link** metabox on the product edit sidebar.
- **`admin_enqueue_scripts`** loads the metabox CSS and JS only on product edit screens for users who can edit products.

There is also a public helper for theme and plugin developers:

```php
// Generate a direct checkout URL for product 456 with a quantity of 3
$url = cm_get_direct_checkout_url( 456, 3 );
```

This returns `wc_get_checkout_url()` with the `direct`, `product_id`, and `quantity` parameters appended. It is a shortcut to `CM_Direct_Checkout_Link::generate_checkout_url()`.

---

## Frequently Asked Questions

### Does a direct checkout link clear the cart or add to it?

It clears the cart. When a customer clicks a direct checkout link, Classic Monks empties the existing cart and adds only the product specified in the link with the given quantity, then redirects to checkout. This is a buy-now flow, not an add-to-cart flow.

### Do I need to write the URL by hand?

No. Classic Monks generates each link for you in the **Direct Checkout Link** sidebar metabox on the product edit screen, with a **Copy Link** button. The URL uses the `direct=1`, `product_id`, and `quantity` parameters automatically.

### Will coupons and tracking parameters survive a direct checkout?

Almost all of them. The `direct`, `product_id`, and `quantity` parameters are consumed, but any other query parameters (coupon codes, UTM parameters, affiliate IDs) are forwarded to the checkout URL, so campaign tracking still works.

### Can I make a direct checkout link for more than one item?

The link supports a single product with a quantity. Use the quantity box in the metabox (when **Show Custom Quantity Generator** is on) to set how many of that product to add. It is capped by **Maximum Quantity Limit** and the product's own max-purchase limit.

### Is direct checkout the same as a WooCommerce redirect plugin?

WooCommerce direct checkout is the same intent: skip the cart and go straight to checkout. Classic Monks implements it as a generated link per product rather than changing every **Add to Cart** button, so it works for buy-now campaigns and checkout links without altering the standard storefront flow.

## Common Use Cases

**Email and newsletter campaigns.** Put a direct checkout link behind every "Buy Now" call-to-action in your campaigns. Users land on checkout with the featured product pre-added, eliminating clicks and drop-off between the email and the order.

**Affiliate and influencer programs.** Hand affiliates a stable direct checkout link per product. Because the quantity and product are baked into the URL, you can trust that every click converts the intended item without manual cart work.

**QR codes on packaging and print.** Link a printed QR code straight to checkout for a product. A shopper scans, lands on checkout with the item ready, and completes the order on their phone.

**Flash sales and hot drops.** When you need to sell a specific SKU fast, share a direct checkout link on social channels. Every visitor who taps the link is one click away from paying.

**Replenishment and subscription-style purchases.** Use a fixed-quantity direct checkout link (for example, quantity 6) so repeat buyers can restock a standard quantity in one tap.

---

## Troubleshooting

### The direct checkout link does nothing

**Cause:** The feature is off, the link is missing the `direct=1` parameter, or a request-caching layer is caching the checkout page.
**Fix:** Confirm **Enable WooCommerce Direct Checkout Links** is on. Verify the link contains `direct=1&product_id=<id>&quantity=<n>`. Purge any full-page cache or CDN cache on the checkout URL, then test with the **Test Link** button in the product metabox.

### The customer lands on the cart page instead of checkout

**Cause:** Another plugin or theme callback intercepts the checkout redirect.
**Fix:** Test a freshly generated link from the metabox. Temporarily disable other cart- or checkout-redirect plugins to isolate the conflict. The redirect uses `wp_safe_redirect`, so an alternate plugin that runs after it could override the destination.

### The product is not added to the cart

**Cause:** The product is unpurchasable or out of stock, or another plugin cleared the cart after the feature added the product.
**Fix:** Confirm the product is published, purchasable, and in stock. Check for a plugin that empties the cart (for example, a "delete all on X" rule) running on `wp_loaded` after priority 5. Test with a known in-stock product.

### The quantity is capped at a number I didn't set

**Cause:** The product's own maximum purchase quantity is lower than the global **Maximum Quantity Limit**.
**Fix:** The effective cap is `min(product_max_purchase_quantity, admin_max_quantity)`. Raise the per-product max-purchase limit in WooCommerce product data, or accept the lower cap.

### I want a link for a product but the metabox is empty

**Cause:** The metabox only renders for published, purchasable products, and only for users who can edit products.
**Fix:** Publish the product and confirm it is set to a purchasable type (simple, variable, group, and so on). Confirm your user role has the `edit_products` capability.

---

## Related Articles

- [How to Add a Product Selector to the WooCommerce Checkout in WordPress](woocommerce-enable-checkout-product-selector.md)
- [How to Show Custom Quantity Generator in WordPress](woocommerce-show-custom-quantity-generator.md)
- [How to Auto Select the First Variation in WordPress](woocommerce-auto-select-first-variation.md)
