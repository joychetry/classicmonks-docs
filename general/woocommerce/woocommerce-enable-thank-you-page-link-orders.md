---
title: "How to Access the Thank You Page from a WooCommerce Order"
slug: enable-thank-you-page-link-orders
description: "Open a WooCommerce order's thank you (order received) page from the orders list or order editor with Classic Monks, and preview it as the customer sees it."
last_updated: 2026-08-06
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/enable-thank-you-page-link-orders/
---

# How to Access the Thank You Page from a WooCommerce Order

> Open a WooCommerce order's thank you (order received) page directly from the orders list or the order editor. With Classic Monks, an admin with the right capability can preview the page as the customer sees it, for support and verification.

## Key Takeaways

- Add a thank you page action to the orders list row actions
- Add a thank you page option to the edit-order actions dropdown
- Preview the order received page as the customer sees it
- Requires the ability to edit shop orders
- Excludes cancelled, failed, and trashed orders by default

## What Does the Feature Do?

The default WooCommerce admin gives you order row actions for viewing, editing, and so on, but no quick way to see the customer-facing order confirmation. The **Enable Thank You Page Link in Orders** feature adds two admin shortcuts:

- An **action button** on each row of the orders list
- An entry in the **edit-order actions** dropdown

Both open the order's thank you (order received) page, so you can see exactly what the customer sees after checkout. When the order belongs to a registered customer, the link is built to let an admin with `edit_shop_orders` capability preview the page in the customer's context.

## When to Enable It

Enable it when you need to see the customer-facing order confirmation regularly:

- Support staff checking what a customer saw at checkout
- Confirming an order resolved correctly after payment
- Reviewing the order details and download links on the public page
- Onboarding staff to the customer's checkout experience

Keep it off if you never need the customer-facing page from the order screen.

---

## How to View the WooCommerce Thank You Page from the Order Admin

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Orders** settings area.
3. Toggle on **Enable Thank You Page Link in Orders**.

### Step 2: Save and Open an Order

Click **Save Changes**, then go to **WooCommerce > Orders**.

### Step 3: Use the Row Action

Hover over any order row and click the **Thank You Page** action. The order received page opens in a new tab.

### Step 4: Use the Edit-Order Dropdown

Open an order in the editor, use its **Order actions** dropdown, select **Thank You Page**, and apply it. The page opens for that order.

The preview runs in the customer's context for registered users, so you see the page the way the buyer would.

---

## Configuration Options

| Option | Default |
|--------|---------|
| **Enable Thank You Page Link in Orders** | Off |

There are no nested options. The feature's behavior is determined by the capability check and the excluded-status list.

| Applied rule | Behavior |
|--------------|----------|
| Capability | Only users who can edit shop orders see working preview links. |
| Excluded statuses | Cancelled, failed, and trashed orders do not show the thank you link. |

---

## What Gets Affected

- The orders list: a **Thank You Page** row action is added
- The order editor: a **Thank You Page** action appears in the Order actions dropdown
- The preview: for registered customers, an admin can view the order received page in the customer's context

## What Does NOT Get Affected

- The customer-facing checkout and order received pages: these are unchanged
- Regular order row actions: view, edit, and the default actions stay in place
- Orders in cancelled, failed, or trashed status: no thank you link is added for them
- Non-admins: the customer preview logic only engages for users who can edit shop orders

---

## Advanced Options (Developers)

The feature registers its hooks in `functions/woocommerce/thank-you-page-link.php`, gated on the **Enable Thank You Page Link in Orders** option:

```php
add_filter( 'woocommerce_admin_order_actions', 'cm_add_thank_you_page_action_button', 10, 2 );
add_filter( 'woocommerce_order_actions', 'cm_add_thank_you_order_action_dropdown', 9999, 2 );
add_action( 'woocommerce_order_action_view_thankyou', 'cm_redirect_to_thank_you_from_order_action' );
add_filter( 'determine_current_user', 'cm_admin_becomes_customer_for_thank_you_page', 20 );
add_filter( 'woocommerce_order_received_verify_known_shoppers', '__return_false' );
```

- **`woocommerce_admin_order_actions`** adds the row-action button, and **`woocommerce_order_actions`** (priority 9999) adds the dropdown entry. Both exclude orders in the cancelled, failed, or trash status.
- **`woocommerce_order_action_view_thankyou`** handles the dropdown selection and redirects to the order received page.
- **`determine_current_user`** drives the customer-context preview: when an `adm` parameter matches the order's customer and the user can edit shop orders, it temporarily switches the running user so the page renders as the customer sees it. This runs only on frontend order-received requests.
- **`woocommerce_order_received_verify_known_shoppers`** returns false so the preview does not get blocked by WooCommerce's shopper-verification check.
- The built URL uses the `order-received` endpoint plus the order key, and appends `adm`, `t`, and `oid` for the customer preview. Filters `cm_thank_you_page_url`, `cm_customer_view_thank_you_url`, and `cm_thank_you_page_excluded_statuses` allow customization. The excluded-statuses filter defaults to `array('cancelled', 'failed', 'trash')`.

---

## Troubleshooting

### The thank you link is not showing

**Cause:** The feature toggle is off, or the order is in an excluded status (cancelled, failed, or trashed).
**Fix:** Confirm **Enable Thank You Page Link in Orders** is on. Open an order in a non-excluded status, such as processing or completed.

### The link opens the wrong page or a 404

**Cause:** The order received URL could not be resolved, usually from an order key or permalink issue.
**Fix:** Verify the checkout and order received pages exist under **WooCommerce > Settings > Advanced > Page setup** and that permalinks are set. Test the order's order received URL directly.

### The preview is not showing customer data

**Cause:** The viewer does not have `edit_shop_orders` capability, or the order belongs to a guest with no customer ID to switch to.
**Fix:** Log in as a user who can edit shop orders. For guest orders, the customer-context switch cannot apply, so the preview shows under the current user.

### The link is showing for orders I do not want

**Cause:** By default the link is hidden only for cancelled, failed, and trashed orders.
**Fix:** Narrow the behavior with the `cm_thank_you_page_excluded_statuses` filter to add more statuses to the exclusion list. There is no settings-field control for this; it is a code-level filter.

---

## Frequently Asked Questions

### Where do the thank you links appear?

They appear as a row action on each order in the orders list and as a **Thank You Page** action in the edit-order actions dropdown.

### Can I see the page exactly as the customer does?

For registered customers, yes. When the order has a customer ID and you hold the `edit_shop_orders` capability, the preview temporarily renders the order received page in that customer's context. Guest orders render under the current user.

### Do cancelled or failed orders get a link?

No. By default, cancelled, failed, and trashed orders are excluded, so no thank you link is added for them.

### Does this affect what customers see?

No. The feature only adds admin shortcuts. The public order received page and the checkout flow are unchanged.

### Can any staff member use these links?

The preview context only works for users who can edit shop orders. Other admin roles can still reach the page if WooCommerce lets them, but the customer-context preview requires the capability.

---

## Related Articles

- [How to Add Custom Columns to the WooCommerce Orders Table](woocommerce-enable-custom-order-columns.md)
- [How to Create Custom Order Statuses in WooCommerce](woocommerce-enable-custom-order-status.md)
- [How to Auto-Complete WooCommerce Orders for Digital Products](woocommerce-enable-woocommerce-auto-completion.md)
