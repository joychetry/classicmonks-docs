---
title: "How to Display Product Price History in WooCommerce | CM"
slug: woocommerce-product-price-history
description: "Track and display historical prices on WooCommerce sale products in Classic Monks. Configure lookback windows, lowest-price display, variable-product behavior, and EU Omnibus compliance."
last_updated: 2026-07-28
author: Joy
reading_time: 9 min
canonical: https://classicmonks.com/docs/woocommerce-product-price-history/
---

# How to Display Product Price History in WooCommerce

> Use the Classic Monks Product Price History feature to track WooCommerce price changes and display the lowest price in a configurable lookback window, including an EU Omnibus-compliant mode.

## Key Takeaways

- Tracks product and variation price history automatically on save
- Displays the lowest price in a configurable lookback window
- Supports an Omnibus-compliant sale-start calculation mode
- Controls display type, fallback behavior, and where the lowest price appears
- Exposes a shortcode and admin price-history meta box
- Supports simple and variable products

## What Product Price History Does

Product Price History tracks WooCommerce price changes in a dedicated database table and shows the lowest recorded price during the configured lookback window. On sale products, this is useful for consumer transparency and EU Omnibus compliance.

The feature does not just show the current sale badge. It stores historical regular and sale prices, calculates the lowest price from a defined time window, and then renders that lowest price in the product display according to your chosen display type and location settings.

---

## When to Enable It

Enable Product Price History when:

- You run regular promotions and want to display the lowest recent price automatically.
- You need EU Omnibus-compliant lowest-price disclosure.
- You want an admin history view on the product edit screen.
- You want a shortcode to place the lowest price anywhere on the site.

Leave it off if the store never runs sales or never needs price-history disclosure.

---

## Before You Enable It

### Check WooCommerce first

The feature requires WooCommerce. If WooCommerce is inactive, the Price History loader bails immediately.

### Decide the compliance mode

If the store operates in EU markets and must satisfy Omnibus requirements, choose **From sale start** as the calculation mode.

### Decide where the price appears

You can limit display to the product page only, or extend it to shop, category, tag, and related-product loops. Choose the narrowest set you need.

---

## How to Configure Product Price History

### Step 1: Open WooCommerce settings in Classic Monks

In WordPress admin, open **Classic Monks > WooCommerce**.

Enable **Product Price History** under the **Single Product** settings area.

### Step 2: Choose the calculation mode

Use **Calculation Mode**:

- **From sale start (Omnibus-compliant)**: Looks back from the product's sale start date.
- **From current day (rolling window)**: Uses a rolling lookback window from the current day.

Choose **From sale start** when Omnibus compliance is the priority.

### Step 3: Set the lookback window

Use **Number of Days** to define how far back the lowest price search goes.

Default: **30**.

### Step 4: Decide what happens when no lower price is found

Use **When No Lower Price Found**:

- **Hide lowest price**
- **Show current price as lowest**
- **Show custom text**

If you choose **Show custom text**, set the text in **Custom Fallback Text**. You can use the `{days}` placeholder.

### Step 5: Choose the display type

Use **Display Type**:

- **Regular (Crossed-out lowest price + sale price)**
- **Text (Separate lines with labels)**: This is the legally conservative Omnibus choice.
- **Alternative (Below product meta)**
- **Shortcodes only (Manual placement)**: Disables automatic rendering; you place the lowest price manually with the shortcode.

### Step 6: Choose the variable-product display style

Use **Variable Product Display**:

- **Show price range (min-max)**
- **Show minimum price only**

This affects how variable product prices appear in loops such as the shop page.

### Step 7: Choose display locations

Use **Display Locations**:

- Product page
- Shop page
- Category pages
- Tag pages
- Related / Upsell products

Enable only the locations where the lowest-price indicator is required when using **Regular**, **Text**, or **Alternative** display types. When **Shortcodes only (Manual placement)** is selected, these location settings are ignored and the lowest price is shown only where you place the shortcode.

### Step 8: Set custom labels

Use the **Custom "Lowest Price" Label** and **Custom "Current Price" Label** fields when you want wording other than the default. Leave them blank to use the plugin defaults.

### Step 9: Save and verify

Click **Save Changes**. Visit a sale product on the frontend and confirm the lowest price appears where expected.

---

## Configuration Options

| Option | What it controls | Source default |
|---|---|---:|
| **Product Price History** | Master toggle for the feature. | Off |
| **Calculation Mode** | Whether the lookback starts from the sale start date or uses a rolling window. | From sale start |
| **Number of Days** | Lookback window in days. | 30 |
| **When No Lower Price Found** | Fallback behavior when the history is empty or not lower than the current price. | Hide lowest price |
| **Custom Fallback Text** | Fallback text when custom fallback is selected. Supports `{days}`. | Price in the last {days} days is the same as current price |
| **Display Type** | Regular, text, alternative, or shortcode-only lowest-price presentation. | Regular |
| **Variable Product Display** | Price range or minimum price in loops. | Range |
| **Display Locations** | Product page, shop page, category pages, tag pages, related/upsell products. Ignored in shortcode-only mode. | Product page and shop page |
| **Custom "Lowest Price" Label** | Override the default lowest-price label. | Empty |
| **Custom "Current Price" Label** | Override the default current-price label in text mode. | Empty |

---

## How the Price History Works

### Price tracking

Every time a product or variation is saved, Price History records a new history entry if the price has changed. The feature tracks both regular and sale prices.

