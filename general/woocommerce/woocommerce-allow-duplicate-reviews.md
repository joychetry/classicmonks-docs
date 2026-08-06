---
title: "How to Allow Multiple Reviews on a Product in WooCommerce"
slug: allow-duplicate-reviews
description: "Let the same customer submit several reviews for one WooCommerce product. Disable the default duplicate-comment block for product reviews with Classic Monks."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/allow-duplicate-reviews/
---

# How to Allow Multiple Reviews on a Product in WooCommerce

> Allow customers to submit more than one review for the same WooCommerce product. This removes the default duplicate-comment block so the same author and email can leave another review for that product.

## Key Takeaways

- Turn off the duplicate-review block that WooCommerce inherits from WordPress comments
- The same customer can submit another review for the same product
- Affects product reviews, not regular blog comments
- One toggle, no nested options
- Review moderation and spam filtering still apply

## What Does the Feature Do?

WordPress blocks a second comment from the same author name and email on the same post. WooCommerce product reviews run on that comment system, so by default a customer can leave only one review per product. The **Allow Duplicate Reviews** feature removes that block for product reviews, letting the same customer submit another review for the same product.

Behind the scenes the feature removes the duplicate-comment guard when a review is submitted, without touching regular WordPress comments.

## Why You Might Use It

Product reviews differ from blog comments, so a customer may reasonably want to review again:

- A buyer leaves an early review, then updates it after long-term use
- A product is updated and deserves a fresh review
- A customer buys the same product again and wants a new opinion
- A follow-up review reflects changed expectations

The trade-off is higher spam and moderation load. The same name and email can now submit repeatedly, so keep review moderation active if you enable this.

---

## How to Allow Multiple Reviews on the Same Product in WooCommerce

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Single Product** settings area.
3. Toggle on **Allow Duplicate Reviews**.

### Step 2: Save and Test

Click **Save Changes**. Submit a review on a product, then submit another with the same name and email. Both should be accepted (subject to your moderation settings).

---

## Configuration Options

| Option | Default |
|--------|---------|
| **Allow Duplicate Reviews** | Off |

There are no nested options. The feature is a single on/off control.

---

## What Gets Affected

- WooCommerce product reviews: the same customer can now submit more than one review for the same product
- The duplicate-comment guard: no longer blocks a repeat review from the same author and email

## What Does NOT Get Affected

- Regular WordPress comments: these keep the default duplicate block
- Review moderation: the approval workflow still applies
- Spam filtering: Akismet and other spam checks still run
- Review settings in WooCommerce: verified-owner and other product review rules are unchanged

---

## Advanced Options (Developers)

The feature registers one hook in `functions/woocommerce/woocommerce-functions.php`:

```php
add_filter( 'pre_comment_on_post', 'cm_allow_duplicate_reviews' );
```

**`pre_comment_on_post`** calls `cm_allow_duplicate_reviews()`. When the feature is enabled, it removes the `duplicate_comment_id` filter's `wp_die` handler, so a repeat review is no longer killed by the duplicate check.

---

## Troubleshooting

### Duplicate reviews are still being blocked

**Cause:** The feature toggle is off, or another plugin re-applies a review deduplication rule.
**Fix:** Confirm **Allow Duplicate Reviews** is on. Check for review plugins that enforce their own one-review-per-product behavior.

### More spammy reviews are appearing

**Cause:** Enabling the feature lets the same author and email submit repeatedly.
**Fix:** Keep review moderation and spam filtering on, and review pending items in **Comments**. The feature removes the duplicate block; it does not disable spam checks.

### Regular blog comments are now duplicating

**Cause:** This should not happen if the change is scoped to the review flow.
**Fix:** The feature removes the duplicate guard during review submission. If regular comments are affected, check whether a plugin applies review handling to all comments.

---

## Frequently Asked Questions

### Does this allow one review per order or unlimited reviews?

Unlimited. The feature removes the duplicate-comment block for product reviews, so the same author and email can submit multiple reviews for the same product, regardless of how many purchases they made.

### Is this the same as allowing review updates?

No. This lets a customer submit brand-new reviews repeatedly. Updating an existing review is a separate behavior controlled by WooCommerce review settings and any reviews extension you use.

### Will this affect blog comments?

No. The feature targets the product review flow. Regular WordPress comments keep the default duplicate-comment block.

### Is spam protection still active?

Yes. The feature only removes the duplicate-review block. WordPress spam filtering, Akismet, and your moderation queue continue to work normally.

---

## Related Articles

- [How to Disable Product Reviews in WooCommerce](woocommerce-disable-product-reviews.md)
- [How to Show Price Savings in WooCommerce](woocommerce-show-price-savings.md)
- [How to Show Percentage Off in WooCommerce](woocommerce-show-percentage-off.md)
