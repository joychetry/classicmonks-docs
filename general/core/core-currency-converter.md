---
title: "How to Use the Currency Converter in Classic Monks"
slug: currency-converter
description: "Add a currency converter to your WordPress site with the [cm_currency_converter] shortcode in Classic Monks. Configure base currency, target currencies, API endpoint, and cache duration."
last_updated: 2026-06-24
author: Joy
reading_time: 6 min
canonical: https://classicmonks.com/docs/currency-converter/
---

# How to Use the Currency Converter in WordPress

> The Currency Converter adds a currency selector to your WordPress site that converts prices displayed in `<span class="cm-price">` tags to a visitor's chosen currency, using real-time exchange rates from a configurable API.

## Key Takeaways

- Shortcode: `[cm_currency_converter]` displays a currency selector
- Markup pattern: wrap prices in `<span class="cm-price" data-price="49.99">$49.99</span>`
- Configurable base currency, target currencies, API endpoint, and cache duration
- Default API: exchangerate.host (free, no API key required)
- Real-time conversion with caching to avoid rate limits

## What Is the Currency Converter?

The Currency Converter is a Classic Monks shortcode-based feature that displays a dropdown of currencies on your site. When a visitor selects a currency, every `<span class="cm-price" data-price="X">` element on the page updates to show the equivalent value in the selected currency, using live exchange rates from a configurable API.

The system has three components:

1. **The shortcode `[cm_currency_converter]`** displays the currency selector. Place it in a sidebar, header, or wherever you want the dropdown
2. **The markup pattern** `<span class="cm-price" data-price="49.99">$49.99</span>` marks prices for conversion. The data-price attribute holds the base-currency value
3. **The conversion logic** fetches exchange rates, caches them, and updates the displayed prices when the visitor selects a new currency

## Why You Need It

WordPress sites selling internationally have several options for multi-currency:

- **WooCommerce multi-currency plugins** (WPML, Aelia): full-featured but expensive and complex
- **Static currency switchers**: require manual price updates when exchange rates change
- **JavaScript-based converters** (e.g., free Open Exchange Rates widget): work but require API setup and are not customizable
- **Classic Monks Currency Converter**: lightweight, no API key required (with default endpoint), customizable base/target currencies, and uses standard WordPress caching

For sites that display prices but don't run WooCommerce (e.g., service pages, portfolio pricing, donation forms), the Currency Converter is the simplest multi-currency option.

---

## How to Use the Currency Converter in Classic Monks

### Step 1: Enable the Shortcode

In the Classic Monks settings, go to the **Core** tab, **Content** subtab. Scroll to the **Shortcode and Filter Utilities** section and toggle on **Enable Currency Converter**.

### Step 2: Configure the Base Currency

Enter your store's base currency code in the **Base Currency** field. Default: USD. Use the three-letter ISO 4217 code (USD, EUR, GBP, JPY, etc.).

### Step 3: Configure the Target Currencies

Enter the list of currencies you want visitors to be able to switch to in the **Target Currencies** field. Default: `INR,EUR,GBP,AUD`. Format: comma-separated three-letter codes.

### Step 4: (Optional) Change the API Endpoint

The default endpoint is `https://api.exchangerate.host/latest`, a free public API that doesn't require authentication. To use a different provider, enter the API URL in the **API Endpoint** field. The endpoint must return a JSON response in the format:

```json
{
  "base": "USD",
  "rates": {
    "EUR": 0.85,
    "GBP": 0.75,
    "JPY": 110.50
  }
}
```

### Step 5: (Optional) Adjust the Cache Duration

The cache duration (in seconds) controls how often the API is called. Default: 3600 (1 hour). Minimum: 300 (5 minutes). For sites with low traffic, longer cache reduces API calls. For sites where exchange rate accuracy matters, shorter cache keeps rates fresher.

### Step 6: Save Changes

Click **Save Changes**.

### Step 7: Mark Prices for Conversion

In your post content, wrap each price in the `cm-price` span:

```html
Subscription: <span class="cm-price" data-price="49.99">$49.99</span>
Annual: <span class="cm-price" data-price="499.99">$499.99</span>
```

