---
title: "How to Offer Rewards to New Customers in WooCommerce"
slug: enable-first-time-customer-coupons
description: "Automatically reward first-time customers with a welcome coupon in WooCommerce. Set the discount type, trigger, validity, and a personalized welcome email."
last_updated: 2026-08-06
author: Joy
reading_time: 6 min
canonical: https://classicmonks.com/docs/enable-first-time-customer-coupons/
---

# How to Offer Rewards to New Customers in WooCommerce

> First-time customer coupons automatically generate a welcome discount for new shoppers and send it by email. Configure the discount type and amount, choose what triggers it, control how long it stays valid, and generate a unique code per customer.

## Key Takeaways

- Detect new customers and reward them with a welcome coupon
- Choose the discount type (percentage, fixed cart, fixed product, or free shipping)
- Pick the trigger: registration, first visit, first item added, or email signup
- Optionally send a personalized welcome email and generate one unique code per customer
- Control validity period, minimum spend, and whether sale items are excluded

## What Are First-Time Customer Coupons?

WooCommerce does not detect first-time shoppers on its own. The Classic Monks **Enable First-Time Customer Coupons** feature identifies new customers, generates a welcome coupon for them, and (optionally) emails it with instructions.

The feature monitors customer history and purchase behavior to decide whether someone is new, then creates a personalized coupon code with a configurable validity period. Detection works for registered users via their account and email, for guests via their email and order history, and optionally via browser cookies or IP.

## Why You Need It

A first-purchase incentive is one of the highest-ROI acquisition levers:

- **Convert curious visitors.** A welcome discount tips a first-time shopper who is still deciding.
- **Build loyalty from day one.** A personal welcome email sets the tone for the relationship.
- **Reduce first-order abandonment.** Discounting the first purchase lowers the "sticker shock" barrier.
- **Automate the sequence.** Once configured, welcome coupons and emails generate without manual work.

---

## How to Offer Rewards to New Customers in WooCommerce

### Step 1: Enable the Feature

1. Open **Classic Monks** in your WordPress admin sidebar.
2. Open the **WooCommerce** tab.
3. Open the **Coupons** subtab.
4. Toggle on **Enable First-Time Customer Coupons**. The nested options expand below the toggle.

### Step 2: Configure the Welcome Coupon

- **Welcome Coupon Type** selects the discount kind: **Percentage Discount** (default), **Fixed Cart Discount**, **Fixed Product Discount**, or **Free Shipping**.
- **Welcome Coupon Amount** (default 10) sets the discount value. For a percentage type this is a percent; for fixed types it is an amount. The field is hidden when the type is **Free Shipping**.

### Step 3: Choose the Trigger

- **Trigger Event** decides when a welcome coupon is generated:
  - **Account Registration** (default) fires when a new account is created.
  - **First Website Visit** fires on a visitor's first site visit.
  - **First Item Added to Cart** fires when a first-time shopper adds their first item.
  - **Email Newsletter Signup** fires on a newsletter signup.

### Step 4: Set Validity and Minimum

- **Coupon Validity Period** controls how long the coupon stays valid after generation: 7, 14, 30 (default), 60, or 90 days, or **No Expiration**.
- **Minimum Order Amount** sets a spend threshold to use the coupon (default 0, which means no minimum).

### Step 5: Configure the Welcome Email

- **Send Welcome Email** (On by default) emails the coupon to the new customer.
- **Email Subject** (default `Welcome! Here's your exclusive discount`) sets the subject line.
- **Email Message** (default `Thank you for joining us! Use code {coupon_code} to get {discount_amount} off your first order.`) sets the body. Use the placeholders `{coupon_code}`, `{discount_amount}`, and `{customer_name}`.

### Step 6: Configure Code and Exclusion Options

- **Generate Unique Coupon Codes** (On by default) creates a separate code for each customer to prevent sharing and track usage.
- **Exclude Sale Items** (Off by default) prevents the welcome coupon from applying to products already on sale.

### Step 7: Save Changes and Test

Click **Save Changes** in the Classic Monks settings. Register a new account, confirm a unique welcome coupon is generated, and verify the welcome email arrives with the code.

---

## Configuration Options

| Option | Behavior | Default |
|--------|----------|---------|
| **Enable First-Time Customer Coupons** | Master toggle for the feature. | Off |
| **Welcome Coupon Type** | Percentage, Fixed Cart, Fixed Product, or Free Shipping. | Percentage Discount |
| **Welcome Coupon Amount** | Discount value (percent or fixed depending on type); hidden for Free Shipping. | 10 |
| **Trigger Event** | Account Registration, First Website Visit, First Item Added to Cart, or Email Newsletter Signup. | Account Registration |
| **Coupon Validity Period** | 7, 14, 30, 60, 90 days, or No Expiration. | 30 days |
| **Minimum Order Amount** | Minimum spend to use the coupon (0 = none). | 0 |
| **Send Welcome Email** | Email the coupon to the customer. | On |
| **Generate Unique Coupon Codes** | One unique code per customer. | On |
| **Exclude Sale Items** | Prevent use on items already on sale. | Off |

Per-coupon, **Email Subject** and **Email Message** are set below **Send Welcome Email** when it is on.

---

## What Gets Affected

- New-customer detection: the feature watches registration, visits, cart additions, and signups per the trigger
- Coupon generation: a welcome coupon is created for identified first-time customers, with a unique code if enabled
- Email delivery: a welcome email with the code is sent when **Send Welcome Email** is on
- Coupon usage: the generated code counts against its usage limit and the customer's order

