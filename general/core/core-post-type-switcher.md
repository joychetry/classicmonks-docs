---
title: "How to Use the Post Type Switcher in Classic Monks | CM"
slug: post-type-switcher
description: "Change a post from one type to another in Classic Monks (post to page, page to custom post type) while preserving metadata, custom fields, and compatible taxonomies."
last_updated: 2026-06-24
author: Joy
reading_time: 6 min
canonical: https://classicmonks.com/docs/post-type-switcher/
---

# How to Use the Post Type Switcher in WordPress

> The Post Type Switcher lets you change a post from one type to another (for example, post to page, or page to a custom post type) while preserving metadata, custom fields, and compatible taxonomies.

## Key Takeaways

- Change a post's type from the edit screen via a dropdown in the Publish meta box
- Compatible taxonomies (categories, tags, custom taxonomies) move with the post
- Incompatible taxonomies are dropped (e.g., "Categories" don't apply to pages)
- The post's URL changes to match the new type's permalink structure (set up a redirect if needed)
- Works with any public post type: post, page, attachment, and custom post types

## What Is the Post Type Switcher?

The Post Type Switcher is a small but powerful Classic Monks feature that adds a **Post Type** dropdown to the post edit screen. The dropdown appears in the Publish meta box (right sidebar, classic editor) and lists every public post type registered on your site. Pick a different type, save the post, and the post is now a member of that new type.

The switch preserves all compatible metadata and custom fields, and it moves the post into any taxonomies that exist for the new type. Incompatible fields (e.g., post categories when switching to a page) are dropped cleanly without errors.

## Why You Need It

WordPress's core admin has no native way to change a post's type. If you originally published something as a "Post" and later realized it should be a "Page" (or a custom post type like "Portfolio"), the default options are:

- Copy the content into a new post of the right type, then delete the original
- Edit the database directly via phpMyAdmin (risky, breaks meta queries, no UI)
- Install a dedicated plugin (yet another plugin to manage)

The Post Type Switcher in Classic Monks does the same thing as a one-click type change, without the manual copy or the database surgery.

---

## How to Use the Post Type Switcher in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Content Subtab

Click on the **Core** menu, then click the **Content** subtab.

### Step 3: Enable Post Type Switcher

Toggle on **Post Type Switcher**. No nested options are needed for this feature; the toggle is a single switch.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Open Any Post's Edit Screen

In the WordPress admin, go to **Posts > All Posts** (or any post type list), and click **Edit** on the post you want to switch.

### Step 6: Use the New "Post Type" Dropdown

In the right sidebar's **Publish** meta box, find the new **Post Type** dropdown. It lists every public post type on your site. Select the target type from the dropdown.

### Step 7: Save the Post

Click **Update** in the Publish meta box. The post is now the new type. The post ID, all compatible meta, all compatible taxonomies, and the content body are preserved.

### Step 8: Verify the Switch

Reload the post list filtered by the new type. Your post should appear in the new type's list. The URL slug also updates to match the new type's permalink structure.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Post Type Switcher** | Master toggle. Adds the dropdown to the post edit screen. | Off |

There are no per-post-type controls; the toggle is global.

## What Gets Preserved vs. Dropped

| Data Type | Switched to compatible type | Switched to incompatible type |
|----------|------------------------------|--------------------------------|
| Post title, content, excerpt | Preserved | Preserved |
| Featured image | Preserved | Preserved |
| Custom fields (post meta) | Preserved | Preserved |
| Compatible taxonomies (e.g., post categories when switching from post to custom-post-type-with-categories) | Preserved | N/A |
| Incompatible taxonomies (e.g., post categories when switching to a page) | N/A | Dropped |
| Post author | Preserved | Preserved |
| Post date | Preserved | Preserved |
| Post slug (URL) | **Regenerated** to match new type's permalink | **Regenerated** |
| Comments | Preserved (comments are a separate post type) | Preserved |
| Page-specific attributes (menu order, page template) | N/A | Set to defaults |
| Post format | Preserved if new type supports it | Dropped if new type doesn't support post formats |

---

## Bulk Switch via List Table

The Post Type Switcher also adds a bulk action to the post list table:

1. Go to **Posts > All Posts** (or any post type list)
2. Check the boxes next to the posts you want to switch
3. From the **Bulk Actions** dropdown, select **Change post type**
4. Click **Apply**
5. A confirmation page shows the selected posts and the target type dropdown
6. Pick the target type and confirm

Bulk switching is useful for migrating a category of posts (e.g., 30 "news" posts that should all become "press releases").

---

## Developer Notes

The Post Type Switcher uses a single filter to control which post types are eligible for switching:

```php
// The actual filter used by the plugin
add_filter('cm_post_type_filter', function($args) {
    // $args contains ['public' => true, 'show_ui' => true]
    // Modify to include/exclude specific post types
    return $args;
});
```

**Options used:**
| Option | Type | Default |
|--------|------|---------|
| `enable_post_type_switcher` | Boolean | `false` |

The switcher is loaded via `cm_post_type_switcher.php` in `functions/core/content/`.
---

## Troubleshooting

### The dropdown is not appearing on the edit screen

**Cause:** The Post Type Switcher toggle is off, or the post type you're editing is not in the allowed types list.
**Fix:** Verify the toggle is on in Core > Content. If the toggle is on but the dropdown still doesn't appear, your theme may be removing the Publish meta box. Switch to a default theme (Twenty Twenty-Four) to confirm.

### The post type is listed but the switch fails

**Cause:** The new type's rewrite rules are not registered. This happens with custom post types registered by a plugin that isn't active, or with a custom post type whose `public` setting is false.
**Fix:** Verify the target post type is registered and public. Use `get_post_types( [ 'public' => true ] )` in `functions.php` or a debug snippet to see what types are available.

### Comments disappeared after switching

**Cause:** Comments are a separate post type (`comment`), not post meta. They should be preserved. If comments are missing, the new type may not have `comments_open` or `comment_status` set correctly.
**Fix:** Edit the post after switching, set the Discussion meta box to "Allow comments", and save. Comments will reappear (they were never deleted, just not displayed because the new type's default comment status was "closed").

### The post's URL changed and inbound links are now 404

**Cause:** Switching the post type changes the URL slug to match the new type's permalink. Inbound links to the old URL now 404.
**Fix:** Set up a 301 redirect from the old URL to the new URL. Use Classic Monks' [Redirection and Logging](core-logs.md) feature to track the 404s and create redirects.

### Bulk switch is only applying to some posts

**Cause:** Some posts may be in a status that doesn't allow the switch (e.g., trash, draft), or the user lacks the `edit_posts` capability for the target type.
**Fix:** Verify the post statuses are compatible. Check the user's capabilities (an Editor can switch to post and page but may not have access to custom post types).

---

## Related Articles

- [How to Use the Taxonomy Switcher in Classic Monks](core-taxonomy-switcher.md)
- [How to Order Post Types in Classic Monks](core-order-post-types.md)
- [How to Use Content Management in Classic Monks](core-content-management.md)
- [How to Use Logs in Classic Monks](core-logs.md)
