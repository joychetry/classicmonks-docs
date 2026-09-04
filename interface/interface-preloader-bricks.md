---
title: "Disable the Preloader in the Bricks Builder in WordPress"
slug: "interface-preloader-bricks"
description: "Turn off the preloader while editing in the Bricks Builder in Classic Monks. Prevent the loading animation from interfering with your design workflow."
last_updated: 2026-08-04
author: Joy
reading_time: 3 min
canonical: "https://classicmonks.com/docs/interface-preloader-bricks/"
---

# How to Disable the Preloader in the Bricks Builder

> The preloader shows a loading animation while a page loads. When you design a page in the Bricks Builder, that animation can get in the way of your work. Classic Monks lets you turn off the preloader while you are editing in the Bricks Builder.

## Key Takeaways

- Turn off the preloader while editing in the Bricks Builder.
- The preloader still works for visitors on the frontend.
- A single toggle in the **Preloader** subtab.
- Works alongside the **Enable Preloader** master toggle.

## What Is Disable Preloader in the Bricks Builder

Disable Preloader in the Bricks Builder is an option in the Classic Monks **Interface** tab, **Preloader** subtab. When the preloader is enabled and you are editing a page in the Bricks Builder, the preloader can appear and interfere with the visual editor. This toggle stops the preloader from showing while you work in the Bricks Builder, while leaving it active for visitors on the frontend.

## Recommendations Before Using

- **Enable the preloader first.** This option only works when **Enable Preloader** is on, so turn the preloader on before you use it.
- **Understand the scope.** The toggle affects only the Bricks Builder editor, not the frontend. Visitors still see the preloader.
- **Test in the editor.** After enabling, open the Bricks Builder to confirm the preloader no longer appears while you edit.

## Disable the Preloader in the Bricks Builder

### Step 1: Open the Interface Tab

In your WordPress dashboard, go to **Classic Monks**, then open the **Interface** tab.

### Step 2: Open the Preloader Subtab

Click the **Preloader** subtab.

### Step 3: Enable the Preloader

Toggle on **Enable Preloader** so the preloader is active.

### Step 4: Disable It in the Bricks Builder

Toggle on **Disable Preloader inside Bricks Builder**. The preloader will no longer show while you edit in the Bricks Builder.

### Step 5: Save and Test

Click **Save (⌘+S)**. Open a page in the Bricks Builder and confirm the preloader does not appear, then check the frontend to confirm visitors still see it.

## Verify It Works

After saving, verify the change:

- Open a page in the Bricks Builder and confirm the preloader does not appear.
- View the site on the frontend and confirm the preloader still shows for visitors.
- Confirm the **Enable Preloader** toggle is on.

If the preloader still appears in the editor, confirm both toggles are set correctly and the page was refreshed.

## Common Use Cases

### Design without the preloader interrupting

A designer builds a page in the Bricks Builder and finds the preloader flashes on every reload. They toggle on **Disable Preloader inside Bricks Builder**. The editor is clean and the design workflow is uninterrupted, while visitors still see the preloader.

### Test the preloader only on the frontend

A developer wants to verify the preloader behavior without it interfering in the editor. They disable it in the Bricks Builder and check the frontend. The preloader works for visitors and stays out of the way during editing.

### Keep the preloader for the live site

A site uses a preloader for its brand experience, but the developer does not want it to interfere while editing. They disable it in the Bricks Builder. The live site keeps its branded preloader, and the editor stays clean for the developer.

### A clean editing environment for a team

A team that builds and edits pages in the Bricks Builder does not want the preloader to flash during their work. They disable it in the Bricks Builder for the whole team. The editors get a clean environment, and visitors still see the preloader on the live site.

## Troubleshooting

### The preloader still shows in the Bricks Builder

**Cause:** The toggle is off, or the editor is showing a cached view.
**Fix:** Confirm **Disable Preloader inside Bricks Builder** is on, save, and reload the Bricks Builder.

### The preloader is gone for visitors too

**Cause:** The **Enable Preloader** toggle may be off, which disables the preloader everywhere.
**Fix:** Confirm **Enable Preloader** is on. This option only affects the Bricks Builder, not the frontend.

## Related Articles

- [How to Use Laser Loader in WordPress](interface-laser-loader.md)
- [How to Use the Preloader in WordPress](interface-preloader.md)
- [How to Use the Interface Tab in Classic Monks: Feature Index](../interface.md)

---

*Written by Joy. Last updated August 4, 2026. Tested with WordPress 6.x and Classic Monks 2.1.0.*

<!-- schema: Article, TechArticle -->
<!-- schema: BreadcrumbList -->