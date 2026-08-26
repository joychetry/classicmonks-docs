---
title: "How to Use Auto Featured Image in Classic Monks"
slug: auto-featured-image
description: "Auto Featured Image in Classic Monks automatically sets the first image in post content as the featured image when saving. Ensures every post has a featured image."
last_updated: 2026-06-24
author: Joy
reading_time: 5 min
canonical: https://classicmonks.com/docs/auto-featured-image/
---

# How to Use Auto Featured Image in WordPress

> Auto Featured Image automatically sets the first image in a post's content as the featured image when the post is saved, if no featured image is already set.

## Key Takeaways

- Sets the first image as featured on save when no featured image exists
- Works with the classic editor, Gutenberg image blocks, and galleries
- Does not overwrite an existing featured image
- Does not pick up background images, embeds, or JavaScript-rendered images
- Saves the original as a media library attachment if it isn't already

## What Is Auto Featured Image?

Auto Featured Image is a Classic Monks feature that runs on every post save. If the post has no featured image set, the feature scans the post content for the first `<img>` tag, downloads it (if external) or uses the media library version, and sets it as the featured image. If the post already has a featured image, the feature does nothing.

## Why You Need It

Featured images are essential for WordPress sites:

- Social sharing (Open Graph and Twitter Cards use the featured image)
- Archive pages (most themes show featured images in post lists)
- SEO (Google Images search can surface featured images)
- Reader experience (posts with images get more engagement)

But authors forget to set them. Auto Featured Image is the safety net: every post that has an image in its content automatically gets a featured image, even if the author skipped the manual step.

---

## How to Use Auto Featured Image in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Content Subtab

Click on the **Core** menu, then click the **Content** subtab.

### Step 3: Enable Auto Featured Image

Scroll to the **Editorial Workflow** section and toggle on **Auto Featured Image**. No nested options are needed.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test on a New Post

Create a new post (or edit an existing one) and add an image to the content. Save the post. The Featured Image meta box in the right sidebar should now show the first image from your content.

### Step 6: Verify on an Existing Post

Open an existing post that has an image in the content but no featured image. Save it. The featured image should now be set.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Auto Featured Image** | Master toggle. Enables the auto-set behavior. | Off |

No nested options. The feature runs silently on every post save.

---

## What Image Sources Are Supported

| Image Source | Supported? | Notes |
|--------------|-----------|-------|
| Image uploaded to Media Library, embedded in content | Yes | Uses the existing media library attachment |
| Image embedded in content via Gutenberg Image block | Yes | The block's `<img>` is captured |
| Image embedded in content via classic editor | Yes | Standard `<img>` tags are captured |
| Image in a Gallery block | Yes | The first gallery image is used |
| Image from an external URL (not in Media Library) | Yes | The image is downloaded and added to the Media Library |
| Featured image set manually | N/A | The existing featured image is preserved (not overwritten) |
| Image in a Cover block (Gutenberg) | Yes | The cover image is used |
| Image as a CSS background | No | Auto Featured Image only reads `<img>` tags |
| Image rendered by JavaScript (e.g., lazy-load placeholder) | Partial | The initial `<img>` is captured; JS-replaced images are not |
| Image inside a third-party embed (YouTube, etc.) | No | Embeds don't have a usable featured image |

---

## Developer Notes

Auto Featured Image sets the first image in post content as the featured image. No developer hooks are currently exposed.

**Options used:**
| Option | Type | Default |
|--------|------|---------|
| `enable_auto_featured_image` | Boolean | `false` |
---

## Troubleshooting

### The featured image is not being set automatically

**Cause:** The post has no `<img>` tag in its content, the first image is a background image (not supported), or the post already has a featured image set.
**Fix:** Verify the post has a real `<img>` tag by editing in the Text/Code view. Manually delete the existing featured image (if any) and save again to trigger the auto-set.

### The auto-set image is the wrong one

**Cause:** The "first" image is interpreted as the first `<img>` in the rendered content. This may be a small icon, a logo, or a decorative image that appears before the main content image.
**Fix:** Use the `cm_auto_featured_image_selector` filter to apply custom selection logic (e.g., skip images smaller than 200x200, prefer images in the post body over images in sidebars). Or manually set the featured image for posts where the auto-set picks the wrong one.

### The auto-set image has no alt text

**Cause:** The original image had no alt text, and the feature doesn't auto-generate one.
**Fix:** Use the `cm_auto_featured_image_alt` filter to set alt text from the post title or a default. Or manually add alt text to the media library image (which the feature will pick up).

### The image is being added to Media Library every save

**Cause:** If the post content has an external image URL, the feature downloads it and adds it to the Media Library on every save. This creates duplicate media library entries.
**Fix:** Move external images to the Media Library manually before publishing. The feature will then use the existing media attachment, not create a new one.

---

## Related Articles

- [How to Use Content Management in Classic Monks](core-content-management.md)
- [How to Use Content Duplication in Classic Monks](core-content-duplication.md)
- [How to Use Custom Columns in Classic Monks](core-custom-columns.md)
