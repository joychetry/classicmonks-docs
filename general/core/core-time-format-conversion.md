---
title: "How to Use the Time Format Conversion in Classic Monks | CM"
slug: core/time-format-conversion
description: "Convert WordPress time displays from 24-hour to 12-hour format with the [cm_time_format] shortcode in Classic Monks. Useful for international sites and audience-specific time preferences."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/core/time-format-conversion/
---

# How to Use the Time Format Conversion in WordPress

> Time Format Conversion adds the `[cm_time_format]` shortcode and a global filter that converts WordPress time displays from 24-hour to 12-hour format (with AM/PM) for international sites and audience-specific preferences.

## Key Takeaways

- One toggle, two effects (shortcode + global filter)
- Shortcode: `[cm_time_format time="14:30"]` outputs the time in 12-hour format
- Global filter: converts all `the_time()` and `get_the_time()` calls in the front-end
- Useful for sites that serve audiences used to 12-hour time
- WordPress stores time internally in 24-hour format; this only changes display

## What Is the Time Format Conversion feature?

Time Format Conversion provides two related capabilities:

1. **A shortcode** `[cm_time_format time="14:30"]` that takes a time string and outputs it in the chosen format (12-hour or 24-hour, with or without AM/PM)
2. **A global filter** that automatically converts time displays in templates and theme functions, so all times appear in 12-hour format without changing your theme code

The shortcode is useful for ad-hoc conversions in content; the global filter is useful for site-wide time display changes.

## Why You Need It

Most WordPress sites use the WordPress time format setting (Settings > General > Time Format), which defaults to the site's locale. Some scenarios require overriding this:

- **Multi-audience sites**: A US-based site serving a European audience (or vice versa) may want to standardize on one format
- **Custom themes**: Some themes hardcode `the_time('g:i a')` (12-hour) or `the_time('H:i')` (24-hour) without using the WordPress setting. Time Format Conversion overrides the hardcoded format
- **Content with mixed time displays**: When a page shows multiple times in different places, the shortcode lets you normalize them all to one format

The feature does not change WordPress's internal time storage. All times remain in 24-hour format in the database; only the display is affected.

---

## How to Use the Time Format Conversion in Classic Monks

### Step 1: Enable the Feature

In the Classic Monks settings, go to the **Core** tab, **Content** subtab. Scroll to the **Shortcode and Filter Utilities** section and toggle on **Enable Time Format Conversion (24h to 12h)**.

### Step 2: Save Changes

Click **Save Changes**.

### Step 3: Use the Shortcode

In any post, page, or template that processes shortcodes, use `[cm_time_format]` to display a time:

```
[cm_time_format time="14:30"]
[cm_time_format time="09:00" format="12h"]
[cm_time_format time="23:45" format="24h"]
[cm_time_format time="14:30" show_am_pm="true"]
```

The shortcode accepts three attributes:

- `time` (required): The time string in 24-hour format
- `format`: Either "12h" (default) or "24h"
- `show_am_pm`: "true" (default) or "false" (for 24-hour display, AM/PM is hidden)

### Step 4: (Optional) Customize the Global Filter

The global filter automatically converts time displays in `the_time()` and `get_the_time()` calls throughout your theme. To customize the filter behavior, use the available filters in the Advanced Options below.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Time Format Conversion (24h to 12h)** | Master toggle. Enables both the shortcode and the global filter. | Off |

Per-instance options are passed as shortcode attributes.

---

## Usage Examples

```markdown
# Convert a 24-hour time to 12-hour with AM/PM:
[cm_time_format time="14:30"]
Output: 2:30 PM

# Convert to 24-hour format (no AM/PM):
[cm_time_format time="14:30" format="24h"]
Output: 14:30

# Show 12-hour without AM/PM:
[cm_time_format time="14:30" show_am_pm="false"]
Output: 2:30

# Midnight conversion:
[cm_time_format time="00:00"]
Output: 12:00 AM

# Noon conversion:
[cm_time_format time="12:00"]
Output: 12:00 PM
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

### The shortcode shows the time in 24-hour format

**Cause:** The format attribute is set to "24h", or the global filter is interfering.
**Fix:** Verify the shortcode includes `format="12h"` (which is the default, so you may not need to specify it). If the global filter is converting to 24h, check the filter override settings or the `cm_time_format_global_output` filter.

### The global filter is not affecting theme time displays

**Cause:** The theme uses a custom time display function that bypasses WordPress's standard `the_time()` and `get_the_time()` calls.
**Fix:** Identify the theme's time display function (search for `date()` or `gmdate()` calls in the theme). Either modify the theme or add a custom filter that intercepts the custom function and applies the conversion.

### The shortcode outputs the raw time string instead of formatted

**Cause:** The `time` attribute is missing or not a valid time string.
**Fix:** Verify the shortcode includes the `time` attribute with a valid 24-hour time (e.g., "14:30", "09:00:00"). The shortcode uses `strtotime()` internally; invalid time strings are returned as-is.

### AM/PM is showing in lowercase ("am", "pm") instead of uppercase

**Cause:** The default WordPress time format setting is using lowercase. The shortcode uses the WordPress setting as the default.
**Fix:** Change the WordPress time format setting to use uppercase AM/PM (Settings > General > Time Format, use "g:i A" instead of "g:i a"). Or filter `cm_time_format_shortcode_output` to force uppercase.

### The conversion is showing different formats in different places

**Cause:** Some time displays use the WordPress setting, some use the global filter, and some use the shortcode. They all default to 12-hour but the formatting can differ.
**Fix:** Standardize by using only one method. The shortcode is the most predictable (it always uses the attributes you specify). Disable the global filter if you only want shortcode-based conversions.

---

## Related Articles

- [How to Use Shortcodes and Filter Utilities in Classic Monks](core-shortcodes.md)
- [How to Use the Tags No Comma Shortcode in Classic Monks](core-tags-no-comma-shortcode.md)
- [How to Use the RankMath Meta Excerpt Shortcode in Classic Monks](core-rm-excerpt-shortcode.md)
- [How to Use the Currency Converter in Classic Monks](core-currency-converter.md)