## What Does NOT Get Affected

- Existing customers: returning shoppers are not given the first-time coupon
- Manually created coupons: the welcome sequence runs independently of your normal coupon library
- Products and pricing: the coupon only adds a discount when applied at checkout
- Sale items: only excluded if **Exclude Sale Items** is on

---

## Advanced Options (Developers)

The feature registers its hooks in `functions/woocommerce/coupons/first-time-customer-coupons.php`:

```php
// Depending on the trigger event:
add_action( 'woocommerce_created_customer', 'cm_handle_customer_registration', 10, 3 );
add_action( 'user_register', 'cm_handle_user_registration' );
add_action( 'init', 'cm_handle_first_visit' );
add_action( 'woocommerce_add_to_cart', 'cm_handle_first_cart_addition', 10, 6 );
add_action( 'mailchimp_signup', 'cm_handle_email_signup' );
add_action( 'newsletter_signup', 'cm_handle_email_signup' );

add_action( 'admin_menu', 'cm_add_first_time_customer_admin_menu' );
add_action( 'wp_ajax_cm_generate_welcome_coupon', 'cm_ajax_generate_welcome_coupon' );
add_action( 'wp_ajax_cm_get_customer_history', 'cm_ajax_get_customer_history' );
```

- Which registration/visit/cart/signup hooks are registered depends on the configured **Trigger Event**.
- **`woocommerce_created_customer`** and **`user_register`** fire on account registration (10, 3 args).
- **`init`** tracks the first visit; **`woocommerce_add_to_cart`** tracks first cart addition.
- `mailchimp_signup` and `newsletter_signup` support the email-signup trigger.
- Admin AJAX endpoints handle manual welcome-coupon generation and customer history lookup.
- Expired welcome coupons are cleaned up via the scheduled `cm_cleanup_expired_welcome_coupons` hook.

---

## Common Use Cases

**First-order welcome offer.** Select **Account Registration** as the trigger and a **Percentage Discount** (for example, 10% or 15%) so every new account gets a first-purchase incentive and email.

**Email capture growth.** Use **Email Newsletter Signup** as the trigger with a fixed cart discount, turning subscribers into first-time buyers and growing your list at the same time.

**Cart-saving nudges.** Set **First Item Added to Cart** as the trigger with a short validity (for example, 17 days) so the offer feels timely and encourages checkout while the interest is fresh.

**Free-shipping welcome.** Choose **Free Shipping** as the welcome coupon type with a **Minimum Order Amount** (for example, $50) to encourage a first order large enough to be worth the shipping cost.

**Stacked margin protection.** Keep **Exclude Sale Items** on so the welcome discount does not compound with existing sale prices, protecting margin on promotional inventory.

---

## Troubleshooting

### The welcome coupon is not generated

**Cause:** The master toggle is off, the detected visitor is not actually new (has prior order history), or the trigger did not fire.
**Fix:** Confirm the feature is on and the correct **Trigger Event** is selected. Use a brand-new account or a clean browser to test, since the detection treats customers with prior order history as returning.

### The welcome email is not sent

**Cause:** **Send Welcome Email** is off, or another email plugin is blocking it.
**Fix:** Turn on **Send Welcome Email**. Confirm **Email Subject** and **Email Message** are set. Check WooCommerce email logs for errors, and temporarily disable other email plugins to isolate a conflict.

### The coupon applies to sale items when it should not

**Cause:** **Exclude Sale Items** is off.
**Fix:** Turn on **Exclude Sale Items** so the welcome coupon skips products already on sale.

### Each customer is getting the same code

**Cause:** **Generate Unique Coupon Codes** is off.
**Fix:** Turn on **Generate Unique Coupon Codes** so every customer receives their own code, which also prevents a shared code from being reused.

### The coupon is valid too long or expires too soon

**Cause:** **Coupon Validity Period** is set to an unintended value.
**Fix:** Review **Coupon Validity Period** (7 to 90 days or No Expiration). If a coupon has expired, note that expired welcome coupons are cleaned up automatically by the scheduled cleanup hook.

---

## Frequently Asked Questions

### How does the feature know a customer is really new?

It tracks customer history and purchase behavior. Registered users are identified by account and email, guests by email and order history, and optionally by browser cookie or IP. Customers with prior completed orders are treated as returning.

### Does the welcome coupon require the customer to register?

Only if you choose **Account Registration** as the trigger. With **First Website Visit**, **First Item Added to Cart**, or **Email Newsletter Signup**, a guest can receive the offer without registering.

### Are welcome coupon codes unique per customer?

Only when **Generate Unique Coupon Codes** is on. With it on, each customer gets their own code; with it off, all customers would share the single configured code.

### Can I choose what discount the welcome coupon gives?

Yes. Set **Welcome Coupon Type** (percentage, fixed cart, fixed product, or free shipping) and **Welcome Coupon Amount** to define the offer, plus **Minimum Order Amount** and **Coupon Validity Period** to bound it.

### Where does the customer get the coupon?

If **Send Welcome Email** is on, the coupon code and instructions arrive by email. You can customize the subject and body (using `{coupon_code}`, `{discount_amount}`, `{customer_name}`) under the welcome-email settings.

---

## Related Articles

- [How to Restrict WooCommerce Coupons by User Role in WordPress](woocommerce-enable-user-role-restrictions.md)
- [How to Create BOGO (Buy One Get One) Deals in WooCommerce](woocommerce-enable-bogo-deals.md)
- [How to Set Up WooCommerce Coupon Auto-Apply in WordPress](woocommerce-enable-auto-apply-coupons.md)
