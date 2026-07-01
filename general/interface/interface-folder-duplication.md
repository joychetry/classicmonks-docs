---
title: "How to Use Folder Duplication in WordPress | CM"
slug: folder-duplication
description: "Duplicate media folders in Classic Monks. Create a complete copy of a folder structure including all nested folders and files."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/folder-duplication/
---

# How to Use Folder Duplication in WordPress

> Folder Duplication in Classic Monks creates a complete copy of a folder structure, including all nested folders and files. Duplicate an entire folder tree with one click.

## Key Takeaways

- Single toggle, no nested options
- Duplicates the entire folder structure (including nested folders and files)
- Files are not physically duplicated (only the folder metadata is copied)
- One-click duplication from the folder context menu
- Works with [Folder Manager](interface-folder-manager.md) folders

## What Is the Folder Duplication feature?

The Folder Duplication feature adds a "Duplicate" option to the folder context menu in the Media Library. When you duplicate a folder, the system copies:

- The folder structure (including nested sub-folders)
- All file assignments (files in the original folder are also assigned to the duplicated folder)
- The folder hierarchy

The files themselves are NOT duplicated. This means:

- The duplicated folder references the same files as the original
- If you delete a file from the duplicated folder, it is also removed from the original
- The duplication is lightweight and fast

## Why You Need It

For sites with complex folder structures, duplicating a folder is useful for:

- **Project templates**: Duplicate a standard project folder structure for a new project
- **Client work**: Duplicate a client's folder for a new client
- **Seasonal content**: Duplicate last year's seasonal folder for this year
- **A/B testing**: Create a copy of a folder to experiment with

Since files aren't physically duplicated, the disk space usage doesn't change.

---

## How to Use Folder Duplication in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Interface Tab

Click on the **Interface** menu, then click the **Folders** subtab.

### Step 3: Enable Folder Duplication

Scroll to **Folder Duplication** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Go to the Media Library. Right-click a folder in the sidebar. Select "Duplicate" from the context menu. A new folder with the same name (and "(Copy)" suffix) should appear.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Folder Duplication** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- The Media Library: a "Duplicate" option appears in the folder context menu
- The folder structure: the duplicated folder references the same files
- The folder hierarchy: nested folders are also duplicated

## What Does NOT Get Affected

- The files themselves: not duplicated (only references are copied)
- The disk space: unchanged
- The file URLs: unchanged
- The original folder: unchanged (the copy is a new folder)

---


## Troubleshooting

### The duplicate option is not showing

**Cause:** The toggle is off, or the folder context menu is not loading.
**Fix:** Verify the toggle is on. Check the browser console for errors. The folder manager's JavaScript must be loaded for the context menu to work.

### The duplicated folder has the same files

**Cause:** This is the default behavior (file references, not copies).
**Fix:** This is by design. The duplicated folder references the same files as the original. To get separate files, use the "new_references" behavior or manually upload new files.

### The nested folders are not being duplicated

**Cause:** A plugin conflict is preventing the nested duplication.
**Fix:** Disable other folder-related plugins. Test with a simple folder structure (one parent with one child).

### The duplication is slow

**Cause:** The folder has many nested folders and files.
**Fix:** For very large folder trees, the duplication may take a few seconds. This is expected.

---

## Related Articles

- [How to Use the Folder Manager in WordPress](interface-folder-manager.md)
- [How to Use Folder Download in WordPress](interface-folder-download.md)
- [How to Use the Gallery Shortcode in WordPress](interface-gallery-shortcode.md)
- [How to Use Quick Inspect in WordPress](interface-quick-inspect.md)
