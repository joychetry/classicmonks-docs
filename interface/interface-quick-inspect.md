---
title: "How to Use Quick Inspect in WordPress"
slug: quick-inspect
description: "Add a Quick Inspect link to the Media Library in Classic Monks. Opens the media edit page in a modal window for fast editing without leaving the Media Library."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/quick-inspect/
---

# How to Use Quick Inspect in WordPress

> Quick Inspect in Classic Monks adds a "Quick Inspect" link to the Media Library. Opens the media edit page in a modal window, so you can edit file details without navigating away from the Media Library.

## Key Takeaways

- Single toggle, no nested options
- Opens the media edit page in a modal window
- Allows editing file details (title, alt text, caption) without leaving the Media Library
- Faster than the default WordPress flow (which navigates away)
- Works on desktop and tablet (not optimized for mobile)

## What Is the Quick Inspect feature?

The default WordPress Media Library flow for editing a file is:

1. Click the file in the Media Library
2. Navigate to the "Edit Media" page (a full-page load)
3. Edit the file details
4. Click "Update"
5. Navigate back to the Media Library

This is slow and disruptive. The Quick Inspect feature opens the edit page in a modal window (overlay) instead, so you can:

1. Click the "Quick Inspect" link on a file
2. A modal window opens with the edit form
3. Edit the file details
4. Click "Update"
5. Close the modal (you're back in the Media Library)

## Why You Need It

For sites with many media files that need frequent editing:

- **Alt text maintenance**: Quick alt text editing for SEO
- **Caption updates**: Quick caption changes
- **File details**: Quick access to file size, dimensions, URL
- **Bulk editing**: Edit multiple files quickly without navigating back and forth

The Quick Inspect feature saves time for media-heavy workflows.

---

## How to Use Quick Inspect in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Interface Tab

Click on the **Interface** menu, then click the **Folders** subtab.

### Step 3: Enable Quick Inspect

Scroll to **Quick Inspect** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Go to the Media Library. Hover over a file. A "Quick Inspect" link should appear. Click it. A modal window should open with the edit form.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Quick Inspect** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- The Media Library: a "Quick Inspect" link appears on each file
- The edit flow: opens in a modal instead of navigating away
- The media editing: same edit form, but in a modal
- The workflow: faster editing of file details

## What Does NOT Get Affected

- The default WordPress edit flow: still available via the full edit link
- The file itself: unchanged
- The file URLs: unchanged
- The Media Library display: unchanged

---


## Troubleshooting

### The "Quick Inspect" link is not showing

**Cause:** The toggle is off, or a plugin conflict is preventing the link from appearing.
**Fix:** Verify the toggle is on. Disable other media-related plugins to find the conflict. Check the browser console for errors.

### The modal is not opening

**Cause:** A JavaScript error is preventing the modal from rendering.
**Fix:** Check the browser console for errors. The modal requires JavaScript to function.

### The edit form is not saving

**Cause:** The modal's form submission is being blocked.
**Fix:** Check the browser console for AJAX errors. The modal uses AJAX to save changes; if the AJAX fails, the changes aren't saved.

### The modal is not responsive

**Cause:** The modal CSS is not adapting to different screen sizes.
**Fix:** This is a known limitation. The modal is designed for desktop and tablet. On mobile, the full edit page may be more appropriate.

### I want to customize the modal content

**Cause:** The modal shows the standard WordPress edit form.
**Fix:** Custom fields require development work. Check the plugin documentation for available options. For a completely custom modal, you would need to modify the JavaScript directly.

---

## Related Articles

- [How to Use the Folder Manager in WordPress](interface-folder-manager.md)
- [How to Use Folder Download in WordPress](interface-folder-download.md)
- [How to Use Folder Duplication in WordPress](interface-folder-duplication.md)
- [How to Use the Gallery Shortcode in WordPress](interface-gallery-shortcode.md)
