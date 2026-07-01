---
title: "How to Use Bricks Elements in WordPress | CM"
slug: bricks/bricks-elements-overview
description: "Overview of all custom Bricks elements in Classic Monks. 77 elements including animations, content, WooCommerce, gallery, and utility elements."
last_updated: 2026-06-24
author: Joy
reading_time: 5 min
canonical: https://classicmonks.com/docs/bricks/bricks-elements-overview/
---

# How to Use Bricks Elements in WordPress

> Classic Monks adds 77 custom elements to Bricks Builder. Each element is a standalone component that can be dragged into the Bricks editor canvas.

## Key Takeaways

- Category overview of Bricks Builder features
- Multiple features can be enabled independently
- Each feature is a standalone toggle
- Features appear in the Bricks editor after enabling

## What Is This Category?

Classic Monks adds 77 custom elements to Bricks Builder. Each element is a standalone component that can be dragged into the Bricks editor canvas. This is a category overview of all features in this group.

---

## Animation and Visual Effects

- **Dismissible Notice**: A notice that can be dismissed by the visitor
- **Number Counter**: Animated counting numbers for stats and milestones
- **Like/Dislike**: Thumbs up/down voting widget
- **Text Image Split**: Split text and image elements for creative layouts
- **Negative Click**: Click effect that reverses the click direction
- **Falling Items**: Animated falling elements (confetti, rain, snow)
- **Hovering Text Image**: Text that transforms to an image on hover
- **Animated Borders**: CSS-animated border effects
- **Animated Text**: Text animation effects (typewriter, fade, slide)
- **Block Tilt Effect**: 3D tilt effect on hover

## Content and Media

- **Classic Tables**: Data tables with sorting and filtering
- **Image Compare**: Before/after image comparison slider
- **Gallery Zoom**: Image zoom on gallery click
- **Nestable Gallery Zoom**: Zoom for nestable gallery elements
- **PDF Viewer**: Embed PDF documents
- **Infinite Scroller**: Infinite scroll for content loops
- **Lottie Animation**: Lottie animation playback
- **OpenStreetMap**: Map element using OpenStreetMap (free, no API key)
- **Reviews Box**: Product review display
- **Flipbox**: Flip animation between front and back content
- **Timeline**: Vertical or horizontal timeline display
- **Classic Slideshow**: Image slideshow with transitions
- **Frontend Post Submission**: Frontend post creation form

## WooCommerce Elements

- **Saved Amount**: Show amount saved on sale products
- **Percentage Off**: Show discount percentage on sale products
- **WooCommerce Buy Now**: Skip cart and go to checkout
- **Mini Cart Quantity Controls**: Add +/- quantity controls to mini cart
- **Wishlist Icon**: Add to wishlist button
- **Wishlist Query**: Query wishlist items
- **Wishlist Count**: Show wishlist item count

## Gallery and Query Elements

- **Product Gallery Query**: Query WooCommerce products for gallery display
- **Gallery Image ID/URL/Alt/Type/Position**: Dynamic data tags for gallery images
- **Menu**: Query and display WordPress menus
- **Menu Item Title/URL/Target/Classes/Description**: Dynamic data for menu items
- **Menu Item Is Current/Has Children/ID/Parent ID/Object/Object ID/Type**: Menu item conditions
- **Recently Viewed Query**: Query recently viewed products
- **Recently Viewed Count**: Show count of recently viewed products
- **Comments Query**: Query WordPress comments
- **WooCommerce Reviews Query**: Query WooCommerce product reviews

## Utility and Controls

- **Click to Copy**: Copy text or URLs on click
- **Web Share API**: Native browser sharing
- **Element Tooltips**: Custom tooltips for elements
- **Read More/Less Buttons for Text Elements**: Expand/collapse text content
- **Read More/Less for Div**: Expand/collapse div content
- **Tabs Nested: Persist Active State**: Remember active tab across page loads
- **Tabs Nested: Auto Switch**: Auto-switch between tabs on a timer
- **Slider Nested: Enable AutoScroll**: Auto-scroll carousel/slider
- **Slider Nested: Enable Slider Sync Extension**: Sync multiple sliders
- **Monks Cursor**: Custom cursor effect
- **Lazy Loading Controls**: Per-element lazy loading control
- **Preloading Controls**: Per-element preloading control
- **Animate On Scroll**: Scroll-triggered animations
- **Parallax Scroll**: Parallax scrolling effects
- **Text Animation**: Text entrance animations

## How to enable elements

All elements can be enabled individually in the Bricks > Elements subtab. Toggle on the specific elements you need. Each element is independent and can be used without other elements.

After enabling, the element appears in the Bricks editor's element panel. Drag it into the canvas and configure its settings.

## Related Articles

- [How to Set Up the Bricks Integration in WordPress](bricks-setup.md)
- [How to Use Bricks Builder UI Improvements in WordPress](bricks-ui-improvements.md)
- [How to Check Bricks Builder Status in WordPress](bricks-status.md)


### Developer integration

The Bricks elements system registers custom elements via `elements-manager.php`.

**Hooks used:**

- `init` registers all elements (priority 11)
- `init` registers AJAX handlers (priority 9)
- `wp_enqueue_scripts` enqueues element assets conditionally via `cm_bricks_should_enqueue()`

Elements are loaded conditionally -- assets only load on pages using Bricks Builder.
