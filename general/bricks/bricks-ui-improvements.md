---
title: "How to Use Bricks Builder UI Improvements in WordPress | CM"
slug: bricks/bricks-ui-improvements
description: "Enhance the Bricks Builder editor interface in Classic Monks. UI improvements include active element highlighting, style panel enhancements, and better control separators."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/bricks/bricks-ui-improvements/
---

# How to Use Bricks Builder UI Improvements in WordPress

> Bricks Builder UI Improvements in Classic Monks enhance the Bricks editor interface. Includes active element highlighting, style panel enhancements, control separators, and setting indicators.

## Key Takeaways

- Master toggle with 4 sub-options
- Active Element Highlighting: visual indicator on the canvas
- Style Panel Enhancements: improved style panel layout
- Control Separator Enhancements: better visual separators between controls
- Setting Indicator Enhancements: visual indicators for set values

## What Are the Bricks UI Improvements?

The Bricks Builder UI Improvements feature adds visual enhancements to the Bricks editor interface. These improvements make the editor easier to use by adding visual cues, better organization, and clearer feedback.

The 4 sub-options include:

1. **Active Element Highlighting**: Shows a colored border around the currently selected element on the canvas, making it easier to see which element is active
2. **Style Panel Enhancements**: Improves the layout and visual hierarchy of the style panel
3. **Control Separator Enhancements**: Adds better visual separators between control groups
4. **Setting Indicator Enhancements**: Shows visual indicators (dots, icons) when a setting has a value

## Why You Need It

The default Bricks editor is functional but can be hard to navigate when building complex layouts:

- **Element identification**: Without highlighting, it's hard to see which element is selected
- **Style organization**: The style panel can be overwhelming without clear separators
- **Value awareness**: Without indicators, you can't tell which settings have values at a glance

The UI improvements solve these problems with subtle visual enhancements.

---

## How to Enable Bricks UI Improvements

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Bricks Tab

Click on the **Bricks** menu, then the **Initial Setup** subtab.

### Step 3: Enable UI Improvements

Toggle on **Enable Builder UI Improvements**. The 4 sub-options expand.

### Step 4: Configure Sub-Options

Select which improvements to enable:
- **Active Element Highlighting**: Recommended (always useful)
- **Style Panel Enhancements**: Recommended (improves organization)
- **Control Separator Enhancements**: Optional (visual preference)
- **Setting Indicator Enhancements**: Recommended (shows set values)

### Step 5: Save and Test

Click **Save Changes**. Open the Bricks editor and verify the improvements are visible.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Builder UI Improvements** | Master toggle. | Off |
| **Active Element Highlighting** | Highlight selected element on canvas. | On |
| **Style Panel Enhancements** | Improved style panel layout. | On |
| **Control Separator Enhancements** | Better visual separators. | On |
| **Setting Indicator Enhancements** | Show indicators for set values. | On |

---

## What Gets Affected

- The Bricks editor interface: visual enhancements applied
- The canvas: active element highlighted with a colored border
- The style panel: improved layout and organization
- The control groups: better visual separators
- The settings panel: visual indicators for set values

## What Does NOT Get Affected

- The Bricks editor functionality: unchanged (visual only)
- The frontend: no effect on the live site
- The Bricks data: unchanged (visual modifications only)
- Performance: negligible overhead (CSS-only enhancements)

---

## Advanced Options (Developers)

The Bricks UI improvements module injects CSS and JS for editor enhancements.

**Hooks used:**

- `wp_enqueue_scripts` enqueues UI improvement assets via `cm_bricks_should_enqueue()`
- `admin_enqueue_scripts` enqueues admin-side UI assets

The highlight colors, border widths, and excluded elements are configured through the plugin settings UI, not via WordPress filters. CSS is injected inline via `wp_head` in `bricks-functions.php`.


## Troubleshooting

### The highlighting is not showing

**Cause:** The toggle is off, or a Bricks update changed the canvas rendering.
**Fix:** Verify the toggle is on. Check for Bricks updates that may have changed the canvas structure. The highlighting uses CSS targeting specific Bricks classes.

### The style panel looks wrong

**Cause:** The enhancements conflict with a Bricks theme or plugin.
**Fix:** Disable the style panel enhancements and test without them. Re-enable after a Bricks update if the issue is resolved.

### The setting indicators are not showing

**Cause:** The indicators are CSS-only and may be hidden by theme CSS.
**Fix:** Check the browser's DevTools for CSS conflicts. Add a more specific selector if needed.

---

## Related Articles

- [How to Use Bricks Builder UI Improvements in WordPress](bricks-ui-improvements.md)
- [How to Use Bricks AI Builder in WordPress](bricks-ai-builder.md)
- [How to Use Live HTML to Bricks in WordPress](bricks-live-html.md)
