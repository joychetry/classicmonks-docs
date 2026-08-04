---
title: "How to Display Dynamic Data in Bricks in WordPress"
slug: "bricks-dynamic-data"
description: "Enable Bricks dynamic data sources in Classic Monks. Display post, user, content, taxonomy, and WooCommerce data with dynamic data tags in the Bricks editor."
last_updated: 2026-08-04
author: Joy
reading_time: 6 min
canonical: "https://classicmonks.com/docs/bricks-dynamic-data/"
---

# How to Use Bricks Dynamic Data in WordPress: Display Content

> Dynamic data lets you pull live values into your Bricks layouts, such as the current year, a post's reading time, or a product's price. Classic Monks adds more dynamic data sources to Bricks, so you can display post, user, content, taxonomy, and WooCommerce data.

## Key Takeaways

- Enable dynamic data sources in the **Bricks** tab, **Dynamic Data** subtab.
- Each data source is an independent toggle.
- Use the data tags in text fields, attributes, and conditional logic.
- Sources cover post, user, content, taxonomy, and WooCommerce data.

## What Are Bricks Dynamic Data Sources

Bricks Dynamic Data sources in Classic Monks are the data tags that the Bricks Builder uses to display live values. They are organized in the **Dynamic Data** subtab as independent toggles. Once you enable a source, it appears as a data tag in the Bricks editor's dynamic data panel, and you can insert it into any text field, attribute, or conditional logic.

## Recommendations Before Enabling

- **Enable the data sources you use.** Each source is independent, so enable the ones your layouts need.
- **Test on a live page.** After adding a data tag, check the frontend to confirm it shows the expected value.
- **Confirm the data is available.** Some sources need supporting data, such as WooCommerce or user data, so confirm it exists on the page.

## Enable Bricks Dynamic Data

### Step 1: Open the Bricks Tab

In your WordPress dashboard, go to **Classic Monks**, then open the **Bricks** tab.

### Step 2: Open the Dynamic Data Subtab

Click the **Dynamic Data** subtab.

### Step 3: Enable the Data Sources You Need

Toggle on the data sources you want. The sources are grouped by type:

- **Post and author**: current year, parent title, post class, post year, loop counter, author stats, comment and ping status, password protection, published and updated time, post views, word count, reading time, and more.
- **Image and media**: image HTML, ID, URL, title, alt, caption, and description.
- **Content analysis**: headings, paragraphs, lists, tables, external links, shortcodes, blocks, and media counts.
- **Taxonomy**: taxonomy depth, children count, parent, hierarchy, and visibility.
- **WooCommerce**: product type, stock, cart data, shipping class, sale dates, total sales, reviews, ratings, customer stats, product details, tax and download, and order data.

### Step 4: Save

Click **Save (⌘+S)**.

### Step 5: Use a Data Source in the Editor

Open a page in the Bricks editor, select a text field or attribute, and insert a data tag from the dynamic data panel.

## Verify It Works

After enabling a data source, verify it:

- Open the Bricks editor and insert the data tag into a field.
- View the page on the frontend and confirm it shows the expected value.
- Confirm the data tag appears in the dynamic data panel.

If a data source does not appear, confirm its toggle is on and the editor was refreshed.

## Common Use Cases

### Show the current year in a footer

Enable the **Current Year** data source and insert it into a footer text field. The footer always shows the current year without updating it manually.

### Show a reading time badge

Enable the **Reading Time** data source and add it to a post template. Each post shows its estimated reading time.

### Show a product's average rating

Enable the **Average Rating** data source and add it to a product template. The template shows the product's average star rating.

### Show a sale start date

Enable the **Sale Start Date** data source and add it to a product template. The template shows when the product's sale begins.

## Troubleshooting

### A data source does not appear in the editor

**Cause:** The source toggle is off, or the Bricks editor is showing a cached view.
**Fix:** Confirm the source is enabled in the **Dynamic Data** subtab and refresh the Bricks editor.

### A data tag shows empty on the frontend

**Cause:** The supporting data is not available on the page.
**Fix:** Confirm the data exists, such as WooCommerce or user data, and that the tag is used in the right context.

### A WooCommerce data source does not work

**Cause:** WooCommerce is not active, or the source needs a product context.
**Fix:** Confirm WooCommerce is active and the tag is used on a relevant page or loop.

## Related Articles

- [How to Use Bricks Elements in WordPress](bricks-elements-overview.md)
- [How to Use Bricks Conditions in WordPress](bricks-conditions-overview.md)
- [How to Complete the Bricks Initial Setup in WordPress](bricks-setup.md)

---

*Written by Joy. Last updated August 4, 2026. Tested with WordPress 6.x and Classic Monks 2.1.0.*

<!-- schema: Article, TechArticle -->
<!-- schema: BreadcrumbList -->