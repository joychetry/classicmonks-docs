---
title: "How to Use the Gallery Shortcode in WordPress | CM"
slug: gallery-shortcode
description: "Add a [gallery] shortcode for folder-based media galleries in Classic Monks. Dynamically display all images from a media folder as a responsive gallery."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/gallery-shortcode/
---

# How to Use the Gallery Shortcode in WordPress

> Gallery Shortcode in Classic Monks adds a `[cm_gallery]` shortcode that dynamically displays all images from a media folder as a responsive gallery. Update the folder, and the gallery updates automatically.

## Key Takeaways

- Single toggle, no nested options
- `[cm_gallery id="X"]` shortcode displays all images from a folder
- Responsive gallery with configurable columns and lightbox
- Dynamic: updates when files are added or removed from the folder
- Works with [Folder Manager](interface-folder-manager.md) folders

## What Is the Gallery Shortcode feature?

The Gallery Shortcode feature adds a `[cm_gallery]` shortcode that displays all images from a specific media folder as a responsive gallery. The gallery updates dynamically when the folder contents change.

This is useful for:

- **Portfolio galleries**: Create a gallery from a "portfolio" folder
- **Product images**: Display all images from a "product-images" folder
- **Event galleries**: Show all photos from an event folder
- **Documentation**: Display all screenshots from a "docs" folder

## Why You Need It

The default WordPress gallery shortcode requires manually selecting individual images:

- **Manual selection**: You must choose each image individually
- **No dynamic updates**: When new images are added, the gallery doesn't update
- **No folder support**: The default gallery uses the post's attached media, not a folder

The `[cm_gallery]` shortcode solves this by using folders instead of manual selection.

---

## How to Use the Gallery Shortcode in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Interface Tab

Click on the **Interface** menu, then click the **Folders** subtab.

### Step 3: Enable Gallery Shortcode

Scroll to **Gallery Shortcode** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Create a Folder and Add Images

Go to the Media Library, create a folder (e.g., "portfolio"), and drag images into it.

### Step 6: Use the Shortcode

Add the shortcode to any post, page, or widget:

```html
[cm_gallery id="123"]
```

Replace `123` with the folder ID. To find the folder ID, hover over the folder name in the sidebar and look at the URL or tooltip.

### Step 7: Test

Visit the page on the frontend. The gallery should display all images from the folder in a responsive grid.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Gallery Shortcode** | Master toggle. | Off |

The shortcode accepts these attributes:

- `id`: The folder ID (required)
- `columns`: Number of columns (default: 3)
- `size`: Image size (default: "medium", options: "thumbnail", "medium", "large", "full")
- `link`: Link behavior (default: "file", options: "file", "none")
- `orderby`: Sort order (default: "menu_order", options: "date", "title", "rand")

Example:
```html
[cm_gallery id="123" columns="4" size="thumbnail" orderby="date"]
```

---

## What Gets Affected

- The page content: the `[cm_gallery]` shortcode is rendered as a responsive gallery
- The folder contents: the gallery updates when files are added or removed
- The page load: additional CSS/JS may be loaded for the lightbox

## What Does NOT Get Affected

- The folder: the gallery is read-only (doesn't modify the folder)
- The original images: not affected
- The Media Library: not affected
- The page performance: minimal impact (the gallery is lazy-loaded)

---


## Troubleshooting

### The gallery is not showing

**Cause:** The toggle is off, or the folder ID is wrong.
**Fix:** Verify the toggle is on. Check the folder ID (hover over the folder name in the sidebar). The folder must contain at least one image.

### The gallery shows broken images

**Cause:** The image URLs are wrong, or the files have been deleted from the server.
**Fix:** Verify the images exist in the Media Library. Check the browser console for 404 errors on the image URLs.

### The gallery is not responsive

**Cause:** A theme or plugin is overriding the gallery CSS.
**Fix:** Check the browser's DevTools for the gallery container. Ensure the CSS is loading (look for `cm-gallery` in the page source).

### The gallery is slow to load

**Cause:** The folder has many high-resolution images.
**Fix:** Use the `size` attribute to display smaller images (e.g., "thumbnail" instead of "large"). The gallery loads images lazily by default.

### The gallery shows duplicate images

**Cause:** Multiple files have the same image (e.g., duplicates in the Media Library).
**Fix:** The gallery shows all files in the folder. Use the "Remove from all" option to remove duplicates, or use the folder download feature to back up and clean the folder.

---

## Related Articles

- [How to Use the Folder Manager in WordPress](interface-folder-manager.md)
- [How to Use Folder Download in WordPress](interface-folder-download.md)
- [How to Use Folder Duplication in WordPress](interface-folder-duplication.md)
- [How to Use Quick Inspect in WordPress](interface-quick-inspect.md)
