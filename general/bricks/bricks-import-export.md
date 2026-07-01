---
title: "How to Import and Export Bricks Settings in WordPress | CM"
slug: bricks-import-export
description: "Import and export Bricks Builder settings in Classic Monks. Transfer theme styles, global settings, and templates between sites."
last_updated: 2026-06-24
author: Joy
reading_time: 5 min
canonical: https://classicmonks.com/docs/bricks-import-export/
---

# How to Import and Export Bricks Settings in WordPress

> Bricks Import/Export in Classic Monks lets you transfer Bricks Builder settings between sites. Import theme styles, global settings, and templates for quick site setup.

## Key Takeaways

- Category overview of Bricks Builder features
- Multiple features can be enabled independently
- Each feature is a standalone toggle
- Features appear in the Bricks editor after enabling

## What Is This Category?

Bricks Import/Export in Classic Monks lets you transfer Bricks Builder settings between sites. Import theme styles, global settings, and templates for quick site setup. This is a category overview of all features in this group.

---

## Import Options

The Import/Export subtab has 3 import features:

1. **Import Global Settings**: Import Bricks global settings (colors, typography, spacing)
2. **Import Theme Styles**: Import Bricks theme styles (predefined style combinations)
3. **Import Templates**: Import Bricks templates for reuse across sites

These features are useful for:
- Setting up multiple sites with the same Bricks configuration
- Migrating a Bricks site to a new domain
- Sharing Bricks configurations between team members
- Backing up your Bricks settings

## How to import

1. On the source site, export the settings (this happens automatically when you save)
2. On the destination site, go to Bricks > Import/Export
3. Select the import type (Global Settings, Theme Styles, or Templates)
4. Upload or paste the import data
5. Save Changes

After importing, verify the settings are applied correctly by opening the Bricks editor.

## Related Articles

- [How to Set Up the Bricks Integration in WordPress](bricks-setup.md)
- [How to Use Bricks Builder UI Improvements in WordPress](bricks-ui-improvements.md)
- [How to Check Bricks Builder Status in WordPress](bricks-status.md)


### Developer integration

The Bricks import/export feature uses AJAX handlers for settings transfer.

**AJAX endpoints:**

- `wp_ajax_cm_export_bricks_options` exports all Bricks settings as JSON
- `wp_ajax_cm_import_bricks_options` imports settings from JSON
- `wp_ajax_cm_reset_bricks_options` resets to defaults

The import/export covers global settings, theme styles, and templates stored in the `cm_options` table.
