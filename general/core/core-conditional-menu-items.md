---
title: "How to Use Conditional Menu Items in WordPress"
slug: conditional-menu-items
description: "Control menu item visibility by user role, device type, page context, and more in Classic Monks. Uses advanced AND/OR logic for granular navigation control."
last_updated: 2026-08-03
author: Joy
reading_time: 6 min
canonical: https://classicmonks.com/docs/conditional-menu-items/
---

# How to Use Conditional Menu Items in WordPress

> Conditional Menu Items controls the visibility of WordPress menu items based on user role, device type, page context, and other criteria, with advanced AND/OR logic for granular navigation control.

## Key Takeaways

- Show or hide menu items per user role, device, page, or custom criteria
- Use AND/OR logic to combine multiple conditions and condition groups
- Conditions are evaluated on the frontend and cached briefly for performance
- Works with WordPress nav menus rendered through `wp_get_nav_menu_items()`
- Per-menu-item configuration via the standard WordPress menu editor

## What Are Conditional Menu Items?

Conditional Menu Items is a Classic Monks feature that adds visibility rules to individual menu items in the WordPress menu editor. Once enabled, every menu item gains a "Conditions" panel where you can set rules like "show only to logged-in users", "hide on mobile", or "show only on the Shop page".

The rules are evaluated on the frontend, so the navigation adapts dynamically to the visitor's role, device, and current page.

## Why You Need It

Most sites have navigation that should differ by audience:

- **B2B sites**: Show "Client Portal" only to logged-in users, hide it from visitors
- **E-commerce**: Show "My Account" only to logged-in customers, "Login" only to logged-out visitors
- **Mobile vs desktop**: Show "Call Us" only on mobile, "Live Chat" only on desktop
- **Member sites**: Show member-only pages in the nav only to members

Without Conditional Menu Items, the only options are creating multiple nav menus and switching between them (which is hard to maintain) or using CSS to hide items (which is fragile and does not help with accessibility or SEO).

---

## How to Use Conditional Menu Items in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Content Subtab

Click on the **Core** menu, then click the **Content** subtab.

### Step 3: Enable Conditional Menu Items

In the **Query & Routing Hooks** category, toggle on **Conditional Menu Items**. The toggle is labeled "Control visibility of menu items based on user roles, device type, page context, and more with advanced AND/OR logic."

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Open the WordPress Menu Editor

Go to **Appearance > Menus** in the WordPress admin. Select the menu you want to add conditions to, or create a new one.

### Step 6: Add a Menu Item

Add any menu item (page, post, custom link, category). The standard WordPress menu item panel appears with a new **Conditions** section.

### Step 7: Choose Show or Hide

In the Conditions section, use the **Show when / Hide when** select to set the base behavior. **Show when** displays the item when the conditions match; **Hide when** hides it when the conditions match.

### Step 8: Choose How Groups Combine

Use the **ANY group matches (OR logic)** or **ALL groups match (AND logic)** select to decide how condition groups combine.

### Step 9: Add Conditions

Under each condition group, tick the checkboxes for the conditions you want. Conditions are grouped by category (general, user role, device, page type, and more). Each group can use its own OR or AND logic.

### Step 10: Add More Groups (Optional)

Click **Add condition group** to create additional groups. Each group can hold a different set of conditions.

### Step 11: Save the Menu

Click **Save Menu**. The conditions are now active.

---

## Available Condition Types

Conditions are grouped into categories in the menu editor. The categories and their conditions are:

### General

| Condition | Description |
|-----------|-------------|
| User is logged in | Show when the visitor is authenticated |
| User is logged out | Show when the visitor is anonymous |

### User Role

| Condition | Description |
|-----------|-------------|
| Role: Administrator | Show when the visitor has the Administrator role |
| Role: Editor | Show when the visitor has the Editor role |
| Role: Author | Show when the visitor has the Author role |
| Role: Contributor | Show when the visitor has the Contributor role |
| Role: Subscriber | Show when the visitor has the Subscriber role |

A "Role: <name>" condition is generated for every role on the site, including custom roles.

### Device

| Condition | Description |
|-----------|-------------|
| Mobile Device | Show on mobile devices (uses WordPress mobile detection) |
| Desktop | Show on desktop devices |

### Page Type

| Condition | Description |
|-----------|-------------|
| Front Page | Show on the site front page |
| Blog Page | Show on the blog posts index |
| Single Post | Show on single post pages |
| Any Page | Show on any singular page |
| Archive Page | Show on archive pages |
| Search Results | Show on search results pages |
| 404 Error Page | Show on the 404 page |

