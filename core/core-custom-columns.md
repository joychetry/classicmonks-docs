---
title: "How to Use Custom Columns in Classic Monks: 14 Admin Columns"
slug: custom-columns
description: "Customize the columns shown in WordPress post, page, and custom post type list tables with 14 optional data fields from Classic Monks."
last_updated: 2026-06-24
author: Joy
reading_time: 6 min
canonical: https://classicmonks.com/docs/custom-columns/
---

# How to Use Custom Columns in WordPress (Admin Columns)

> Custom Columns adds 14 optional data columns to your WordPress post, page, and custom post type list tables, with one master toggle and per-column switches.

## Key Takeaways

- One master toggle to enable Custom Columns
- 14 individual column toggles (Last Modified, Author Role, Word Count, Reading Time, Featured Image, Template, Revisions, Menu Order, Slug, ID, Modified By, Excerpt, Taxonomies, Comments Status, Ping Status, Child Pages Count)
- Each column is independently enabled or disabled
- Improves content management workflow at a glance

---

## What Are Custom Columns?

Custom Columns is a feature in the Classic Monks Core tab, Content subtab. It adds optional data columns to the WordPress admin list tables for posts, pages, and custom post types. Instead of opening individual posts to check word count, featured image, or last modified date, you see all of that information in the list view.

The feature has a master toggle (Custom Columns) and 14 individual column toggles. Each column is enabled independently, so you only see the data you care about.

## Why You Need It

The default WordPress list table shows the title, author, categories, tags, date, and comments count. For content teams managing many posts, that view is too sparse. You end up clicking into individual posts to check basic metadata that should be visible at a glance.

Custom Columns adds the metadata that content teams actually need:

- **Last Modified Date**: Identify outdated content without opening it
- **Author Role**: Spot ownership and permission issues quickly
- **Word Count and Reading Time**: Maintain content length standards
- **Featured Image**: Find posts missing featured images for social sharing
- **Template**: See which template is applied to each page
- **Revisions Count**: Identify heavily edited content
- **Menu Order**: Manage hierarchy without database edits
- **Slug**: Audit URL structure for SEO consistency
- **ID**: Quick reference for development tasks
- **Modified By**: Track who made the most recent change
- **Excerpt**: Scan content summaries in the list view
- **Taxonomies**: See assigned categories/tags at a glance
- **Comments Status**: Audit comment policies
- **Ping Status**: Manage cross-site linking settings
- **Child Pages Count**: Visualize page hierarchy

---

## How to Enable Custom Columns in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Content Subtab

Click on the **Core** menu, then click the **Content** subtab.

### Step 3: Enable Custom Columns

Find the **Custom Columns** toggle (under Custom Post Type and Taxonomy Controls) and turn it on. The 14 column toggles expand.

### Step 4: Select the Columns You Want

Toggle on each column you want to appear in the list tables. All are off by default except the ones that match the source defaults (most are on by default when the master toggle is on).


![Custom Columns section with the master toggle and 14 individual column toggles for Last Modified Date, Author Role, Word Count, Reading Time, Featured Image, Template, Revisions Count, Menu Order, Slug, ID, Modified By, Excerpt, Taxonomies, Comments Status, Ping Status, and Child Pages Count](../images/core/custom-columns/custom-columns-options.png)

### Step 5: Save Changes

Click **Save Changes**. Reload the Posts, Pages, or custom post type list table to see the new columns.

---

## The 14 Columns