For variable products, price tracking happens at the variation level rather than the parent product. This prevents the parent record from becoming meaningless when only one variant changes.

### Lowest-price lookup

When WooCommerce renders price HTML, the feature looks up the lowest recorded price within the configured window. If the calculated lowest price is lower than the current regular price, it shows that lowest price according to your display type and location settings.

### Omnibus mode

In **From sale start** mode, the lookback window is calculated from the product's sale start date. This is the recommended mode when the goal is to comply with the EU Omnibus requirement to disclose the lowest price applied during the 30-day period before the promotion.

### Fallback behavior

When the history is empty, stale, or no lower price exists, the feature follows your fallback setting:

- **Hide lowest price**: No extra price indication is shown.
- **Show current price as lowest**: The current price is shown as the lowest.
- **Show custom text**: A custom message is shown instead.

---

## Where the Lowest Price Appears

Enable only the display locations you actually need:

- **Product page**: Single product view
- **Shop page**: Main WooCommerce shop loop
- **Category pages**: Product category archives
- **Tag pages**: Product tag archives
- **Related / Upsell products**: Product recommendation loops

If the lowest price appears where you do not want it, disable that display location instead of adjusting theme templates.

---

## Product Edit Screen Price History

When the feature is active, the product edit screen includes a **Price history** meta box.

This meta box is useful for:

- Viewing recorded price history rows
- Manually editing history entries when necessary
- Applying an older price as the current product price
- Deleting incorrect history entries

Use the meta box for corrections or audits. Normal price tracking happens automatically when products or variations are saved.

---

## Shortcode

Use the `cm_price_history` shortcode to display the lowest price for a product or variation.

Example usage:

```markdown
[cm_price_history id="694"]
```

Use this when the lowest price must appear outside the normal display-location rules, such as in page builder content, promotional copy, or custom product templates.

---

## Verify the Result

### Product page test

1. Open a sale product.
2. Confirm the lowest price indicator appears if **Product page** is enabled.
3. Check that the label, formatting, and position match the selected **Display Type**.

### Shop loop test

1. Open the main shop page if **Shop page** is enabled.
2. Confirm the lowest-price indicator appears in the loop.
3. If the product is variable, confirm the price presentation matches **Variable Product Display**.

### Omnibus test

1. Use a product whose current sale price is lower than the regular price but not lower than the lowest price during the lookback window.
2. Confirm the displayed lowest price reflects the correct historical comparison, not just the current sale badge.

### Meta box test

1. Open the product edit screen.
2. Confirm the price history meta box is present.
3. Confirm that saving a new price creates a new history row.

---

## Troubleshooting

### The lowest price does not appear

**Cause:** The feature is disabled, no sale is active, the selected display locations exclude the page being tested, or the history does not contain a lower price.
**Fix:** Enable the feature, verify the product is on sale, check the enabled display locations, and confirm that the configured lookback window actually includes earlier price data.

### The lowest price looks wrong

**Cause:** The calculation mode or lookback window is not set to what you expect.
**Fix:** Confirm **Calculation Mode** and **Number of Days**. Use **From sale start** for Omnibus compliance and verify that the product has a saved sale start date.

### The indicator shows on pages where it should not

**Cause:** One or more display locations are enabled unexpectedly.
**Fix:** Disable the unnecessary display locations under **Display Locations**.

### Variable products show inconsistent pricing in loops

**Cause:** The variable display mode is set to range while you want only the minimum price, or vice versa.
**Fix:** Change **Variable Product Display** to match the store's merchandising preference.

### The meta box is missing on a product

**Cause:** Price History is disabled, or the screen is not a WooCommerce product edit screen.
**Fix:** Enable the master toggle and open the standard WooCommerce product editor.

### The lowest price never changes after updates

**Cause:** The history is not being recorded because the sale price has not changed, or the product is a variable parent instead of a variation.
**Fix:** Edit a variation or adjust the product's sale price. For variable products, Price History tracks variations, not the parent.

---

## Related Articles

- [How to Display Price Savings in WordPress](woocommerce-show-price-savings.md)
- [How to Show Percentage Off in WordPress](woocommerce-show-percentage-off.md)
- [How to Customize the Add to Cart Button in WordPress](woocommerce-customize-add-to-cart-button.md)

---

## Developer Notes

### Source files

- `functions/woocommerce/price-history.php`
- Admin assets: `assets/css/cm-price-history.css`, `assets/js/cm-price-history-admin.js`
- Frontend assets: `assets/js/cm-price-history.min.js`

### Database

- Custom table: `{wpdb_prefix}cm_price_history`
- Cached lowest price meta key: `_cm_price_history`

### Important hooks

- `init` via `cm_price_history_init()`
- `woocommerce_update_product`
- `woocommerce_update_product_variation`
- `woocommerce_before_product_object_save`
- `woocommerce_before_variation_object_save`
- `woocommerce_get_price_html`
- `woocommerce_product_meta_end`
- `add_meta_boxes_product`
- `admin_enqueue_scripts`
- `widgets_init`
- `wp_ajax_cm_price_history_delete`
- `wp_ajax_cm_price_history_apply`
- `wp_ajax_cm_price_history_update`
- `shortcode: cm_price_history`

### Recommended implementation reference

The internal feature reference at `docs/features-docs/price-history/price-history.md` is useful for schema details, write-path behavior, and hook mapping. Use it for developer support work, not for the public-facing article.