The `data-price` attribute is the base-currency value. The text inside the span is what visitors see by default (e.g., "$49.99"). When the visitor selects a different currency, the text updates to show the converted value (e.g., "€42.50" for EUR).

### Step 8: Add the Currency Selector

Place the shortcode where you want the selector to appear:

```html
[cm_currency_converter]
```

Common placements: sidebar widget, header, footer, or a dedicated "Choose your currency" page.

### Step 9: Test

Visit a page with both the shortcode and a `cm-price` span. Select a different currency. The price should update to the converted value, and the URL should update to remember the choice (e.g., `?currency=EUR`).

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Currency Converter** | Master toggle. | Off |
| **Base Currency** | Three-letter ISO 4217 code. | USD |
| **Target Currencies** | Comma-separated list of three-letter codes. | INR,EUR,GBP,AUD |
| **API Endpoint** | URL returning JSON rates. | https://api.exchangerate.host/latest |
| **Cache Duration** | Seconds to cache exchange rates. Min 300, default 3600. | 3600 |

---

## Usage Examples

```html
# Currency selector in a sidebar widget:
[cm_currency_converter]

# Mark a price for conversion:
Subscription: <span class="cm-price" data-price="49.99">$49.99</span>

# Multiple prices on a page:
<p>Starter: <span class="cm-price" data-price="9.99">$9.99</span></p>
<p>Pro: <span class="cm-price" data-price="49.99">$49.99</span></p>
<p>Enterprise: <span class="cm-price" data-price="499.99">$499.99</span></p>

# In a template (PHP):
<?php echo do_shortcode('[cm_currency_converter]'); ?>

# With a custom wrapper class for styling:
<div class="currency-selector">
  [cm_currency_converter]
</div>
```

---

## Developer Notes

This feature is a single toggle with no developer hooks currently exposed. The feature-specific logic is loaded conditionally when the toggle is enabled.

**Options used:**
| Option | Type | Default |
|--------|------|---------|
| Feature toggle | Boolean | `false` |
---

## Troubleshooting

### The selector shows but the prices do not update

**Cause:** The prices are not wrapped in the correct `<span class="cm-price" data-price="X">` markup, or the JavaScript that listens for the selector change is not loaded.
**Fix:** Verify the markup pattern is exactly `<span class="cm-price" data-price="49.99">`. Verify the page includes the shortcode `[cm_currency_converter]` somewhere (the JavaScript is loaded by the shortcode). View the page source and check for JavaScript errors in the console.

### The API call is failing

**Cause:** The endpoint URL is incorrect, the API is down, or the API returns a different format than expected.
**Fix:** Test the endpoint URL in a browser or with `curl`. The response should match the expected JSON format. If the API is rate-limited, increase the cache duration to reduce call frequency.

### The same price is showing for every currency

**Cause:** The exchange rate data is missing or the rate for the selected currency is 1.0 (no conversion).
**Fix:** Verify the API response includes the selected currency code. Check the rate field for the selected currency; if it's 1.0, the API is not providing a real exchange rate for that currency.

### The currency selection does not persist across pages

**Cause:** The default storage is the URL (`?currency=EUR`), which means each new page needs the URL parameter to apply the choice.
**Fix:** Either accept the URL-based behavior (visitors can bookmark a currency-specific URL), or change the storage to cookies via the `cm_currency_user_choice_storage` filter.

### The conversion is showing rounded values (e.g., $9.99 → €8)

**Cause:** The default rounding rounds to whole numbers (e.g., 8.49 → 8).
**Fix:** Remove the rounding via the `cm_currency_convert_price` filter, or change the rounding strategy (e.g., round to 2 decimal places for cents, or no rounding for display purposes).

---

## Related Articles

- [How to Use Shortcodes and Filter Utilities in Classic Monks](core-shortcodes.md)
- [How to Use the Tags No Comma Shortcode in Classic Monks](core-tags-no-comma-shortcode.md)
- [How to Use the RankMath Meta Excerpt Shortcode in Classic Monks](core-rm-excerpt-shortcode.md)
- [How to Use the Time Format Conversion in Classic Monks](core-time-format-conversion.md)
