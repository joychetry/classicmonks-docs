---
title: "How to Order Post Types in Classic Monks"
slug: order-post-types
description: "Add drag-and-drop reordering to WordPress post type list tables in Classic Monks. Choose which post types are reorderable with per-post-type control."
last_updated: 2026-06-24
author: Joy
reading_time: 6 min
canonical: https://classicmonks.com/docs/order-post-types/
---

# How to Order Post Types in WordPress

> The Order Post Types feature adds drag-and-drop reordering to WordPress post type list tables. Configure which post types are reorderable, with per-post-type control via three modes.

## Key Takeaways

- Drag-and-drop post ordering in the list table (no more manual `menu_order` edits)
- Three modes: only-on selected, except-on selected, or all-post-types
- Per-post-type checkboxes let you pick exactly which post types are reorderable
- Saves the order as `menu_order` in the database, which themes can query with `orderby=menu_order`
- Works with any public post type: post, page, and custom post types

## What Is the Order Post Types feature?

Order Post Types is a Classic Monks feature that adds drag-and-drop reordering to the post list table for any public post type. Once enabled for a post type, you can drag rows up or down to change their display order. The order is saved to WordPress's `menu_order` field, which themes can then use to display content in a custom order (e.g., a featured posts slider, a hand-curated "latest articles" section, a portfolio sorted by importance rather than date).

## Why You Need It

WordPress's default post order is by date (newest first) for most post types, with no built-in UI for manual reordering:

- For blog posts, date order is fine
- For pages, the default is alphabetical, which is rarely what you want
- For portfolio items, "Featured" or "Importance" order matters more than date
- For staff members, you want a hand-curated order (CEO first, then VP, etc.)

Without Order Post Types, achieving a custom order requires either editing `menu_order` in the database or using a separate plugin. Classic Monks bakes it in.

---

## How to Use the Order Post Types feature in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Content Subtab

Click on the **Core** menu, then click the **Content** subtab.

### Step 3: Enable Order Post Types

Toggle on **Order Post Types**. Nested options expand below the toggle.

### Step 4: Choose a Mode

Pick from the **Order Mode** dropdown:

- **Enable only on selected**: Drag-and-drop is enabled only for the post types you check below
- **Enable except on selected**: Drag-and-drop is enabled for all post types EXCEPT the ones you check below
- **Enable on all post types**: Drag-and-drop is enabled for every public post type, no exceptions

For most sites, "Enable only on selected" is the safest default. It gives you explicit control over which post types are reorderable.

### Step 5: Select the Post Types

A list of every public post type on your site appears. Check the ones you want to enable reordering for. Uncheck the ones you want to leave in default order (typically posts, since date order is what readers expect).

### Step 6: Save Changes

Click **Save Changes**.

### Step 7: Reorder Posts in the List Table

Go to the post type's list page (e.g., **Pages > All Pages** for the Pages post type). Each row now has a drag handle (typically a small icon on the left of the row). Click and drag to reorder. The new order saves automatically as you drop.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Order Post Types** | Master toggle. Enables drag-and-drop reordering. | Off |
| **Order Mode** | `only-on`, `except-on`, or `all-post-types`. Controls which post types are reorderable. | `only-on` |
| **Post Type Checkboxes** | Per-post-type control (when Mode is `only-on` or `except-on`). | None checked |

---

## How Themes Use the Custom Order

After reordering posts, your theme or a custom query can display them in the new order by using the `orderby=menu_order` parameter:

```php
// In a theme template or a custom WP_Query
$featured = new WP_Query( array(
    'post_type'      => 'portfolio',
    'posts_per_page' => 10,
    'orderby'        => 'menu_order',
    'order'          => 'ASC',
) );
```

This returns the posts in the order you set with the drag-and-drop UI. Without `orderby=menu_order`, WordPress falls back to date order and ignores the drag-and-drop reordering.

---

## Advanced Options (Developers)

```php
// Customize the post types that appear in the orderable list
add_filter( 'cm_orderable_post_types', function( $types ) {
    // Force 'page' to be orderable even if the user unchecked it
    $types['page'] = 'page';
    return $types;
} );

// Show the menu_order value in the list table for debugging
add_action( 'manage_pages_custom_column', function( $column, $post_id ) {
    if ( $column === 'title' ) {
        echo '<br><small style="color:#999;">menu_order: ' . get_post( $post_id )->menu_order . '</small>';
    }
}, 10, 2 );

// Modify the sort order for archive pages
add_action( 'pre_get_posts', function( $query ) {
    if ( $query->is_main_query() && $query->is_post_type_archive( 'portfolio' ) ) {
        $query->set( 'orderby', 'menu_order' );
        $query->set( 'order', 'ASC' );
    }
} );
```

The `cm_orderable_post_types` filter controls which post types show in the toggle UI. The pre_get_posts example shows how to make the custom order apply to the front-end automatically (without requiring theme changes).

---

## Troubleshooting

### The drag handles are not appearing

**Cause:** The Order Post Types toggle is off, or the post type is not in the enabled list.
**Fix:** Verify the toggle is on in Core > Content. Verify the post type is checked (or that the mode is set to `all-post-types`).

### Drag-and-drop works but the order doesn't persist

**Cause:** JavaScript conflict with another plugin or theme that intercepts the list table.
**Fix:** Open the browser console and look for JavaScript errors. Disable other admin table plugins one at a time to find the conflict. Verify the WP admin is not in a degraded mode (a JS error in another admin area can break drag-and-drop in unrelated list tables).

### The custom order doesn't show on the front-end

**Cause:** The theme is not using `orderby=menu_order` in its queries. WordPress defaults to date order, which ignores your drag-and-drop changes.
**Fix:** Add `orderby=menu_order&order=ASC` to the theme's WP_Query (or use the `pre_get_posts` filter shown above). Test with a default theme (Twenty Twenty-Four) to confirm the custom order is saved in the database.

### The post type doesn't appear in the toggle UI

**Cause:** The post type is not registered as `public => true`, so it's filtered out of the toggle list.
**Fix:** Verify the post type is public. Custom post types registered with `public => false` are intentionally hidden from the admin list table. Adjust the post type registration if it should be orderable.

### Posts show the same order in two browsers

**Cause:** Caching. Some caching plugins cache the admin list table (rare but possible).
**Fix:** Clear the cache, or disable admin caching. The drag-and-drop reordering writes to `menu_order` immediately, so caching should not affect the underlying data.

---

## Related Articles

- [How to Use the Post Type Switcher in Classic Monks](core-post-type-switcher.md)
- [How to Use the Taxonomy Switcher in Classic Monks](core-taxonomy-switcher.md)
- [How to Use Content Management in Classic Monks](core-content-management.md)
- [How to Add Code Snippets in WordPress (PHP, CSS, JS)](../code-manager.md)
