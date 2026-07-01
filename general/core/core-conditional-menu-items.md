---
title: "How to Use Conditional Menu Items in Classic Monks | CM"
slug: conditional-menu-items
description: "Control menu item visibility by user role, device type, page context, and more in Classic Monks. Uses advanced AND/OR logic for granular navigation control."
last_updated: 2026-06-24
author: Joy
reading_time: 6 min
canonical: https://classicmonks.com/docs/conditional-menu-items/
---

# How to Use Conditional Menu Items in WordPress

> Conditional Menu Items controls the visibility of WordPress menu items based on user role, device type, page context, and other criteria, with advanced AND/OR logic for granular navigation control.

## Key Takeaways

- Show or hide menu items per user role, device, page, or custom criteria
- Use AND/OR logic to combine multiple conditions
- Conditions evaluate at page render time (no caching issues)
- Works with WordPress nav menus and Bricks Builder nav elements
- Per-menu-item configuration via the standard WordPress menu editor

## What Are Conditional Menu Items?

Conditional Menu Items is a Classic Monks feature that adds visibility rules to individual menu items in the WordPress menu editor. Once enabled, every menu item gains a "Conditions" panel where you can set rules like "show only to logged-in users", "hide on mobile", or "show only on the Shop page".

The rules are evaluated on every page render, so the navigation adapts dynamically to the visitor's role, device, and current page.

## Why You Need It

Most sites have navigation that should differ by audience:

- **B2B sites**: Show "Client Portal" only to logged-in users, hide it from visitors
- **E-commerce**: Show "My Account" only to logged-in customers, "Login" only to logged-out visitors
- **Mobile vs desktop**: Show "Call Us" only on mobile, "Live Chat" only on desktop
- **Multi-region sites**: Show region-specific menu items only to visitors in that region
- **Member sites**: Show member-only pages in the nav only to members

