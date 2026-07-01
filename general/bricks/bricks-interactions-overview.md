---
title: "How to Use Bricks Interactions in WordPress | CM"
slug: bricks/bricks-interactions
description: "Overview of all interaction triggers and actions in Classic Monks. 43 triggers and actions for creating dynamic, interactive page experiences."
last_updated: 2026-06-24
author: Joy
reading_time: 5 min
canonical: https://classicmonks.com/docs/bricks/bricks-interactions/
---

# How to Use Bricks Interactions in WordPress

> Classic Monks adds 43 interaction triggers and actions to Bricks Builder. Create dynamic, interactive experiences with triggers (when) and actions (then).

## Key Takeaways

- Category overview of Bricks Builder features
- Multiple features can be enabled independently
- Each feature is a standalone toggle
- Features appear in the Bricks editor after enabling

## What Is This Category?

Classic Monks adds 43 interaction triggers and actions to Bricks Builder. Create dynamic, interactive experiences with triggers (when) and actions (then). This is a category overview of all features in this group.

---

## Triggers (When)

- **Scroll Direction**: Trigger on scroll direction change (up/down)
- **Window Resize**: Trigger on browser window resize
- **Tab Active**: Trigger when browser tab becomes active
- **Double Click**: Trigger on double-click
- **Right Click**: Trigger on right-click
- **Focus Within**: Trigger when element receives focus
- **System Theme Change**: Trigger on light/dark mode change
- **Checkbox**: Trigger on checkbox state change
- **Paste Text**: Trigger on text paste
- **Network**: Trigger on network status change (online/offline)
- **Print Requested**: Trigger when print dialog is opened
- **Key Press**: Trigger on specific key press
- **Swipe Gestures**: Trigger on swipe (left/right/up/down)
- **Long Press**: Trigger on long press (hold)
- **User Idle / Inactive**: Trigger after user inactivity
- **Scroll Progress**: Trigger at specific scroll percentage
- **Copy / Cut**: Trigger on copy or cut action
- **Device Orientation**: Trigger on device tilt
- **Before Unload**: Trigger when leaving the page
- **Scroll Stop**: Trigger when scrolling stops
- **Fullscreen Change**: Trigger on fullscreen toggle

## Actions (Then)

- **Copy Content**: Copy text to clipboard
- **Play Media**: Start playing audio/video
- **Pause Media**: Pause audio/video
- **Toggle Mute**: Toggle audio mute
- **Submit Form**: Submit a form
- **Focus Element**: Focus on a specific element
- **Disable Element**: Disable an element
- **Go Back**: Navigate to previous page
- **Print Page**: Open print dialog
- **Reload Page**: Reload the current page
- **Go Forward**: Navigate to next page
- **Remove Element**: Remove element from DOM
- **Toggle Body Scroll**: Enable/disable body scrolling
- **Save/Restore Scroll Position**: Save and restore scroll position
- **Toggle Class**: Add/remove CSS classes
- **Animate Number**: Animate a number change
- **Download File**: Trigger file download
- **Copy Link to Clipboard**: Copy a URL to clipboard
- **Toggle Password Visibility**: Show/hide password text
- **Toggle Fullscreen**: Enter/exit fullscreen mode
- **Lazy Load Trigger**: Trigger lazy loading manually
- **Set Cookie**: Set a browser cookie

## How to use interactions

All triggers and actions can be enabled in the Bricks > Interactions subtab. Once enabled, they appear as options in the Bricks editor's interaction panel. Combine triggers and actions to create dynamic, interactive page experiences.

## Related Articles

- [How to Set Up the Bricks Integration in WordPress](bricks-setup.md)
- [How to Use Bricks Builder UI Improvements in WordPress](bricks-ui-improvements.md)
- [How to Check Bricks Builder Status in WordPress](bricks-status.md)


### Developer integration

The Bricks interactions system registers triggers and actions via WordPress hooks in `interactions/class-interactions-triggers.php` and `interactions/class-interactions-actions.php`.

**Hooks used:**

- `init` registers interaction triggers and actions (priority 100)
- `wp_enqueue_scripts` enqueues interaction assets

Custom interactions are added by registering PHP classes that implement the trigger/action interface.
