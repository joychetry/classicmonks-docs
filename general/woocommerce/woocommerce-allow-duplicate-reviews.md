---
title: "How to Allow Duplicate Reviews in WordPress | CM"
slug: woocommerce/allow-duplicate-reviews
description: "Allow the same user to submit multiple reviews for the same WooCommerce product in Classic Monks. Overrides WordPress's default duplicate-comment block for product reviews."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/woocommerce/allow-duplicate-reviews/
---

# How to Allow Duplicate Reviews in WordPress

> Allow Duplicate Reviews lets the same user submit multiple reviews for the same WooCommerce product. Overrides WordPress's default behavior of blocking the second review from the same author and email.

## Key Takeaways

- Single toggle, no nested options
- Affects WooCommerce product reviews specifically (not regular WordPress comments)
- Same user can submit unlimited reviews for the same product
- Useful for long-term product reviews and evolving experiences
- Spam risk: easier for spammers to flood product reviews

## What Is the Allow Duplicate Reviews feature?

WordPress by default blocks the second comment from a user with the same name and email on the same post. This applies to regular comments AND to WooCommerce product reviews (which are a special comment type).

The Allow Duplicate Reviews feature disables the duplicate block specifically for WooCommerce product reviews. The same user can submit multiple reviews for the same product.

## Why You Need It

The default duplicate block is correct for most comment scenarios, but product reviews are different:

- **Long-term ownership**: A customer might buy a product, use it for a year, and want to leave a new review based on long-term experience
- **Updated products**: A product that has been updated (new features, new version) deserves a fresh review
- **Comparison reviews**: A customer might leave an initial review, then a follow-up after comparing to a similar product
- **Multi-purchase**: A customer who bought the product multiple times might leave separate reviews for each experience

The trade-off is increased spam risk. A spammer can post multiple reviews with the same name and email. For most sites, the spam risk outweighs the benefits. For sites that value long-term reviews, this feature is useful.

---

## How to Allow Duplicate Reviews in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Single Product** subtab.

### Step 3: Enable Allow Duplicate Reviews

Scroll to **Allow Duplicate Reviews** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Submit a review on a product. Then submit another review with the same name and email. Both should appear.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Allow Duplicate Reviews** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- WooCommerce product reviews: the same user can submit multiple reviews for the same product
- All other comment types (regular WordPress comments, WooCommerce order notes, etc.): not affected

## What Does NOT Get Affected

- Regular WordPress comments: still subject to the default duplicate block
- Comment moderation, spam filtering, Akismet integration: still work as expected
- Review approval workflow: still applies (if you require manual approval)
- The review submission form: same form, just allows multiple submissions
- Other duplicate review checks (e.g., review spam detection): independent

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Filters:**

- `pre_comment_on_post` calls `cm_allow_duplicate_reviews()` (Allows duplicate reviews from same user on same product)

```php
// Hooked in woocommerce-functions.php
add_filter( 'pre_comment_on_post', 'cm_allow_duplicate_reviews' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### Duplicate reviews are still being blocked

**Cause:** The toggle is off, or a different plugin is enforcing review deduplication.
**Fix:** Verify the toggle is on. Check for review-related plugins (e.g., "Review Stream", custom review management plugins) that may enforce their own duplicate checks.

### The same user can't leave reviews but spam reviewers can

**Cause:** The toggle is on, but a spam filter or moderation queue is blocking legitimate reviews.
**Fix:** Check the WordPress moderation queue (Comments > Spam or Comments > Pending) for the legitimate review. Mark it as not spam. The duplicate-allow feature doesn't bypass spam filtering.

### The review count is wrong (showing too many)

**Cause:** The review count is calculated by counting all reviews, including duplicates that are now allowed.
**Fix:** This is expected. The count includes all reviews. If you want to limit the count display, use the plugin settings to cap the number of reviews per user.

### I want to allow duplicates for some products but not others

**Cause:** The toggle is global.
**Fix:** Configure in the plugin settings to specify which products allow duplicates. The default is all products; the filter can restrict to a subset.

---

## Related Articles

- [How to Disable Product Reviews in WordPress](woocommerce-disable-product-reviews.md)
- [How to Customize the Add to Cart Button in WordPress](woocommerce-customize-add-to-cart-button.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