Without Conditional Menu Items, the only options are creating multiple nav menus and switching between them (which is hard to maintain) or using CSS to hide items (which is fragile and doesn't help with accessibility or SEO).

---

## How to Use Conditional Menu Items in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Content Subtab

Click on the **Core** menu, then click the **Content** subtab.

### Step 3: Enable Conditional Menu Items

Toggle on **Conditional Menu Items**. No nested options are needed.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Open the WordPress Menu Editor

Go to **Appearance > Menus** in the WordPress admin. Select the menu you want to add conditions to (or create a new one).

### Step 6: Add a Menu Item

Add any menu item (page, post, custom link, category). The standard WordPress menu item panel appears.

### Step 7: Expand the Conditions Panel

In the menu item panel, find the new **Conditions** section. Click to expand it. You'll see a list of condition types and a builder for combining them.

### Step 8: Add Conditions

Click **Add Condition**. Pick a condition type (User Role, Device, Page, etc.). Configure the condition's value. Add more conditions if needed.

### Step 9: Choose AND/OR Logic

If you have multiple conditions, choose how they combine:

- **AND**: All conditions must be true for the menu item to show
- **OR**: Any condition being true shows the menu item

For example, "show to Administrators AND on the Shop page" requires both. "show to Administrators OR Editors" requires one or the other.

### Step 10: Save the Menu

Click **Save Menu**. The conditions are now active.

---

## Available Condition Types

Classic Monks provides a set of built-in condition types:

| Condition | Description | Example values |
|-----------|-------------|----------------|
| **User Role** | Show/hide based on the visitor's WordPress role. | Administrator, Editor, Author, Subscriber, custom roles |
| **Logged In** | Show only to logged-in or logged-out visitors. | Logged in, Logged out |
| **Device** | Show only on specific device types (uses WordPress's mobile detection). | Mobile, Desktop, Tablet |
| **Page** | Show only on specific pages. | Any single page, multiple pages |
| **Post Type** | Show only when viewing specific post types. | Post, Page, Portfolio, any custom post type |
| **Category** | Show only when viewing posts in specific categories. | Any single category, multiple categories |
| **Tag** | Show only when viewing posts with specific tags. | Any single tag, multiple tags |
| **Custom Field** | Show only when a specific post meta value is set. | `_featured` is "yes", any meta key/value |
| **User Agent** | Show only to specific browsers or devices (advanced). | Chrome, Safari, Mobile Safari, custom regex |
| **Cookie** | Show only when a specific cookie is set. | Cookie name + value |
| **URL Parameter** | Show only when a query string parameter is present. | `utm_source=email`, any query key/value |
| **Date/Time** | Show only during specific date or time ranges. | "Show only between Jan 1 and Mar 31" |

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Conditional Menu Items** | Master toggle. Adds the Conditions panel to every menu item. | Off |

Per-menu-item configuration happens in the WordPress menu editor, not in the Classic Monks settings.

---

## Advanced Options (Developers)

```php
// Add a custom condition type
add_filter( 'cm_conditional_menu_conditions', function( $conditions ) {
    $conditions['user_has_subscription'] = array(
        'label'       => 'User has active subscription',
        'description' => 'Show only to users with an active subscription',
        'callback'    => function() {
            $user = wp_get_current_user();
            return (bool) get_user_meta( $user->ID, '_active_subscription', true );
        },
    );
    return $conditions;
} );

// Modify the menu items output before render
add_filter( 'wp_nav_menu_objects', function( $items, $args ) {
    foreach ( $items as $key => $item ) {
        // Example: remove all menu items with a specific class
        if ( in_array( 'cm-hide-on-mobile', $item->classes ) ) {
            unset( $items[ $key ] );
        }
    }
    return $items;
}, 10, 2 );
```

The `cm_conditional_menu_conditions` filter lets you register custom condition types with custom callbacks. The `wp_nav_menu_objects` filter is the standard WordPress hook for modifying menu output before render, useful for advanced hiding logic that doesn't fit the condition builder.

---

## Troubleshooting

### The Conditions panel is not appearing in the menu editor

**Cause:** The Conditional Menu Items toggle is off, or a JavaScript error is preventing the panel from rendering.
**Fix:** Verify the toggle is on in Core > Content. Open browser dev tools, check the console for errors. Disable other menu-related plugins one at a time to find the conflict.

### A condition is set but the menu item still shows for the wrong audience

**Cause:** The condition was saved but WordPress's menu cache is serving an old version. Some caching plugins cache nav menus aggressively.
**Fix:** Clear the WordPress object cache. If you're using a caching plugin, exclude the nav menu from cache (or clear the full cache). Test in incognito to bypass browser cache.

### The condition works in the editor preview but not on the live site

**Cause:** The condition's callback function is firing in the admin but failing on the front-end (e.g., it depends on admin-only data).
**Fix:** Check the condition's source code (in the source plugin). If it's a custom condition you wrote, ensure the callback works in both admin and front-end contexts. Use `is_admin()` checks if needed.

### I want to hide a menu item from all users (not based on a condition)

**Cause:** You want unconditional hiding, but the menu editor requires conditions to be configured.
**Fix:** Use WordPress's built-in menu editor: click the item, click **Remove**. Conditions are for conditional visibility, not for removal.

### Can I use conditions on Bricks Builder nav elements?

Conditional Menu Items applies to any nav element that uses `wp_nav_menu()`, which includes most Bricks Builder nav elements. If your Bricks nav uses a custom query instead of `wp_nav_menu()`, the conditions don't apply. Check the Bricks nav element's settings to confirm it uses the WordPress menu system.

---

## Related Articles

- [How to Use Content Management in Classic Monks](core-content-management.md)
- [How to Use Bricks AI Builder in Classic Monks](../bricks/bricks-ai-builder.md)
- [How to Add Code Snippets in WordPress (PHP, CSS, JS)](../code-manager.md)