### Custom Post Types

A "Single <CPT>" and "<CPT> Archive" condition is generated for every public custom post type. For example, a Portfolio post type adds "Single Portfolio" and "Portfolio Archive".

### Taxonomies

A "<Taxonomy> Archive" condition is generated for every public taxonomy. For example, a Category taxonomy adds "Category Archive", and a Tag taxonomy adds "Tag Archive".

### WooCommerce (when WooCommerce is active)

| Condition | Description |
|-----------|-------------|
| Shop Page | Show on the WooCommerce shop page |
| Product Page | Show on a single product page |
| Product Category | Show on a product category archive |
| Product Tag | Show on a product tag archive |
| Cart Page | Show on the cart page |
| Checkout Page | Show on the checkout page |
| My Account Page | Show on the My Account page |
| Has Products in Cart | Show when the cart has at least one product |
| Cart is Empty | Show when the cart is empty |
| Customer Has Purchased | Show when the logged-in customer has placed at least one order |

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Conditional Menu Items** | Master toggle. Adds the Conditions panel to every menu item. | Off |

Per-menu-item configuration happens in the WordPress menu editor, not in the Classic Monks settings.

---

## Advanced Options (Developers)

Conditions are registered on the `init` hook and filtered on the frontend through `wp_get_nav_menu_items`. The following filter is available to register custom condition types:

```php
// Add a custom condition type
add_filter( 'cm_conditional_menu_conditions', function( $conditions ) {
    $conditions['user_has_subscription'] = array(
        'name'      => 'User has active subscription',
        'callback'  => function() {
            $user = wp_get_current_user();
            return (bool) get_user_meta( $user->ID, '_active_subscription', true );
        },
    );
    return $conditions;
} );
```

- **`init`** calls `register_conditions()` (registers all built-in condition types and fires the `cm_conditional_menu_conditions` filter)
- **`wp_get_nav_menu_items`** calls `filter_menu_items()` (applies the conditions to each menu item on the frontend)
- **`wp_nav_menu_item_custom_fields`** calls `render_menu_item_options()` (renders the Conditions panel in the menu editor)
- **`wp_update_nav_menu_item`** calls `save_menu_item_options()` (saves the condition data to post meta)

The frontend result is cached for 5 minutes per menu and arguments using the WordPress object cache, so heavy condition evaluation is not repeated on every request.

The `cm_conditional_menu_conditions` filter lets you register custom condition types with callbacks. Each condition is an array with a `name` and a `callback` that returns a boolean. Condition data is stored per menu item in the `_cm_menu_item_condition` post meta field.

---

## Troubleshooting

### The Conditions panel is not appearing in the menu editor

**Cause:** The Conditional Menu Items toggle is off, or a JavaScript error is preventing the panel from rendering.
**Fix:** Verify the toggle is on in Core > Content. Open browser dev tools and check the console for errors. Disable other menu-related plugins one at a time to find the conflict.

### A condition is set but the menu item still shows for the wrong audience

**Cause:** The condition was saved but the frontend is serving a cached result.
**Fix:** The feature caches filtered menu results for 5 minutes. Clear the WordPress object cache and wait a few minutes, or test in an incognito window after the cache expires. If you use a caching plugin, exclude the nav menu from cache or clear the full cache.

### The condition works in the editor preview but not on the live site

**Cause:** The condition's callback is failing on the frontend, for example when it depends on data that is only available in the admin.
**Fix:** Check the condition's callback. If it is a custom condition you wrote, ensure the callback works in frontend context. Use `is_admin()` checks if needed.

### I want to hide a menu item from all users (not based on a condition)

**Cause:** You want unconditional hiding, but the menu editor requires conditions to be configured.
**Fix:** Use the WordPress menu editor directly: click the item, then click **Remove**. Conditions are for conditional visibility, not for removal.

### Can I use conditions on Bricks Builder nav elements?

Conditional Menu Items applies to any nav element that renders through `wp_get_nav_menu_items()`, which includes most Bricks Builder nav elements that use the WordPress menu system. If your Bricks nav uses a custom query instead of the WordPress menu system, the conditions do not apply. Check the Bricks nav element's settings to confirm it uses the WordPress menu.

---

## Related Articles

- [How to Use Content Management in WordPress](core-content-management.md)
- [How to Use Bricks AI Builder in WordPress](../bricks/bricks-ai-builder.md)
- [How to Add Code Snippets in WordPress (PHP, CSS, JS)](../code-manager.md)