| Column | Description |
|--------|-------------|
| **Last Modified Date** | When each post was last updated, with exact date and time. |
| **Author Role** | The WordPress user role of each post's author. |
| **Word Count** | Total word count, excluding HTML tags and shortcodes. Sortable. |
| **Reading Time** | Estimated reading time in minutes (200-250 wpm). |
| **Featured Image** | Thumbnail preview with fallback indicator. |
| **Template** | The assigned page template or post template. |
| **Revisions Count** | Number of saved revisions for each post. |
| **Menu Order** | The `menu_order` value, controls display order. |
| **Slug** | The URL slug (permalink) for each post. |
| **ID** | The unique database ID. |
| **Modified By** | Which user made the most recent modification. |
| **Excerpt** | Truncated custom excerpt or auto-generated preview. |
| **Taxonomies** | Assigned categories, tags, custom taxonomy terms. |
| **Comments Status** | Whether comments are open, closed, or disabled. |
| **Ping Status** | Pingback and trackback settings. |
| **Child Pages Count** | Number of child pages (Pages only). |

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Custom Columns** | Master toggle for the entire feature. | Off |
| **Last Modified Date** | Add Last Modified Date column. | On (when master on) |
| **Author Role** | Add Author Role column. | On |
| **Word Count** | Add Word Count column. | On |
| **Reading Time** | Add Reading Time column. | On |
| **Featured Image** | Add Featured Image column. | On |
| **Template** | Add Template column. | On |
| **Revisions Count** | Add Revisions Count column. | On |
| **Menu Order** | Add Menu Order column. | On |
| **Slug** | Add Slug column. | On |
| **ID** | Add ID column. | On |
| **Modified By** | Add Modified By column. | On |
| **Excerpt** | Add Excerpt column. | On |
| **Taxonomies** | Add Taxonomies column. | On |
| **Comments Status** | Add Comments Status column. | On |
| **Ping Status** | Add Ping Status column. | On |
| **Child Pages Count** | Add Child Pages Count column (Pages only). | On |

---

## Developer Notes

The Custom Columns feature adds configurable columns to the post list table. No developer hooks are currently exposed.

**Options used:**
| Option | Type | Default |
|--------|------|---------|
| `enable_custom_columns` | Boolean | `false` |
// Remove a default Classic Monks column
add_filter( 'cm_post_columns', function( $columns ) {
    unset( $columns['post_columns_slug'] );
    return $columns;
} );
```

The `cm_post_columns` filter receives the full columns array; you can add, remove, or reorder entries.

---

## Troubleshooting

### Columns Not Appearing in List Table

**Cause:** Master Custom Columns toggle is off, or the specific column toggle is off.
**Fix:** Enable the master toggle in Core > Content. Verify the specific columns you want are toggled on.

### Column Shows Wrong Data

**Cause:** Another plugin is also modifying the column or has stored incompatible metadata.
**Fix:** Disable other admin customization plugins one at a time to identify the conflict.

### Featured Image Column Is Empty for Posts With Images

**Cause:** The post type does not support featured images, or the image is set as a custom field instead of the standard featured image.
**Fix:** Verify the post type supports `thumbnails` (add `supports => array('thumbnail')` to the post type registration).

### Child Pages Count Shows on Posts

**Cause:** The column is supposed to be Pages-only, but the UI is showing it for all post types.
**Fix:** This is a known display behavior. The count will be 0 for non-hierarchical post types, which is correct.

### Word Count Is Inaccurate

**Cause:** The count includes shortcodes, embedded content, or HTML attributes in the tally.
**Fix:** Word count excludes HTML tags and shortcodes by design. For very shortcodes-heavy posts, the count may be lower than expected.

---

## Frequently Asked Questions

### Do the columns show on all post types?

Yes, the master toggle enables columns on every public post type, including custom post types registered by other plugins. Per-column toggles do not have per-post-type control. If you need a column on some post types but not others, edit the source code or use a child theme's `manage_*_posts_columns` filter.

### Are the columns sortable?

The Word Count, Last Modified Date, ID, Menu Order, and Revisions Count columns are sortable by default (clicking the column header triggers a sort). Other columns display data but are not sortable through the admin UI.

### Do the columns appear in the REST API or WP_Query?

No. The columns are a presentation feature for the admin list table only. They do not change what data is available via WP_Query, the REST API, or any other data access layer. To get the data programmatically, query the post meta directly using `get_post_meta( $post_id, '_your_meta_key', true )`.

### Can I add my own custom column?

Classic Monks does not provide a UI for adding new columns. To add a custom column programmatically, use the `manage_posts_columns` and `manage_posts_custom_column` filters in a small custom plugin or your theme's `functions.php`. The existing Classic Monks columns are good templates for the data structure.

## Related Articles

- [How to Manage Content in Classic Monks (WordPress)](core-content-management.md)
- [How to Use Content Utilities in Classic Monks](core-content-utilities.md)
