---
title: "Use Bricks Interactions in WordPress: Triggers and Actions"
slug: "bricks-interactions"
description: "Enable Bricks interaction triggers and actions in Classic Monks. Create dynamic, interactive page experiences with triggers (when) and actions (then)."
last_updated: 2026-08-04
author: Joy
reading_time: 6 min
canonical: "https://classicmonks.com/docs/bricks-interactions/"
---

# How to Use Bricks Interactions in WordPress

> Bricks Builder lets you build interactions that respond to visitor actions, such as scrolling, clicking, or pressing a key. Classic Monks adds more interaction triggers and actions to Bricks, so you can create dynamic, interactive page experiences.

## Key Takeaways

- Enable interaction triggers and actions in the **Bricks** tab, **Interactions** subtab.
- Each trigger and action is an independent toggle.
- Combine a trigger (when) with an action (then) in the Bricks editor.
- Interactions cover scroll, click, keyboard, layout, and media events.

## What Are Bricks Interactions

Bricks Interactions in Classic Monks are the triggers and actions that the Bricks Builder uses to create dynamic behavior. A **trigger** is the event that starts an interaction, such as scrolling or a key press. An **action** is what happens, such as playing media or toggling a class. Classic Monks organizes these in the **Interactions** subtab. Once enabled, they appear in the Bricks editor's interaction panel, where you pair a trigger with an action.

## Recommendations Before Enabling

- **Enable the interactions you use.** Each trigger and action is independent, so enable only the ones your designs need.
- **Test on a live page.** After building an interaction, check the frontend to confirm it fires as expected.
- **Keep interactions simple.** Too many interactions can make a page feel busy, so use them where they add value.

## Enable Bricks Interactions

### Step 1: Open the Bricks Tab

In your WordPress dashboard, go to **Classic Monks**, then open the **Bricks** tab.

### Step 2: Open the Interactions Subtab

Click the **Interactions** subtab.

### Step 3: Enable the Triggers You Need

Toggle on the triggers, which are the events that start an interaction. Triggers include scroll direction, window resize, double click, right click, key press, swipe, long press, user idle, scroll progress, copy or cut, and more.

### Step 4: Enable the Actions You Need

Toggle on the actions, which are what an interaction does. Actions include copy content, play or pause media, toggle mute, submit a form, go back, reload the page, toggle a class, download a file, and more.

### Step 5: Save

Click **Save (⌘+S)**.

### Step 6: Build an Interaction

Open a page in the Bricks editor, select an element, and add an interaction. Choose a trigger (when) and an action (then), and set any options.

## Verify It Works

After enabling and building an interaction, verify it:

- Open the page in the Bricks editor and set up the interaction.
- View the page on the frontend and trigger the event, such as scrolling or clicking.
- Confirm the action fires as expected.

If a trigger or action does not appear, confirm its toggle is on and the editor was refreshed.

## Common Use Cases

### Play a video when it scrolls into view

Use the **Scroll Progress** trigger and the **Play Media** action to start a video when the visitor scrolls to it. The video plays automatically as it comes into view.

### Copy a link on click

Use the **Double Click** or **Click** trigger and the **Copy Link to Clipboard** action so a visitor can copy a link by interacting with an element.

### Toggle a class on scroll

Use the **Scroll Direction** trigger and the **Toggle Class** action to change an element's style based on scroll direction. For example, shrink a header when the visitor scrolls down.

### Show a password field toggle

Use the **Click** trigger and the **Toggle Password Visibility** action so a visitor can show or hide a password field.

## Troubleshooting

### A trigger or action does not appear in the editor

**Cause:** The toggle is off, or the Bricks editor is showing a cached view.
**Fix:** Confirm the trigger or action is enabled in the **Interactions** subtab and refresh the Bricks editor.

### The interaction does not fire

**Cause:** The trigger and action are not paired correctly, or the event is not what you expect.
**Fix:** Review the interaction setup, confirm the trigger and action are both enabled, and test the exact event.

### An action works on one page but not another

**Cause:** The element or context differs on the other page.
**Fix:** Confirm the element exists and the interaction is set up on the target page.

## Related Articles

- [How to Use Bricks Conditions in WordPress](bricks-conditions-overview.md)
- [How to Use Bricks Dynamic Data in WordPress](bricks-dynamic-data-overview.md)
- [How to Complete the Bricks Initial Setup in WordPress](bricks-setup.md)

---

*Written by Joy. Last updated August 4, 2026. Tested with WordPress 6.x and Classic Monks 2.1.0.*

<!-- schema: Article, TechArticle -->
<!-- schema: BreadcrumbList -->