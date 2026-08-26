---
title: "How to Use the RankMath Meta Excerpt Shortcode in Classic Monks"
slug: rm-excerpt-shortcode
description: "Display the RankMath SEO meta description as visible page content using the [rm_excerpt] shortcode in Classic Monks. Show SEO descriptions on archive pages, related post sections, and more."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/rm-excerpt-shortcode/
---

# How to Use the RankMath Meta Excerpt Shortcode in WordPress

> The `[rm_excerpt]` shortcode displays a post's RankMath SEO meta description as visible page content, where the standard WordPress excerpt would normally appear.

## Key Takeaways

- One shortcode: `[rm_excerpt]`
- Displays the RankMath meta description field, not the standard WordPress excerpt
- Useful for archive pages, related post sections, and anywhere a post summary appears
- Falls back gracefully if RankMath is not active
- No nested options; the toggle just enables the shortcode

## What Is the RankMath Meta Excerpt Shortcode?

RankMath stores the SEO meta description (the description Google shows in search results) as a post meta field. This field is separate from the standard WordPress excerpt and is typically not displayed on the front-end.

The `[rm_excerpt]` shortcode outputs the RankMath meta description wherever you place the shortcode. It does not require a manual excerpt and does not affect the post's regular content or featured image.

## Why You Need It

The standard WordPress excerpt is fine for many sites, but the RankMath meta description is often more carefully crafted (because it affects SEO and search snippets). Showing the same text on the page:

- **Visual consistency**: The description readers see matches the description in Google
- **SEO alignment**: No risk of the visible content diverging from the indexed content
- **Saves time**: Authors write the description once for SEO; it doesn't need to be duplicated in the post excerpt field
- **Template control**: Place the shortcode in templates, custom blocks, or page builders; the description appears wherever you want it

The shortcode is especially useful in archive pages, related-posts sections, and any custom block where you want a post summary but don't want to maintain a separate excerpt.

---

## How to Use the RankMath Meta Excerpt Shortcode in Classic Monks

### Step 1: Enable the Shortcode

In the Classic Monks settings, go to the **Core** tab, **Content** subtab. Scroll to the **Shortcode and Filter Utilities** section and toggle on **RankMath Meta Excerpt Shortcode**.

### Step 2: Install and Activate RankMath

The shortcode reads from RankMath's meta description field. If RankMath is not installed and active, the shortcode returns an empty string. Install RankMath from the WordPress.org repository if it isn't already.

### Step 3: Set a Meta Description on a Post

Open a post edit screen. Scroll to the RankMath SEO section (usually below the content editor). In the **Description** field, enter the post's meta description. Save the post.

### Step 4: Add the Shortcode to Your Content

In any post, page, or template that processes shortcodes, add:

```
[rm_excerpt]
```

The shortcode outputs the RankMath meta description for the current post.

### Step 5: View the Result

Preview or publish the page. The RankMath meta description appears where the shortcode was placed.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **RankMath Meta Excerpt Shortcode** | Master toggle. Enables the `[rm_excerpt]` shortcode. | Off |

No per-instance options. The shortcode is just `[rm_excerpt]` with no attributes.

---

## Usage Examples

```markdown
# Default usage (outputs the current post's RankMath description):
[rm_excerpt]

# Inside a theme template or block:
<?php echo do_shortcode('[rm_excerpt]'); ?>

# Combined with a heading for archive cards:
<h3>Summary</h3>
[rm_excerpt]

# In a custom post type with no standard excerpt:
[rm_excerpt]
```

---

## What Happens When RankMath Is Not Active

If RankMath is not installed, the shortcode's `get_post_meta($post_id, 'rank_math_description', true)` returns an empty string. The shortcode outputs nothing, and the surrounding content renders normally. There is no error message or visual indicator that the shortcode did nothing.

If you want a fallback (e.g., to the standard WordPress excerpt), wrap the shortcode in a conditional check in your template:

```php
<?php
$rm_excerpt = do_shortcode('[rm_excerpt]');
if ( $rm_excerpt ) {
    echo $rm_excerpt;
} else {
    echo get_the_excerpt();
}
?>
```

This shows the RankMath description if available, and falls back to the standard excerpt otherwise.

---

## Developer Notes

This feature is a single toggle with no developer hooks currently exposed. The feature-specific logic is loaded conditionally when the toggle is enabled.

**Options used:**
| Option | Type | Default |
|--------|------|---------|
| Feature toggle | Boolean | `false` |
---

## Troubleshooting

### The shortcode outputs nothing

**Cause:** RankMath is not active, the post has no meta description set, or the post ID is not in scope.
**Fix:** Verify RankMath is installed and active. Verify the post has a Description set in the RankMath SEO panel. If the shortcode is in a custom block or widget, ensure the post ID is correctly available (the shortcode uses `get_the_ID()` internally).

### The output is HTML-encoded

**Cause:** The shortcode output is being escaped as HTML somewhere in the rendering chain. This is correct security behavior; the meta description is plain text and should not contain HTML.
**Fix:** No action needed. The shortcode runs `wpautop()` on the output, which adds paragraph tags if the description has line breaks. If you want raw output without auto-paragraph, filter `cm_rm_excerpt_output` and remove the `wpautop` call.

### The shortcode shows a different post's description

**Cause:** The `get_the_ID()` call inside the shortcode is returning an unexpected value. This happens when the shortcode is used inside a Query Loop or nested WP_Query.
**Fix:** Pass the post ID explicitly. Use a custom shortcode that wraps `[rm_excerpt post_id="123"]` and adds the meta lookup with the passed ID.

### The SEO description shows in search results but not via the shortcode

**Cause:** The post has a RankMath description, but the description is set in a different meta key (older versions of RankMath used different keys).
**Fix:** Check the post's meta in the database or via `get_post_meta($post_id)` in WordPress debug. If the description is in `rank_math_description` (the current key), the shortcode works. If it's in an older key, use the `cm_rm_excerpt_meta_key` filter to point to the right key.

---

## Related Articles

- [How to Use Shortcodes and Filter Utilities in Classic Monks](core-shortcodes.md)
- [How to Use the Tags No Comma Shortcode in Classic Monks](core-tags-no-comma-shortcode.md)
- [How to Use the Time Format Conversion in Classic Monks](core-time-format-conversion.md)
- [How to Use the Currency Converter in Classic Monks](core-currency-converter.md)
