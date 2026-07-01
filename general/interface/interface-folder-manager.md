---
title: "How to Use the Folder Manager in WordPress | CM"
slug: interface/folder-manager
description: "Organize WordPress media files into folders in Classic Monks. Drag-and-drop organization, multiple folders per item, and automatic categorization."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/interface/folder-manager/
---

# How to Use the Folder Manager in WordPress

> Folder Manager in Classic Monks organizes WordPress media files into virtual folders. Drag-and-drop organization, multiple folders per item, and automatic categorization without changing the file system.

## Key Takeaways

- Single toggle with 3 sub-options (multiple folders, uncategorized removal, media screen visibility)
- Creates a folder system in the Media Library
- Drag-and-drop organization
- Supports multiple folders per item (one file in many folders)
- Virtual folders: doesn't change the actual file system

## What Is the Folder Manager feature?

The default WordPress Media Library is a flat list. For sites with hundreds or thousands of media files, finding the right image or document becomes difficult. The Folder Manager feature adds a virtual folder system to the Media Library, allowing you to organize files into folders.

The folders are "virtual", they don't create directories on the server. The organization is stored in the database as metadata. This means:

- Files are not moved on the server
- The folder structure is independent of the file structure
- One file can exist in multiple folders
- Deleting a folder doesn't delete the files

## Why You Need It

The WordPress Media Library is a flat list of files. For most sites with a few hundred images, this is manageable. But for sites with thousands of files:

- **Navigation**: Scrolling through a flat list to find a specific image is time-consuming
- **Organization**: Grouping files by project, client, season, or type improves workflow
- **Collaboration**: Multiple editors need to know where files are
- **Reusability**: Knowing which images are for which project prevents accidental deletion

Folder Manager solves these problems by adding the organizational layer that the Media Library lacks.

---

## How to Use the Folder Manager in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Interface Tab

Click on the **Interface** menu, then click the **Folders** subtab.

### Step 3: Enable Folder Manager

Toggle on **Enable Folder Manager**. Nested options expand.

### Step 4: Configure Sub-Options

The 3 sub-options include:

- **Multiple Folders Per Item**: Allow a media file to be in more than one folder
- **Uncategorized Removes From All Folders**: When a file is set to "Uncategorized", it is removed from all folders (rather than creating a new "Uncategorized" folder)
- **Show in 'Add New' Media Screen**: Show the folder selector when uploading new files

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Test

Go to the Media Library. The folder tree should appear on the left side. Create a folder, drag files into it, and verify the organization.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Folder Manager** | Master toggle. | Off |
| **Multiple Folders Per Item** | Allow one file in many folders. | On |
| **Uncategorized Removes From All Folders** | Remove from all when uncategorized. | Off |
| **Show in 'Add New' Media Screen** | Folder selector on upload. | On |

---

## What Gets Affected

- The Media Library: folder tree appears on the left
- The media upload: folder selector appears (if enabled)
- The media edit: folder assignment is shown
- The folder operations: create, rename, delete, move files between folders
- The media search: can search within a specific folder

## What Does NOT Get Affected

- The actual file system: files are not moved on the server
- The file URLs: unchanged
- The file names: unchanged
- Other media management plugins: should be compatible

---


## Troubleshooting

### The folder tree is not appearing

**Cause:** The toggle is off, or a plugin conflict is preventing the tree from rendering.
**Fix:** Verify the toggle is on. Disable other media management plugins to find the conflict.

### Files are not being moved to the folder

**Cause:** The drag-and-drop is not working.
**Fix:** Check the browser console for JavaScript errors. The folder manager uses AJAX to update file positions; if the AJAX fails, the files aren't moved.

### The folder tree is empty

**Cause:** No folders have been created yet.
**Fix:** Create a folder by right-clicking in the Media Library sidebar and selecting "New Folder". Or use the "Create New Folder" button.

### I can't find a file after moving it to a folder

**Cause:** The file is in a folder and may not be visible in the "All" view.
**Fix:** Check the folder tree on the left. Click the folder name to see its contents. Files in folders are also visible in the "All" view.

### The folders are not showing in the 'Add New' screen

**Cause:** The "Show in 'Add New' Media Screen" option is off.
**Fix:** Enable the option in the Folders subtab settings.

---

## Related Articles

- [How to Use Folder Download in WordPress](interface-folder-download.md)
- [How to Use Folder Duplication in WordPress](interface-folder-duplication.md)
- [How to Use the Gallery Shortcode in WordPress](interface-gallery-shortcode.md)
- [How to Use Quick Inspect in WordPress](interface-quick-inspect.md)
