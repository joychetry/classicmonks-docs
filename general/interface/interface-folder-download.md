---
title: "How to Use Folder Download in WordPress | CM"
slug: interface/folder-download
description: "Download media folders as ZIP archives in Classic Monks. Download an entire folder's contents as a single ZIP file with one click."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/interface/folder-download/
---

# How to Use Folder Download in WordPress

> Folder Download in Classic Monks adds a one-click ZIP download option to media folders. Download an entire folder's contents as a single ZIP archive with one click.

## Key Takeaways

- Single toggle, no nested options
- Adds a download button to each folder in the Media Library
- Downloads all files in the folder as a ZIP archive
- Requires PHP ZIP extension (standard on most hosts)
- Works with [Folder Manager](interface-folder-manager.md) folders

## What Is the Folder Download feature?

The Folder Download feature adds a download button to each folder in the Media Library. When you click the download button, all files in the folder are packaged into a ZIP archive and downloaded to your computer.

This is useful for:

- Downloading all assets from a specific project folder
- Backing up the contents of a specific folder
- Sharing a folder's contents with clients or team members
- Downloading a set of images for social media

## Why You Need It

The WordPress Media Library doesn't have a built-in way to download multiple files at once:

- **No batch download**: You'd need to download files one at a time
- **No folder download**: There's no "download this folder" option
- **External tools**: Using FTP or SSH to download a folder is too complex for most users

Folder Download solves this by packaging all files in a folder into a ZIP.

---

## How to Use Folder Download in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Interface Tab

Click on the **Interface** menu, then click the **Folders** subtab.

### Step 3: Enable Folder Download

Scroll to **Folder Download (ZIP)** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Go to the Media Library. Click the folder name in the sidebar. Click the download button (or use the folder context menu). The folder contents should be downloaded as a ZIP file.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Folder Download (ZIP)** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- The Media Library: a download button appears for each folder
- The download flow: clicking the button downloads a ZIP of the folder's contents
- The ZIP file: contains all files in the folder, preserving the folder name as the archive name

## What Does NOT Get Affected

- The files themselves: not modified, moved, or deleted
- The folder structure: not changed
- The Media Library display: unchanged
- The file URLs: unchanged

---


## Troubleshooting

### The download button is not showing

**Cause:** The toggle is off, or the PHP ZIP extension is not installed.
**Fix:** Verify the toggle is on. Check if the ZIP extension is installed by creating a `phpinfo.php` file and looking for "zip". If not installed, ask your host to enable it.

### The ZIP file is empty

**Cause:** The folder has no files, or the download is failing.
**Fix:** Verify the folder has files. Check the WordPress error log for download errors. Some hosting environments restrict ZIP creation.

### The download is slow

**Cause:** The folder has many large files (e.g., high-resolution images or videos).
**Fix:** This is expected. ZIP creation takes time proportional to the total file size. For very large folders (100+ files), consider splitting into smaller folders.

### The ZIP file is corrupted

**Cause:** A file in the folder is corrupted or too large for ZIP.
**Fix:** Check the file sizes and integrity. Some hosting environments have memory limits that prevent large ZIP creation. Increase the PHP memory limit.

---

## Related Articles

- [How to Use the Folder Manager in WordPress](interface-folder-manager.md)
- [How to Use Folder Duplication in WordPress](interface-folder-duplication.md)
- [How to Use the Gallery Shortcode in WordPress](interface-gallery-shortcode.md)
- [How to Use Quick Inspect in WordPress](interface-quick-inspect.md)
