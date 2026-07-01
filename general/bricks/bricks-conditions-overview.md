---
title: "How to Use Bricks Conditions in WordPress | CM"
slug: bricks-conditions
description: "Overview of all conditional display rules in Classic Monks. 80 conditions for showing/hiding elements based on post, user, content, and WooCommerce data."
last_updated: 2026-06-24
author: Joy
reading_time: 5 min
canonical: https://classicmonks.com/docs/bricks-conditions/
---

# How to Use Bricks Conditions in WordPress

> Classic Monks adds 80 conditional display rules to Bricks Builder. Show or hide elements based on post data, user data, content analysis, and WooCommerce conditions.

## Key Takeaways

- Category overview of Bricks Builder features
- Multiple features can be enabled independently
- Each feature is a standalone toggle
- Features appear in the Bricks editor after enabling

## What Is This Category?

Classic Monks adds 80 conditional display rules to Bricks Builder. Show or hide elements based on post data, user data, content analysis, and WooCommerce conditions. This is a category overview of all features in this group.

---

## Post Conditions

- **Post Views Count**: Show element based on view count
- **Post Word Count**: Show/hide based on word count
- **Reading Time**: Show/hide based on estimated reading time
- **Images Count**: Show/hide based on number of images
- **Links Count**: Show/hide based on number of links
- **Current Year**: Show/hide based on current year
- **Parent Title**: Show/hide based on parent page title
- **Post Class**: Show/hide based on CSS classes
- **Post Year**: Show/hide based on post publication year
- **Loop Counter**: Show/hide based on loop iteration
- **Author Posts Count**: Show/hide based on author's post count
- **Author Comments Count**: Show/hide based on author's comment count
- **Comment Status**: Show/hide based on comment status
- **Ping Status**: Show/hide based on ping status
- **Is Password Protected**: Show/hide password-protected content

## User and Visitor Conditions

- **Visitor Type**: Show/hide for guests vs. logged-in users
- **Days Since Registration**: Show/hide based on user registration date
- **User Role Level**: Show/hide based on user role

## Content Analysis Conditions

- **Headings Count**: Show/hide based on heading count
- **Paragraphs Count**: Show/hide based on paragraph count
- **Lists Count**: Show/hide based on list count
- **Tables Count**: Show/hide based on table count
- **External Links**: Show/hide based on external link count
- **Shortcodes Count**: Show/hide based on shortcode count
- **Blocks Count**: Show/hide based on block count
- **Media Count**: Show/hide based on media count

## Taxonomy Conditions

- **Taxonomy Depth**: Show/hide based on taxonomy nesting depth
- **Posts in Taxonomy Count**: Show/hide based on posts in taxonomy
- **Child Terms Count**: Show/hide based on child term count
- **Has Parent Term**: Show/hide based on parent term existence
- **Is Hierarchical**: Show/hide based on taxonomy hierarchy
- **Is Public**: Show/hide based on taxonomy visibility

## Image Conditions

- **Image HTML/ID/URL/Title/Alt/Caption/Description**: Show/hide based on image attributes

## WooCommerce Conditions

- **Cart Weight/Items Count/Categories Count/Subtotal/Total**: Cart-based conditions
- **Product Sales/Reviews/Gallery Count**: Product-based conditions
- **Customer Orders Count/Reviews Count/Last Order Days/Average Order Value**: Customer-based conditions
- **Order Tax Total/Status Count**: Order-based conditions
- **Cross Sells/Upsells Count**: Cross-sell/upsell conditions
- **Product Type/Stock Quantity/Shipping Class**: Product attribute conditions
- **Sale Start/End Date**: Sale period conditions
- **Product Total Sales/Total Reviews/Average Rating**: Product statistics
- **Customer Total Orders/Total Spent**: Customer statistics
- **Product Dimensions/Weight/Purchase Note**: Product details
- **Tax Status/Class/Download Limit/Expiry**: Tax and download conditions
- **Average Order Interval/Last Purchased Date**: Customer timing conditions
- **Is Checkout Page/Thank You Page**: Page type conditions
- **Payment Gateway/Order Status**: Checkout conditions

## How to use conditions

All conditions can be enabled in the Bricks > Conditions subtab. Once enabled, they appear as condition types in the Bricks editor's conditional logic panel. Use them to show or hide elements based on any of the available data sources.

## Related Articles

- [How to Set Up the Bricks Integration in WordPress](bricks-setup.md)
- [How to Use Bricks Builder UI Improvements in WordPress](bricks-ui-improvements.md)
- [How to Check Bricks Builder Status in WordPress](bricks-status.md)


### Developer integration

The Bricks conditions system extends Bricks' native condition API.

**Bricks filters used:**

- `bricks/conditions/groups` adds custom condition groups
- `bricks/conditions/options` adds custom condition options
- `bricks/conditions/result` modifies condition evaluation

Custom conditions are registered by extending the conditions manager class in `conditions-manager.php`.
