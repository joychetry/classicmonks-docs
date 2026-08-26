---
title: "How to Use the Tags No Comma Shortcode in Classic Monks"
slug: tags-no-comma-shortcode
description: "Display WordPress post tags without the default comma separator using the [tags_no_comma] shortcode in Classic Monks. Customize the separator with the separator attribute."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/tags-no-comma-shortcode/
---

# How to Use the Tags No Comma Shortcode in WordPress

> The `[tags_no_comma]` shortcode displays a post's tags without the default comma separator, with a configurable separator character for custom styling.

## Key Takeaways

- Replaces the default comma-separated tag list with a custom separator
- Configurable separator via the `separator` attribute
- Works inside any post, page, or template that processes shortcodes
- Useful for design systems that use icons, bullets, pipes, or other non-comma separators
- Standard WordPress `post_tag` taxonomy only (not custom taxonomies)

## What Is the Tags No Comma Shortcode?

WordPress's default tag display uses commas (e.g., "WordPress, Plugins, Bricks"). The `[tags_no_comma]` shortcode displays the same tags with a customizable separator, so you can use bullets, pipes, icons, or any character that fits your design.

The shortcode accepts a `separator` attribute:

```
[tags_no_comma separator=" • "]
[tags_no_comma separator=" | "]
[tags_no_comma separator=" &#9679; "]  <!-- bullet character -->
```

The default separator is a single space when no attribute is provided.

## Why You Need It

The default comma-separated tag list is functional but rarely matches a site's visual design. Common reasons to use a custom separator:

- **Design consistency**: Many sites use bullet (•) or pipe (|) separators to match navigation and footer styling
- **Visual hierarchy**: A non-comma separator (like → or ⇒) suggests forward motion or progression
- **Internationalization**: Some languages and scripts have different separator conventions (e.g., middle dot · in French, ideographic comma 、 in Chinese/Japanese)
- **Accessibility**: A meaningful separator (vs. a comma) is easier for screen readers to parse when reading the tag list aloud

The shortcode is a small but useful customization for any site that cares about tag display.

---

## How to Use the Tags No Comma Shortcode in Classic Monks

### Step 1: Enable the Shortcode

In the Classic Monks settings, go to the **Core** tab, **Content** subtab. Scroll to the **Shortcode and Filter Utilities** section and toggle on **Tags with No Comma Shortcode**.

### Step 2: Save Changes

Click **Save Changes**.

### Step 3: Add the Shortcode to Your Content

Open any post or page edit screen. In the content editor, add the shortcode where you want the tag list to appear:

```
[tags_no_comma separator=" • "]
```

### Step 4: Customize the Separator

Change the `separator` attribute to whatever character or string fits your design:

```
[tags_no_comma separator=" | "]      <!-- pipe -->
[tags_no_comma separator=" / "]      <!-- forward slash -->
[tags_no_comma separator=": "]     <!-- em dash (do not actually use this; use a colon or comma in real text) -->
[tags_no_comma separator=" " ]      <!-- single space (the default) -->
```

### Step 5: View the Result

Preview or publish the post. The tags appear with your custom separator.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Tags with No Comma Shortcode** | Master toggle. Enables the `[tags_no_comma]` shortcode. | Off |

The `separator` attribute is per-shortcode-instance, set when you use the shortcode.

---

## Usage Examples

```markdown
# Default (single space):
[tags_no_comma]
Output: WordPress Plugins Bricks

# With bullet separator:
[tags_no_comma separator=" • "]
Output: WordPress • Plugins • Bricks

# With pipe separator:
[tags_no_comma separator=" | "]
Output: WordPress | Plugins | Bricks

# With arrow separator:
[tags_no_comma separator=" → "]
Output: WordPress → Plugins → Bricks

# No separator (just space):
[tags_no_comma separator=" "]
Output: WordPress Plugins Bricks (single space between)

# Empty separator (no space):
[tags_no_comma separator=""]
Output: WordPressPluginsBricks
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

### The shortcode shows up as literal text

**Cause:** The shortcode toggle is off, or shortcodes are not being processed in the content area.
**Fix:** Verify the toggle is on. If you're using a custom block or widget that doesn't process shortcodes, switch to a standard WordPress content area (page/post editor, classic widget, classic block).

### The separator is HTML-encoded on the page

**Cause:** The separator is being escaped as HTML, so `&` becomes `&amp;`, etc.
**Fix:** This is correct security behavior. If you need to use HTML entities in the separator (e.g., `&#9679;` for a bullet), make sure your shortcode attribute is wrapped in quotes: `[tags_no_comma separator=" &#9679; "]`. Some plugins strip quotes from shortcode attributes; in that case, use the Unicode character directly.

### The shortcode only shows on the post, not on archive pages

**Cause:** The shortcode is in the post content, which only renders on the single post view. Archive pages use the theme's tag list template.
**Fix:** To use the shortcode on archive pages, add it to your theme's template (e.g., `archive.php`, `category.php`) using `<?php echo do_shortcode('[tags_no_comma separator=" • "]'); ?>`. Or use a child theme to override the theme's tag list rendering.

### The shortcode is showing the separator but the tags list is empty

**Cause:** The post has no tags assigned, or the tags are private (not visible to non-logged-in visitors).
**Fix:** Add tags to the post in the post edit screen. Verify the tags are public (not private).

### The custom separator works in the editor preview but not on the front-end

**Cause:** Caching, or a theme function is overriding the shortcode output.
**Fix:** Clear all caching layers. Check your theme for any `the_content` filter that might be stripping shortcode attributes. Use the [the_content filter example above] to apply the separator consistently.

---

## Related Articles

- [How to Use Shortcodes and Filter Utilities in Classic Monks](core-shortcodes.md)
- [How to Use the RankMath Meta Excerpt Shortcode in Classic Monks](core-rm-excerpt-shortcode.md)
- [How to Use the Time Format Conversion in Classic Monks](core-time-format-conversion.md)
- [How to Use the Currency Converter in Classic Monks](core-currency-converter.md)
