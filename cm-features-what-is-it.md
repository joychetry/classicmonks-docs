# Classic Monks Features - What It Is, How It Works, and Benefits

*A plain-language guide to every Classic Monks feature. For each feature you'll find a simple "What is it" explanation, a short "How it works" description, and the "Benefits" it delivers. This is the version intended for the public website, written so any WordPress site owner can understand what each feature actually does.*

> **Structure:** Features are grouped under tab headings (`##`) and subtab headings (`###`). Each entry has a bold feature name, a **What is it** definition in plain language, a **How it works** explanation, and a **Benefits** summary.

## Table of Contents
- [AI Tab](#ai-tab)
- [Core Tab](#core-tab)
- [Email Tab](#email-tab)
- [WooCommerce Tab](#woocommerce-tab)
- [Bricks Builder Tab](#bricks-builder-tab)
- [Security Tab](#security-tab)
- [Interface Tab](#interface-tab)
- [Performance Tab](#performance-tab)
- [White Label Tab](#white-label-tab)
- [Options Tab](#options-tab)

---

## Feature Summary

| Tab                | Main Features |
|--------------------|--------------|
| AI                 | 16 |
| Core               | 67 |
| Email              | 12 |
| WooCommerce        | 59 |
| Bricks Builder     | 96 |
| Security           | 57 |
| Interface          | 29 |
| Performance        | 74 |
| White Label        | 16 |
| Options            | 22 |
| **Total**          | **448** |

---

## AI Tab

### AI Integration

**Enable AI Features:**
What is it: AI Features is the master switch that turns on all the AI-powered tools inside Classic Monks, from content generation and image editing to SEO help and site management tasks.
How it works: Activates AI-powered content generation, SEO optimization, and WordPress management features throughout the plugin by connecting to external AI providers via API.
Benefits: Unlocks intelligent automation for content creation, SEO optimization, and site management, reducing manual work and improving content quality.

**Enable AI Agent:**
What is it: The AI Agent is a chatbot that lives in your WordPress admin bar, ready to answer questions and help you work right inside the dashboard.
How it works: Enables an AI chat overlay in the WordPress admin bar that provides interactive assistance, answering questions and performing tasks through natural language conversation.
Benefits: Provides instant WordPress expertise within the admin interface, speeds up workflow with AI-powered assistance, and reduces time spent searching for solutions.

**Enable Bricks AI Builder:**
What is it: Bricks AI Builder is an AI assistant that converts raw HTML designs into ready-to-use Bricks Builder elements, so you spend less time building from scratch.
How it works: Activates AI generation inside the Live HTML to Bricks panel for Bricks Builder, allowing AI to convert HTML designs into Bricks Builder elements with structured data support.
Benefits: Accelerates Bricks Builder development, enables rapid prototyping from HTML mockups, and provides AI-assisted design-to-code conversion.

### AI Agent

**AI Agent System Prompt:**
What is it: The AI Agent System Prompt is a set of custom instructions that tells your AI assistant how to behave, what it knows, and how to respond.
How it works: Custom instructions that guide the AI agent's behavior and responses. Leave empty for default WordPress assistant behavior, or specify custom personality, expertise, and response patterns.
Benefits: Customizes AI responses to match your workflow, provides domain-specific expertise, and ensures consistent AI behavior aligned with your needs.

**Bricks AI Builder System Prompt:**
What is it: The Bricks AI Builder System Prompt is a set of custom instructions that shapes how the AI converts HTML into Bricks elements and what code style it follows.
How it works: Custom instructions for the Bricks AI Builder that guide HTML-to-Bricks conversion behavior, coding standards, and design preferences. Leave empty for default behavior.
Benefits: Ensures AI-generated Bricks elements follow your design system, produces consistent code quality, and tailors output to your development standards.

**Max Tokens:**
What is it: Max Tokens sets an upper limit on how long each AI response can be, controlling detail level and cost.
How it works: Sets the maximum number of tokens (100-8000) per AI response, controlling response length and cost. Higher values allow more detailed responses but increase API costs.
Benefits: Balances response detail with cost efficiency, prevents unexpectedly long responses, and provides control over API usage and spending.

**Chat Panel Width:**
What is it: Chat Panel Width controls the size of the AI chat window that slides over your admin screen.
How it works: Configures the width of the AI chat overlay panel in pixels (300-600px), adjusting how much screen space the agent interface occupies.
Benefits: Provides comfortable reading experience, adapts to different screen sizes and preferences, and optimizes workspace between the chat panel and admin interface.

### AI Provider

**AI Provider Selection:**
What is it: AI Provider Selection lets you choose which AI service powers the plugin, with options like OpenRouter, OpenAI, Anthropic, and Google Gemini.
How it works: Choose from 8 AI providers, OpenRouter (recommended), OpenAI, Anthropic, Google Gemini, NVIDIA Build/Integrate, Zhipu AI (GLM), OpenAI Compatible, or Custom Endpoint, each requiring an API key and optional model configuration.
Benefits: Provides flexibility to use preferred AI providers, enables cost optimization through provider comparison, and supports both mainstream and specialized AI models.

**Vision / Image Provider:**
What is it: Vision / Image Provider is a separate AI service you can set just for image tasks like alt text and image generation, so the right model handles visual work.
How it works: Configure a separate AI provider specifically for image-aware workflows (alt text generation, image generation, Bricks AI image attachments) that takes priority over the main text provider for image tasks, falling back to the main provider when the selected vision model supports it.
Benefits: Optimizes image processing with specialized models, reduces costs by using targeted models only for image tasks, and enables multimodal features even when the main provider doesn't support images.

### AI Tools

**Alt Text Generation:**
What is it: Alt Text Generation automatically writes descriptive alternative text for your images, which improves SEO and accessibility without you typing it by hand.
How it works: Automatically generates descriptive alt text for images in the Media Library using AI vision models, analyzing image content to create SEO-friendly and accessibility-compliant descriptions.
Benefits: Improves SEO with descriptive image alt text, ensures accessibility compliance, saves hours of manual alt text writing, and maintains consistent image descriptions across the site.

**Image Generation:**
What is it: Image Generation creates brand-new images from a text description right inside WordPress, so you don't need an external tool or stock photo service.
How it works: Creates images from text prompts using AI image generation models (FLUX, GPT-Image) directly within WordPress, enabling visual content creation without external tools.
Benefits: Enables rapid content creation, produces custom images for posts and pages, eliminates dependency on stock photo services, and supports creative workflows within WordPress.

**Image Editing:**
What is it: Image Editing brings AI-powered photo tools into your Media Library, letting you remove backgrounds and adjust images without other software.
How it works: Provides AI-powered image editing capabilities directly within the WordPress Media Library, including background removal, object inpainting/outpainting, and style transfers using configured vision/image provider models.
Benefits: Eliminates the need for external image editing software, enables rapid image adjustments without leaving WordPress, and supports creative workflows with AI-assisted editing tools.

**AI Tools System Prompt:**
What is it: The AI Tools System Prompt is a shared set of instructions applied to all AI text tools, keeping their output style consistent.
How it works: Custom instructions applied to all AI text-generation tools (Alt Text Generation, Image Generation, Image Editing) that define output style, format preferences, and quality standards. Leave empty for provider-default behavior.
Benefits: Ensures consistent AI output quality across all tools, enforces brand guidelines and tone, and provides centralized control over AI text generation behavior without configuring each tool individually.

### Advanced

**Debug Mode:**
What is it: Debug Mode records detailed logs of every AI request and response so you can find and fix problems when something goes wrong.
How it works: Enables detailed logging of AI API requests and responses for troubleshooting, capturing full request/response data including headers, payloads, and error details.
Benefits: Simplifies API integration troubleshooting, provides visibility into AI request/response cycles, and helps identify configuration issues quickly.

**Max Retries:**
What is it: Max Retries sets how many times Classic Monks retries an AI request that fails, helping it recover from temporary errors automatically.
How it works: Configures the number of retry attempts (0-5) for failed AI API requests, automatically reattempting calls that fail due to rate limits, network issues, or temporary errors.
Benefits: Improves reliability of AI operations, handles transient API errors gracefully, and ensures successful completion of AI-assisted tasks.

**Chat History Limit:**
What is it: Chat History Limit controls how many past messages the AI assistant remembers, which affects both context and cost.
How it works: Sets the maximum number of messages (5-50) retained in conversation history for the AI agent, controlling context window size and memory usage.
Benefits: Manages API token usage and costs, provides relevant conversational context without exceeding limits, and balances response quality with resource efficiency.

---

## Email Tab

### Email Settings

**Enable Email Logging:**
What is it: Email Logging records every email your WordPress site sends, so you can review history and resend any that failed.
How it works: Intercepts all emails sent through WordPress and stores detailed records including sender, recipient, subject, content, and delivery status with the ability to resend failed emails.
Benefits: Provides audit trail for all email communications, enables troubleshooting of email delivery issues, and ensures important emails are never lost.

**Enable SMTP Settings:**
What is it: SMTP Settings lets you send WordPress emails through a proper mail server instead of the default method, which makes delivery far more reliable.
How it works: Replaces WordPress default mail() function with SMTP authentication, supporting popular email services like Gmail, Outlook, and custom SMTP servers with backup server options.
Benefits: Dramatically improves email deliverability, reduces spam folder placement, and provides reliable email sending with authentication and encryption.

**Customize WP Emails:**
What is it: Customize WP Emails gives you one place to redesign and rebrand every notification email WordPress sends, from password resets to new user alerts.
How it works: Provides a centralized interface to customize all WordPress system notification emails, including password resets, new user registrations, comment notifications, and admin alerts, with dynamic merge tags for personalized content.
Benefits: Creates consistent, branded email communications across all WordPress notifications, improves user trust with professional email formatting, and eliminates the need for separate email customization plugins.

### Notifications

**Enable Comment Reply Email:**
What is it: Comment Reply Email notifies users when someone replies to their comment, keeping conversations going and bringing visitors back.
How it works: Automatically sends email notifications to comment authors when someone replies to their comments, with configurable trigger conditions and opt-in/opt-out functionality.
Benefits: Increases user engagement by notifying users of responses, builds community interaction, and encourages return visits to continue conversations.

**Disable Password Change Email:**
What is it: Disable Password Change Email stops WordPress from sending a notice every time a password is changed, cutting down on trivial email.
How it works: Prevents WordPress from sending email notifications to users when their passwords are changed, either by themselves or administrators.
Benefits: Reduces email clutter for users, prevents notification fatigue, and eliminates unnecessary emails for routine password management.

**Disable New User Email:**
What is it: Disable New User Email stops the notification WordPress sends to admins each time a new user registers.
How it works: Stops automatic email notifications sent to administrators when new users register on the website.
Benefits: Reduces admin email volume, prevents notification overload on high-traffic membership sites, and allows selective user management.

**Disable Admin Email Change:**
What is it: Disable Admin Email Change removes the confirmation step when you update the site admin email address, applying the change immediately.
How it works: Removes the email confirmation process when administrators change the site admin email address, allowing immediate changes.
Benefits: Speeds up site administration, eliminates unnecessary verification steps, and provides immediate admin email updates.

**Disable Auto Update Notification Emails for Core:**
What is it: This setting stops the email WordPress sends after it automatically updates the core software.
How it works: Prevents WordPress from sending email notifications when WordPress core automatically updates to newer versions.
Benefits: Reduces administrative email noise, prevents update notification fatigue, and focuses attention on important notifications only.

**Disable Auto Update Notification Emails for Plugins:**
What is it: This setting stops the notification emails WordPress sends after plugins are automatically updated.
How it works: Stops email notifications when plugins are automatically updated by WordPress background update system.
Benefits: Eliminates routine update notifications, reduces email volume, and prevents notification overload from frequent plugin updates.

**Disable Auto Update Notification Emails for Themes:**
What is it: This setting stops the email notices WordPress sends when themes are automatically updated.
How it works: Prevents email notifications when themes are automatically updated through WordPress auto-update functionality.
Benefits: Reduces unnecessary email communications, focuses on critical notifications, and prevents inbox clutter from routine theme updates.

### WooCommerce

**Disable WooCommerce Emails:**
What is it: Disable WooCommerce Emails turns off every automated WooCommerce email, from order confirmations to shipping notices.
How it works: Completely disables all WooCommerce email notifications including order confirmations, shipping notices, and admin notifications.
Benefits: Prevents email overload, allows custom email solutions, and provides complete control over customer communication timing and content.

**Allow Reset Password Email:**
What is it: Allow Reset Password Email is a fine-tuned version of disabling WooCommerce email, keeping only password reset messages enabled.
How it works: Disables all WooCommerce transactional emails except password reset emails, which remain active so users can still recover their accounts.
Benefits: Silences routine order notifications while keeping essential account recovery emails working.

---

## Core Tab

### Setup

**Quick WordPress Setup:**
What is it: Quick WordPress Setup is a guided wizard that walks you through the essential first steps of a new site, like site identity, plugins, themes, homepage, and cleanup. It can only be run once.
How it works: Runs a set of initial WordPress setup tasks (site identity, plugins, themes, homepage, cleanup) in a guided flow, then disables itself so it cannot be run again.
Benefits: Gets a new site configured correctly from the start, saves setup time, and prevents missed essential configuration.

**Self-Host Google Analytics v4:**
What is it: Self-Host Google Analytics v4 lets you track site traffic with your own copy of the analytics script, instead of loading it from Google's servers.
How it works: Provides self-hosted Google Analytics v4 integration with two performance-optimized tracking options: Minimal Analytics (1.4KB) for ultra-fast basic tracking and Gtag.js (90KB) for full GA4 features. Includes tracking ID validation, admin exclusion options, and performance optimizations.
Benefits: Eliminates dependency on external Google Analytics servers, improves page load performance through optimized tracking scripts, provides choice between speed and functionality, and ensures analytics data privacy by self-hosting tracking code.

**Code Manager:**
What is it: Code Manager is a built-in code editor that lets you add PHP, CSS, and JavaScript snippets to your site without editing your theme files.
How it works: Adds a dedicated Code Manager submenu under Classic Monks for managing PHP, CSS, and JavaScript code snippets. Add custom functionality without editing theme files, with support for conditional loading and syntax highlighting.
Benefits: Enables safe code customization without theme modifications, provides organized code snippet management, and allows adding custom functionality through a user-friendly interface. Page reload required after enabling.

### File Downloader

**Plugin Zip Downloads:**
What is it: Plugin Zip Downloads adds a download button next to each installed plugin so you can grab its ZIP file straight from the WordPress admin.
How it works: Adds download links to the WordPress plugins page that allow you to download any installed plugin as a ZIP file directly from the admin interface without accessing the server files.
Benefits: Enables easy plugin backup and transfer between sites, useful for development workflows, and provides a quick way to create plugin archives for distribution or storage.

**Theme Zip Downloads:**
What is it: Theme Zip Downloads adds a download option for your installed themes so you can save their ZIP files without needing FTP access.
How it works: Adds download links to the WordPress themes page that allow you to download any installed theme as a ZIP file directly from the admin interface without FTP access.
Benefits: Simplifies theme backup and migration processes, enables easy theme sharing between development and production environments, and provides a convenient way to archive custom themes.

**Download File to WordPress:**
What is it: Download File to WordPress lets you pull any file from an external URL straight onto your server, with progress tracking, right from the admin.
How it works: Provides a modal interface where you can enter any URL to download files directly to your WordPress server, with real-time progress tracking and error handling.
Benefits: Eliminates the need for FTP clients or server access to upload large files, speeds up the process of importing external assets, and provides a secure way to download files with progress monitoring.

### Content Management

**Post Type Switcher:**
What is it: Post Type Switcher lets you change a piece of content from one post type to another, either on the edit screen or in bulk, without recreating it.
How it works: Adds dropdown menus to edit screens and bulk actions that allow changing content from one post type to another while preserving all metadata, custom fields, and compatible taxonomies.
Benefits: Fixes content organization mistakes without recreating content, enables flexible content strategy changes, and saves time when restructuring site content architecture.

**Taxonomy Switcher:**
What is it: Taxonomy Switcher lets you move taxonomy terms from one taxonomy to another, keeping all your content associations intact.
How it works: Provides interface to migrate taxonomy terms between different taxonomies, updating all associated posts and maintaining hierarchical relationships where possible.
Benefits: Enables taxonomy restructuring without losing content associations, simplifies site reorganization, and provides flexibility in content categorization strategies.

**Order Post Types:**
What is it: Order Post Types adds drag-and-drop reordering to your post type lists so you can set the display order visually instead of with code.
How it works: Adds drag-and-drop reordering functionality to post type list tables, saving the custom order in the database and optionally reflecting it on the frontend through menu_order queries.
Benefits: Allows intuitive content organization without manual menu_order editing, improves content management workflow, and provides visual control over content hierarchy and display order.

**Order Taxonomy Terms:**
What is it: Order Taxonomy Terms lets you arrange categories and other taxonomy terms in any order using drag-and-drop.
How it works: Provides a dedicated interface for reordering hierarchical taxonomy terms (categories, custom taxonomies) via simple drag-and-drop within the admin panel, updating the term display order throughout the site.
Benefits: Enables intuitive taxonomy organization without custom code, improves content categorization workflow, and ensures terms appear in the desired sequence on frontend displays.

**Admin Columns Manager:**
What is it: Admin Columns Manager lets you control which columns appear in your admin list tables, reorder them, hide the ones you do not need, and customize how they behave for any post type.
How it works: Provides a drag-and-drop interface to manage, reorder, hide, and customize the columns shown in admin list tables for all registered post types, applying your layout to the relevant admin screens.
Benefits: Declutters the admin interface to show only the data you use, improves content management efficiency, and tailors admin screens to your workflow.

**Custom Taxonomy Filters:**
What is it: Custom Taxonomy Filters adds dropdown menus to your admin list pages so you can filter content by category, tag, or any custom taxonomy.
How it works: Automatically adds taxonomy dropdown filter menus to admin list table pages for all registered taxonomies, enabling quick filtering of content by category, tag, or custom taxonomy without additional configuration.
Benefits: Speeds up content management in sites with many categories or custom taxonomies, provides instant filtering capabilities for all taxonomy types, and improves admin workflow efficiency without manual setup.

**Global 404 Redirect:**
What is it: Global 404 Redirect sends every "page not found" visitor to a custom destination, like your homepage or shop, instead of showing a dead-end error page.
How it works: Redirect all 404 errors site-wide to a custom destination, home page, shop page, a specific page, or a custom URL, instead of showing the default error page.
Benefits: Improves user experience by guiding visitors to relevant content, reduces bounce rates from broken links, and maintains engagement even when pages are not found.

**Short Links & Tracking:**
What is it: Short Links & Tracking lets you create branded, short links for your site with built-in click tracking, expiration dates, and password protection.
How it works: Creates a custom post type for managing branded short URLs with built-in analytics, expiration dates, password protection, and detailed click tracking with geographic and device data.
Benefits: Improves social media sharing with branded links, provides detailed analytics on link performance, and offers professional URL management for marketing campaigns.

**Conditional Menu Items:**
What is it: Conditional Menu Items lets you show or hide navigation menu items based on user roles, device type, page context, and other conditions.
How it works: Control visibility of menu items based on user roles, device type, page context, and more with advanced AND/OR logic conditions.
Benefits: Provides granular control over navigation display, personalizes menu content for different user segments, and creates dynamic navigation experiences.

**Public Post Preview:**
What is it: Public Post Preview lets you share unpublished posts with outside collaborators using a secure, temporary link, so they do not need a login.
How it works: Generates secure, temporary URLs that allow external users to view unpublished content without WordPress login credentials, with optional password protection and configurable expiration times.
Benefits: Streamlines client review processes, enables collaboration with external stakeholders, and maintains security while allowing content preview access.

**Enable Global Password Protection:**
What is it: Global Password Protection adds a single site-wide password that guards every Public Post Preview link, so only people with the password can see unpublished content.
How it works: Adds a single, site-wide password that protects all Public Post Preview links, requiring visitors to enter the global password before viewing any unpublished content shared via preview URLs.
Benefits: Provides an additional security layer for all preview content, prevents unauthorized access to unpublished materials, and simplifies access control by using a single password for all preview links.

**Enable Content Duplication:**
What is it: Content Duplication adds a one-click "Duplicate" button to your posts, pages, and custom post types so you can clone content quickly.
How it works: Adds "Duplicate" action links to posts, pages, and custom post types in the admin interface that create exact copies of content including all metadata, custom fields, and taxonomies.
Benefits: Speeds up content creation when you need similar posts or pages, saves time when creating template-based content, and ensures consistency across related content pieces.

**Classic Feedback:**
What is it: Classic Feedback adds a simple "Was this article helpful to you?" prompt to your content so visitors can rate your pages.
How it works: Inserts a lightweight feedback widget into your content that lets visitors mark an article as helpful or not, with results viewable in the admin.
Benefits: Gives you direct insight into how useful your content is, helps identify weak pages to improve, and collects feedback without a third-party survey service.

**Auto Featured Image:**
What is it: Auto Featured Image automatically sets the first image in a post as its featured image when none is assigned.
How it works: Automatically scans post content for the first image when a post is saved and sets it as the featured image if no featured image is already assigned.
Benefits: Ensures all posts have featured images for consistent theme display, saves time in content creation workflow, and improves social media sharing appearance.

**Disable Author Edit:**
What is it: Disable Author Edit prevents non-admin users from changing who authored a post, keeping attribution accurate.
How it works: Prevents non-admin users from changing the post author field on edit screens, restricting author reassignment to administrators only while leaving all other editing capabilities intact.
Benefits: Maintains content attribution integrity, prevents unauthorized author changes by editors and authors, and ensures proper credit and accountability for content creators.

**Disable Scheduled Deletion:**
What is it: Disable Scheduled Deletion stops WordPress from automatically deleting trashed posts after the default waiting period.
How it works: Prevents WordPress from automatically deleting trashed posts after the default 30-day period, giving you more time to recover content.
Benefits: Provides longer recovery window for accidentally deleted content and prevents unexpected content loss.

**Disable Comments:**
What is it: Disable Comments turns off comments across all post types, removing forms and blocking new submissions site-wide.
How it works: Globally disables comments on all post types by removing comment forms, hiding comment-related admin sections, and preventing new comment submissions.
Benefits: Reduces spam and moderation workload, improves page loading speeds by removing comment-related queries, and eliminates security risks associated with comment forms.

**Allow Duplicate Comments:**
What is it: Allow Duplicate Comments lets the same person post more than once on the same article without being blocked as a duplicate.
How it works: Allows users with the same name and email to submit multiple comments on the same post without being treated as duplicates.
Benefits: Enables returning commenters to participate in ongoing discussions and supports community conversations where users may want to comment multiple times.

**Disable Link in Comment and Disable Auto-linking:**
What is it: This feature strips links out of comment text and stops WordPress from auto-converting URLs into clickable links, removing a common spam vector.
How it works: Strips all hyperlinks from comment text and disables WordPress's automatic URL-to-link conversion, preventing commenters from posting clickable links in any form.
Benefits: Eliminates spam links in comments completely, prevents SEO manipulation through comment link injection, and maintains cleaner, safer comment sections without manual moderation of links.

**Remove Comment URLs:**
What is it: Remove Comment URLs deletes the website field from the comment form and strips URLs from comment author names.
How it works: Removes the website URL field from the comment form, simplifying the commenting experience and reducing spam signals.
Benefits: Streamlines the comment submission process, removes a common spam entry point, and creates a cleaner commenting interface.

**HTML5 Comment Support:**
What is it: HTML5 Comment Support upgrades your comment forms to use modern HTML5 input types and attributes for better validation.
How it works: Enables HTML5 input types and attributes in WordPress comment forms for better validation and modern browser support.
Benefits: Improves form validation with native browser support, enhances mobile commenting experience, and uses modern HTML5 form features.

**Tags Without Comma Shortcode:**
What is it: Tags Without Comma Shortcode provides a `[tags_no_comma]` shortcode that displays your post tags without comma separators.
How it works: Provides the `[tags_no_comma]` shortcode that displays post tags without comma separators, allowing use in loops, pages, posts, or anywhere shortcodes are supported.
Benefits: Enables flexible tag presentation without separators, provides design freedom for tag displays, and works in any shortcode-supported context for maximum placement flexibility.

**RankMath Meta Excerpt Shortcode:**
What is it: RankMath Meta Excerpt Shortcode lets you display your RankMath SEO meta description as visible content on the page using a shortcode.
How it works: Provides a shortcode to display the RankMath SEO meta description as visible content on the page.
Benefits: Shows SEO-optimized descriptions as page content and ensures consistency between displayed content and search results.

**Enable Time Format Conversion:**
What is it: Time Format Conversion lets you display times in different formats and timezones using shortcodes.
How it works: Adds shortcode support for converting and displaying time values in different formats and timezones.
Benefits: Provides flexible time display options and enables timezone-aware content presentation.

**Enable Currency Converter:**
What is it: Currency Converter lets visitors see prices converted to different currencies using live exchange rates.
How it works: Adds shortcode support for displaying currency conversion rates and converted values within content.
Benefits: Provides dynamic currency information and enables multi-currency content for international audiences.

**Add nofollow to External Links and Open in New Tab:**
What is it: This feature automatically adds rel="nofollow" to every external link and makes those links open in a new tab, protecting your SEO and keeping visitors on your site.
How it works: Automatically scans content for external links and adds rel="nofollow" attribute and target="_blank" to prevent link juice loss and keep visitors on your site.
Benefits: Improves SEO by preserving link authority, enhances user experience by keeping visitors engaged, and reduces bounce rate from external link clicks.

**Enable Nofollow for Post Types:**
What is it: Enable Nofollow for Post Types lets you automatically mark all links on selected post types as nofollow, which is useful for user-generated content.
How it works: Allows you to configure specific post types to automatically have all their links marked with nofollow attributes, useful for user-generated content or specific content types.
Benefits: Protects SEO value from potentially spammy or low-quality content, enables selective link juice management, and provides automated SEO protection.

**Disable Core Sitemaps:**
What is it: Disable Core Sitemaps turns off WordPress's built-in XML sitemap feature, which is helpful when you use an SEO plugin's sitemap instead.
How it works: Removes WordPress default XML sitemaps functionality that was introduced in WordPress 5.5, preventing conflicts with SEO plugins or custom sitemap solutions.
Benefits: Eliminates duplicate sitemap issues, prevents conflicts with advanced SEO plugins, and gives you full control over sitemap generation.

**Exclude Noindex Posts from Search Results:**
What is it: This feature keeps posts marked as noindex out of your site's internal search results, matching what search engines do.
How it works: Automatically removes posts marked with noindex meta tags from WordPress internal search results to match search engine behavior.
Benefits: Maintains consistency between site search and search engine results, prevents confusing search experiences, and ensures proper content visibility control.

**Enable Search Engine Visibility Status:**
What is it: Search Engine Visibility Status shows your current indexing setting in the admin bar and automatically turns off indexing on development sites so they are never crawled.
How it works: Displays the current search engine visibility setting in the admin bar and automatically detects development environments to prevent accidental indexing.
Benefits: Prevents accidental SEO penalties from development sites being indexed, provides constant visibility of indexing status, and protects against staging site indexing.

### Gutenberg

**Disable Gutenberg Editor:**
What is it: Disable Gutenberg Editor swaps the block editor back to the classic editor for the post types you choose.
How it works: Selectively disables the Gutenberg block editor for specific post types and reverts to the classic TinyMCE editor interface.
Benefits: Maintains familiar editing experience for users who prefer classic editor, improves performance on older systems, and ensures compatibility with legacy content workflows.

**Also Disable Frontend Block Styles:**
What is it: Also Disable Frontend Block Styles removes Gutenberg's CSS files from the frontend for post types using the classic editor, keeping pages lean.
How it works: Provides a toggle to remove all Gutenberg block stylesheets from the frontend for selected post types, ensuring no block CSS loads when the classic editor is used.
Benefits: Keeps frontend CSS lean by loading only necessary styles, prevents style conflicts between block and theme CSS, and improves page performance on sites using the classic editor.

**Deregister wp-block-library:**
What is it: Deregister wp-block-library fully removes the block library stylesheet from your page load, a stronger removal than simply dequeuing it.
How it works: Completely deregisters the `wp-block-library` stylesheet using WordPress's `wp_deregister_style()` function, ensuring the block library CSS is fully removed from the page load sequence rather than just dequeued.
Benefits: Provides a more definitive removal of block library CSS than dequeuing alone, eliminates all traces of block library loading, and offers broader compatibility with performance optimization strategies.

**Deactivate Block Directory:**
What is it: Deactivate Block Directory turns off the feature that lets you install blocks directly from the WordPress.org block directory inside the editor.
How it works: Removes the block directory feature that allows installing blocks directly from the WordPress.org block directory within the editor.
Benefits: Improves editor security by preventing unauthorized block installations, speeds up editor loading, and maintains stricter control over site functionality.

**Deactivate Core Block Patterns:**
What is it: Deactivate Core Block Patterns removes WordPress's pre-designed block patterns from the editor, giving you a cleaner block inserter.
How it works: Removes the default WordPress block patterns from the block inserter, providing a cleaner editor interface without pre-designed block layouts.
Benefits: Reduces editor clutter for custom theme development, prevents users from accessing potentially incompatible patterns, and provides cleaner block selection.

**Disable Gutenberg for Widgets:**
What is it: Disable Gutenberg for Widgets reverts the block-based widget editor back to the classic widgets screen.
How it works: Reverts the WordPress 5.8+ widget editor back to the classic widget interface, removing the block-based widget editing experience.
Benefits: Maintains familiar widget management for users, improves widget editing performance, and ensures compatibility with classic widget workflows.

**Deactivate Template Editor:**
What is it: Deactivate Template Editor removes the full-site editing template editor, so theme templates cannot be modified from the admin.
How it works: Removes the full-site editing template editor from the admin interface, preventing users from modifying theme templates through the editor.
Benefits: Protects theme integrity from accidental modifications, maintains developer control over theme structure, and prevents template conflicts.

**Auto Close Welcome Guide:**
What is it: Auto Close Welcome Guide automatically dismisses the Gutenberg welcome guide popup so it does not interrupt you.
How it works: Automatically dismisses the Gutenberg welcome guide popup that appears for new users, eliminating the need for manual dismissal.
Benefits: Streamlines user onboarding experience, reduces interface clutter, and prevents repeated guide displays for experienced users.

**Auto Exit Fullscreen Mode:**
What is it: Auto Exit Fullscreen Mode automatically turns off Gutenberg's fullscreen editing mode so the admin sidebar stays visible.
How it works: Automatically disables the fullscreen editing mode in Gutenberg, ensuring the editor always displays with the admin sidebar visible.
Benefits: Maintains consistent admin interface, provides better workflow integration, and prevents users from getting lost in fullscreen mode.

**Disable "Try Gutenberg" Nag:**
What is it: Disable "Try Gutenberg" Nag removes the promotional notices that encourage you to try Gutenberg features.
How it works: Removes the promotional notices encouraging users to try Gutenberg editor features, eliminating persistent admin notifications.
Benefits: Reduces admin interface clutter, improves user experience, and eliminates unnecessary promotional content.

### Users

**Role Manager:**
What is it: Role Manager lets you create and manage custom user roles and capabilities, and optionally restrict which posts each role can edit.
How it works: Provides a visual interface to create custom roles, assign capabilities, and configure optional post-edit allowlists that limit which posts a role can edit.
Benefits: Gives you precise control over what users can and cannot do, supports complex permission setups, and improves site security through least-privilege access.

**Login & Register Forms With OTP:**
What is it: Login & Register Forms With OTP replaces the standard login and registration forms with modern versions that support one-time password (OTP) sign-in via phone or email.
How it works: Replaces the default WordPress login, registration, and lost-password forms with inline AJAX-powered versions that support one-time password (OTP) authentication via phone (Twilio SMS/WhatsApp) or email (Firebase), enabling passwordless authentication flows.
Benefits: Eliminates password management headaches for users, enhances security with time-limited OTP codes, provides a frictionless login experience, and supports multi-channel OTP delivery for maximum user convenience.

**View Admin as Role:**
What is it: View Admin as Role lets an administrator temporarily view the admin and the site as if they were a different user role, to test what that role sees.
How it works: Allows an administrator to preview the admin interface and frontend exactly as a chosen user role would experience it, without changing any user accounts.
Benefits: Makes it easy to test permissions and layouts for different roles, helps troubleshoot role-specific issues, and verifies what each user type actually sees.

**User Switching:**
What is it: User Switching lets administrators quickly switch into another user's account and switch back, ideal for testing and support.
How it works: Adds a "Switch to" action that lets an administrator temporarily log in as another user, then switch back to their own account instantly.
Benefits: Speeds up testing and support work, lets you experience issues as a specific user, and makes it easy to verify account-specific behavior.

**Username Changer:**
What is it: Username Changer lets eligible users update their own username from their profile page.
How it works: Adds a username field to the profile page that eligible users can edit, with the change applied to their account.
Benefits: Lets users personalize their usernames, removes the need for manual admin changes, and improves user satisfaction.

**Local User Avatar:**
What is it: Local User Avatar lets users upload their own profile picture and use it instead of the standard Gravatar.
How it works: Adds a profile picture upload option that stores the image locally and uses it in place of Gravatar across the site.
Benefits: Gives users control over their profile image, removes reliance on external Gravatar services, and enables custom avatars without extra plugins.

**Disable All Gravatars:**
What is it: Disable All Gravatars removes Gravatar images site-wide, stopping all requests to Gravatar's external servers.
How it works: Completely removes Gravatar functionality from WordPress, preventing any external requests to Gravatar servers and displaying default avatars only.
Benefits: Improves privacy by eliminating external service dependencies, reduces page load times, and maintains consistent avatar display.

**Disable All Avatars:**
What is it: Disable All Avatars turns off every avatar display on your site, including Gravatars and locally uploaded images.
How it works: Disables all avatar displays across the entire site, including Gravatars, local user avatars, and any custom avatar systems, completely suppressing avatar output from all WordPress avatar functions.
Benefits: Maximizes performance gains by eliminating all avatar-related processing and database queries, provides the most thorough avatar removal for minimal designs, and creates the cleanest possible site interface without any avatar elements.

**Show Last Login Column:**
What is it: Show Last Login Column adds a column to the users admin table showing each user's most recent login date and time.
How it works: Adds a column to the users admin table displaying the date and time of each user's most recent login to the website.
Benefits: Helps identify inactive users for cleanup, assists with security monitoring, and provides insights into user engagement patterns.

**Show Registration Date Column:**
What is it: Show Registration Date Column adds a column to the users admin table showing when each user registered.
How it works: Displays the exact date and time each user registered on the website in a dedicated column in the users admin table.
Benefits: Enables user lifecycle analysis, helps with user engagement tracking, and assists with account management and retention strategies.

### Plugins

**Show All Active Plugins on Top:**
What is it: Show All Active Plugins on Top reorganizes your plugins list so active plugins appear first, followed by inactive ones.
How it works: Automatically reorganizes the plugins list page to display all active plugins at the top, followed by inactive plugins, regardless of alphabetical order.
Benefits: Improves plugin management workflow, provides quick access to active plugins, and reduces time spent searching for currently enabled plugins.

**Disable Maintenance Mode Message:**
What is it: Disable Maintenance Mode Message hides the default "briefly unavailable for scheduled maintenance" notice that appears during updates.
How it works: Hides the default WordPress maintenance mode message that appears briefly during core, plugin, or theme updates.
Benefits: Prevents visitor confusion during updates and maintains a professional site appearance during background maintenance.

**Disable Automatic Plugin Update:**
What is it: Disable Automatic Plugin Update stops WordPress from automatically updating plugins in the background, so you approve changes first.
How it works: Prevents WordPress from automatically updating plugins in the background, requiring manual approval for all plugin updates.
Benefits: Maintains control over plugin versions, prevents compatibility issues from unexpected updates, and ensures testing before updates are applied.

**Enable Plugin Maintenance Status:**
What is it: Enable Plugin Maintenance Status analyzes plugins and shows whether each one is actively maintained, outdated, or abandoned.
How it works: Analyzes plugin update history and displays maintenance indicators (actively maintained, outdated, abandoned) in the plugins list based on last update dates.
Benefits: Helps identify potentially insecure or abandoned plugins, assists with security maintenance, and guides plugin replacement decisions.

**Show Admin Warnings for Outdated Plugins:**
What is it: Show Admin Warnings for Outdated Plugins displays admin notices when a plugin has not been updated in over two years.
How it works: Displays admin notices when plugins haven't been updated for more than 2 years, warning about potential security and compatibility issues.
Benefits: Proactively identifies security risks, encourages timely plugin updates, and helps maintain site security standards.

**Advanced Plugin Manager:**
What is it: Advanced Plugin Manager is a power tool for plugin management that adds multiple installation methods and advanced controls beyond the defaults.
How it works: Expands the WordPress plugin screen with extra management and installation options, including multiple ways to install plugins and advanced controls for managing them.
Benefits: Gives you more flexible ways to install and manage plugins, reduces manual server work, and centralizes advanced plugin operations in the admin.

### Logs

**Enable 404 Error Logging:**
What is it: 404 Error Logging records every "page not found" error on your site so you can find and fix broken links.
How it works: Captures and stores detailed information about all 404 errors including URL requested, referrer, user agent, IP address, and timestamp in a database table.
Benefits: Identifies broken internal links, reveals missing content that should be restored, and provides insights for redirect planning and SEO improvements.

**Enable Broken Link Detection:**
What is it: Broken Link Detection automatically scans your content for dead links and reports them with repair suggestions.
How it works: Automatically scans your content for broken internal and external links, checking link availability and reporting dead links with repair suggestions.
Benefits: Maintains site quality by identifying link rot, improves user experience by preventing dead link clicks, and assists with SEO maintenance.

**Enable Redirection & Logging:**
What is it: Redirection & Logging lets you create and manage URL redirects from the WordPress admin and track how each one performs.
How it works: Creates and manages URL redirects directly from the WordPress admin, tracking each redirect's performance, hit count, and source/destination details in a dedicated log for monitoring and analytics.
Benefits: Simplifies redirect management without server configuration, provides comprehensive analytics on redirect performance, identifies redirect chain issues, and offers an audit trail of all URL redirects on the site.

**Enable Search Logging:**
What is it: Search Logging records every search query visitors make on your site, giving you insight into what users are looking for.
How it works: Records all search queries performed on your site including search terms, results count, user information, and timestamp data for analytics.
Benefits: Provides insights into user intent and content gaps, helps improve site search functionality, and guides content creation strategy.

**Enable WP Debug Logging:**
What is it: WP Debug Logging gives you a clean admin interface to view and manage the WordPress debug.log file without FTP access.
How it works: Provides an admin interface to view, filter, and manage WordPress debug.log files without requiring FTP access or file system navigation.
Benefits: Simplifies debugging process for developers, enables quick error identification, and provides user-friendly access to technical logs.

---

## WooCommerce Tab

### Product Swatches

**Product Swatches:**
What is it: Product Swatches turn the default dropdown menus for product variations into visual color, image, and label selectors that are easier and faster to use.
How it works: Transforms product attributes into clickable swatches (colors, images, labels) that customers can select directly instead of picking from a dropdown, with styling options to match your store.
Benefits: Makes choosing variations faster and more visual, reduces selection errors, improves the shopping experience, and can lift conversion rates.

**Show Swatches on Archive Pages:**
What is it: Show Swatches on Archive Pages displays product swatches right on your shop and category pages, so customers can pick variations without opening the product page.
How it works: Display product swatches on shop and category pages for quick variation selection without visiting the product page.
Benefits: Enables quick product variation selection without visiting product pages, improves browsing experience, and can increase conversion rates.

**Show Swatches in Filters:**
What is it: Show Swatches in Filters replaces the text-based attribute filters in your shop search widgets with visual swatches.
How it works: Replace text-based attribute filters in WooCommerce layered navigation widgets with visual swatches.
Benefits: Creates more intuitive filtering experience, improves visual appeal of shop pages, and makes product discovery more engaging.

**Out of Stock Variations:**
What is it: Out of Stock Variations visually marks swatches for sold-out options, so customers can see at a glance which variations are unavailable.
How it works: Visually disables or marks out-of-stock variation swatches (blur, cross, or hide) so customers can tell at a glance which options are unavailable.
Benefits: Prevents frustration from selecting unavailable options, makes inventory status clear, and guides shoppers toward in-stock choices.

**Enable Tooltip:**
What is it: Enable Tooltip adds a helpful label that appears when customers hover over a swatch, showing what each option is.
How it works: Adds descriptive tooltips to product swatches that appear on hover, showing the attribute label or custom text to help customers identify each swatch option.
Benefits: Improves customer understanding of swatch options, reduces selection errors by providing clear labels on hover, and enhances the shopping experience with informative tooltips.

**Enable Custom Tooltip:**
What is it: Enable Custom Tooltip lets you style the swatch tooltip to match your brand instead of using the browser default.
How it works: Use custom tooltip styling instead of browser default tooltips for better visual consistency and branding, with configurable position (top/bottom) and color options.
Benefits: Provides better visual consistency with site branding, improves accessibility with larger readable tooltips, and enhances user understanding of product options.

### Single Product

**Customize Add to Cart Button Text:**
What is it: Customize Add to Cart Button Text lets you change the "Add to Cart" button wording for different product types, stock levels, users, and categories.
How it works: Customize the "Add to Cart" button text for different product types and contexts including simple, variable, grouped, and external products, with options for product loops, single pages, dynamic stock-based text, personalized text for different user types, and category-specific text.
Benefits: Improves conversion rates with targeted button text, creates urgency with dynamic stock messaging, enables personalized shopping experiences, and optimizes call-to-action messaging for different product contexts.

**Customize Out of Stock Button Text:**
What is it: Customize Out of Stock Button Text replaces the default "Read More" on sold-out products with your own message, like "Out of Stock" or "Sold Out", or hides the button entirely.
How it works: Replaces the default "Read More" button text for out-of-stock products with custom messaging like "Out of Stock" or "Sold Out", with options to make buttons disabled, link to product pages, or hide them completely.
Benefits: Improves user experience with clear product availability messaging, prevents customer confusion about unavailable products, and provides professional out-of-stock display options.

**Show Price Savings:**
What is it: Show Price Savings displays how much a customer saves on a sale product using a `[price_savings]` shortcode.
How it works: Displays price savings on sale products using the [price_savings] shortcode, with configurable prefix text, suffix text, and display options for showing both percentage and amount savings.
Benefits: Highlights value propositions to customers, increases sales conversion with visible savings, and provides clear discount information that motivates purchases.

**Show Percentage Off:**
What is it: Show Percentage Off displays the discount percentage on sale products, like "20% off", right on the product page.
How it works: Shows the percentage discount on sale products by calculating the discount rate from original prices, with custom formatting and display options.
Benefits: Creates urgency and value perception, improves sales conversion rates, and provides easily understood discount information for customers.

**Remove Clear Variation Link:**
What is it: Remove Clear Variation Link takes away the "Clear" option next to variation selections, preventing customers from accidentally deselecting a choice.
How it works: Removes the "Clear" link that allows customers to deselect chosen product variations.
Benefits: Prevents accidental variation clearing, streamlines the selection process, and reduces customer confusion during product configuration.

**Auto-select First Variation:**
What is it: Auto-select First Variation automatically chooses the first available variation when a customer opens a variable product page, saving them a step.
How it works: Automatically selects the first available product variation when customers visit variable product pages.
Benefits: Speeds up customer decision-making, improves user experience, and can increase conversion rates by reducing steps to purchase.

**Disable Out of Stock Variations:**
What is it: Disable Out of Stock Variations makes unavailable variations non-selectable, so customers cannot pick options that are sold out.
How it works: Visually disable or hide swatches for out-of-stock product variations, with configurable behavior (blur with cross, blur only, or completely hide).
Benefits: Prevents customer frustration with unavailable options, improves inventory management presentation, and guides customers toward available products.

**Update Price on Variation Selection:**
What is it: Update Price on Variation Selection refreshes the displayed price the moment a customer picks a variation, so they always see the right price.
How it works: Dynamically update price when variations are selected.
Benefits: Provides immediate price feedback, improves transparency, and helps customers make informed purchasing decisions.

**Hide Default Variation Price:**
What is it: Hide Default Variation Price hides the starting price on variable products until a customer actually selects a variation.
How it works: Hide the default price display for variable products.
Benefits: Reduces price confusion, focuses customer attention on selected variation pricing, and creates cleaner product presentations.

**Disable Product Reviews:**
What is it: Disable Product Reviews turns off the WooCommerce review system, removing review forms and displays from product pages.
How it works: Completely disables the WooCommerce product review system, removing review forms and review displays from product pages.
Benefits: Simplifies product pages for stores that don't need reviews, reduces spam management overhead, and provides cleaner product layouts for specialty stores.

**Allow Duplicate Reviews:**
What is it: Allow Duplicate Reviews lets customers submit more than one review for the same product.
How it works: Allow customers to submit multiple reviews for the same product.
Benefits: Enables customers to update reviews based on extended use, captures evolving product experiences, and provides richer review data.

**Product Price History:**
What is it: Product Price History tracks past prices and displays the lowest historical price on sale products, a requirement for EU Omnibus Directive compliance.
How it works: Tracks price changes automatically when products or variations are updated, storing historical data in a dedicated database table. Displays the lowest price from a configurable lookback period on sale products with selectable calculation mode (from sale start or rolling window), fallback behavior, display type (Regular, Text, or Alternative below product meta), variable product display options, display location toggles (product page, shop, categories, tags, related/upsell), and custom labels for both lowest and current price. Includes a `[cm_price_history]` shortcode with id/variation_id/show_currency attributes, a dedicated widget, and an admin meta box on the product edit screen with inline editing, apply, and delete capabilities. Supports both simple and variable products with per-variation price tracking.
Benefits: Ensures EU Omnibus Directive compliance for consumer protection, builds customer trust through price transparency, reduces legal risk with automated price history tracking, and provides a complete price audit trail for all products.

### Checkout

**Remove Company Field:**
What is it: Remove Company Field deletes the company name input from your checkout form, making it shorter and faster to fill out.
How it works: Removes the company name field from WooCommerce checkout forms to streamline the checkout process.
Benefits: Simplifies checkout for B2C customers, reduces form abandonment, and speeds up the purchase process.

**Enable Checkout Field Placeholders:**
What is it: Enable Checkout Field Placeholders adds example text inside checkout fields, showing customers exactly what to enter.
How it works: Adds placeholder text inside checkout form fields to guide customer input and improve form usability.
Benefits: Improves form completion rates, provides clear input guidance, and enhances overall checkout user experience.

**Enable Inline Checkout Field Validation:**
What is it: Enable Inline Checkout Field Validation checks checkout fields in real time as customers type, flagging errors before they submit.
How it works: Provides real-time inline validation on all checkout fields as customers fill in their information, highlighting errors and showing success indicators before form submission.
Benefits: Reduces checkout errors by catching issues early, improves form completion rates with instant feedback, and enhances user experience with clear visual indicators of valid and invalid fields.

**Remove Order Notes Field:**
What is it: Remove Order Notes Field deletes the order notes textarea from checkout, trimming an optional field most customers skip anyway.
How it works: Removes the order notes textarea field from the WooCommerce checkout page to streamline the checkout form and reduce visual clutter.
Benefits: Simplifies the checkout form for faster completion, reduces customer decision points during checkout, and can improve conversion rates by eliminating non-essential form fields.

**Show Product Images in Checkout:**
What is it: Show Product Images in Checkout displays a picture of each product next to its name on the checkout page, confirming exactly what the customer is buying.
How it works: Displays product images on the checkout page next to product names, with configurable image size (thumbnail, medium, large, or custom) and style options.
Benefits: Improves customer confidence by showing what they're purchasing, reduces cart abandonment through visual confirmation, and creates a more professional checkout experience.

**Custom Order Review Heading:**
What is it: Custom Order Review Heading changes the "Order Review" heading text on your checkout page to fit your brand.
How it works: Customize the "Order Review" heading text on the checkout page to match your store branding.
Benefits: Creates consistent branding throughout checkout, improves customer orientation, and enables personalized checkout messaging.

**Custom Place Order Button:**
What is it: Custom Place Order Button changes the text and icon of the "Place Order" button on checkout, so it can say exactly what you want.
How it works: Customize the "Place Order" button text, icon, and icon position on the checkout page.
Benefits: Improves call-to-action messaging, creates branded checkout experience, and enables conversion-optimized button text.

### One Click Checkout

**Enable WooCommerce Direct Checkout Links:**
What is it: Direct Checkout Links let you create special URLs that skip the cart and send customers straight to checkout for a specific product.
How it works: Creates direct checkout links for products using SKU or product ID URL parameters.
Benefits: Enables marketing campaigns with direct purchase links.

**Enable Checkout Product Selector:**
What is it: Checkout Product Selector adds a small product picker on the checkout page so customers can add last-minute items before paying.
How it works: Adds a product selector widget to the checkout page for last-minute additions.
Benefits: Increases average order value through checkout upsells.

**Show Product Prices:**
What is it: Show Product Prices displays the cost of products in the checkout product selector, so customers see the price before moving to the cart.
How it works: Displays product prices in the checkout product selector and direct checkout interface, showing customers the cost before they proceed to the checkout page.
Benefits: Provides price transparency during checkout navigation, helps customers make informed purchase decisions, and can increase conversion rates by eliminating price uncertainty.

**Enable Variable Product Support:**
What is it: Enable Variable Product Support makes direct checkout links work with variable products, letting customers choose size or color before checkout.
How it works: Enables variable product support in direct checkout links, allowing customers to select specific product variations (size, color, etc.) before being redirected to checkout.
Benefits: Expands direct checkout functionality to all product types, enables promotional campaigns for variable products, and ensures customers can purchase the exact variation they want through direct links.

**Show Custom Quantity Generator:**
What is it: Show Custom Quantity Generator adds a quantity selector to your direct checkout links so customers can choose how many they want before paying.
How it works: Displays a custom quantity selector interface alongside direct checkout links, allowing customers to specify the desired quantity before being redirected to checkout.
Benefits: Increases order values by enabling bulk purchases through direct checkout links, provides flexible quantity selection for promotional campaigns, and improves the one-click checkout experience with quantity control.

**Enable Auto-Completion for Virtual/Downloadable Products:**
What is it: Auto-Completion for Virtual/Downloadable Products automatically marks digital orders as completed once payment goes through, so customers get their downloads instantly.
How it works: Automatically transitions WooCommerce orders containing only virtual or downloadable products to a Completed status upon payment confirmation, with configurable product type logic, audit logging, and optional email notifications.
Benefits: Streamlines digital product fulfillment by removing manual processing steps, provides instant customer access to purchased downloads, reduces admin workload for digital order management, and maintains a complete audit trail of auto-completed orders.

### Coupons

**Enable Auto-Apply Coupons:**
What is it: Auto-Apply Coupons automatically applies eligible discounts to the cart, so customers never miss a coupon they qualify for.
How it works: Automatically applies eligible coupons to the cart when predefined conditions (cart contents, total, user role, time) are met, prioritizing highest-value coupons and displaying success notifications.
Benefits: Ensures customers never miss available discounts, increases conversion rates through automatic savings, reduces cart abandonment from coupon search frustration, and provides detailed analytics on auto-applied coupon performance.

**Enable URL Coupons:**
What is it: URL Coupons let people apply a coupon just by clicking a link, like ?coupon=SUMMER10, which is perfect for campaigns.
How it works: Lets you apply coupons via a shareable URL parameter (e.g., ?coupon=SUMMER10). Supports custom parameter names, UTM-source tracking, automatic success notices, optional redirection (cart / checkout / shop), and an admin metabox & shortcode to generate links. Includes stringent validation and logging to keep campaigns secure and measurable.
Benefits: Perfect for email, social, or affiliate campaigns, customers get discounts with a single click, boosting click-through and conversion while providing accurate marketing analytics.

**Enable Maximum Discount Amount for Coupons:**
What is it: Maximum Discount Amount for Coupons caps how much discount a coupon can apply, protecting your margins.
How it works: Adds a "Maximum Discount Settings" metabox to coupons and a global default setting. The discount applied is automatically capped so it never exceeds the defined amount. Advanced options include role-based, time-based, category-specific, and tiered (cart-total) limits, real-time preview for admins, REST API exposure, and detailed analytics.
Benefits: Protects margins by preventing excessive discounts, offers enterprise-level control over promotions, and integrates seamlessly with all coupon types and HPOS.

**Enable Time-Based Maximum Discounts:**
What is it: Time-Based Maximum Discounts sets a cap on how much discount can apply during specific hours, days, or date ranges.
How it works: Sets time-based limits on the maximum discount amount for coupons, restricting how much discount can be applied during specific hours, days, or date ranges for targeted promotional control.
Benefits: Enables time-sensitive promotions with discount caps, prevents excessive discounting during peak hours, and provides granular control over when maximum discount limits apply.

**Enable Role-Based Maximum Discounts:**
What is it: Role-Based Maximum Discounts sets different discount caps for different user roles, like higher caps for VIP customers.
How it works: Configures different maximum discount amounts for different user roles, allowing higher discounts for VIP customers or restricting maximum discounts for standard users.
Benefits: Enables loyalty-based discount structures, provides preferential pricing for premium members, and prevents excessive discount abuse across different user segments.

**Enable Category-Specific Maximum Discounts:**
What is it: Category-Specific Maximum Discounts applies different discount caps per product category, letting you discount clearance items more aggressively.
How it works: Sets different maximum discount limits for products in specific categories, enabling higher discounts for clearance items while capping discounts on high-margin categories.
Benefits: Provides category-level discount control, enables strategic pricing across product lines, and prevents margin erosion on premium product categories.

**Enable Single Coupon Restriction:**
What is it: Single Coupon Restriction limits the cart to one coupon at a time, preventing stacked discounts.
How it works: Restricts the cart to only one coupon at a time, replacing any previously applied coupon when a new one is entered.
Benefits: Prevents coupon stacking abuse, simplifies discount management, ensures pricing control, and avoids unintended discount combinations.

**Enable BOGO (Buy One Get One) Deals:**
What is it: BOGO Deals let you run "Buy X Get Y" promotions, like buy one get one free or buy two get one at a discount.
How it works: Provides configurable Buy X Get Y rules where the customer buys a qualifying quantity and receives the promotional item, with flexible settings for which products qualify, quantities, and discount amounts.
Benefits: Drives higher order values with proven promotional mechanics, clears inventory with attractive offers, and gives you flexible control over buy-item, get-item, and quantity rules.

**Enable First-Time Customer Coupons:**
What is it: First-Time Customer Coupons automatically detects new customers and gives them a welcome discount to encourage their first purchase.
How it works: Detects whether a customer has ordered before and automatically applies a configured welcome coupon to new customers' first orders, rewarding registration and first purchases.
Benefits: Converts new visitors into paying customers, incentivizes first orders with an automatic welcome offer, and rewards account creation without manual coupon distribution.

**Enable User Role Coupon Restrictions:**
What is it: User Role Coupon Restrictions limits which coupons each user role can use, so offers only reach the right people.
How it works: Restrict coupons to specific user roles for enhanced targeting. Allows setting role-based access controls, custom error messages for unauthorized users, and detailed restriction rules based on membership levels or customer types.
Benefits: Enables sophisticated customer segmentation strategies, provides exclusive offers for premium members, and ensures promotional campaigns reach only intended audience segments while maintaining security.

### Orders

**Enable Thank You Page Link in Orders:**
What is it: Thank You Page Link in Orders adds a direct link in the admin orders table that opens each order's thank you page.
How it works: Adds a link to the order's thank you page in the WooCommerce admin orders table, giving store owners one-click access to the post-purchase page for any order.
Benefits: Makes it easy to verify what customers see after purchase, speeds up order review workflows, and provides quick access to each order's success page.

**Enable Custom Order Status:**
What is it: Custom Order Status lets you create additional order statuses beyond WooCommerce's defaults to fit your workflow.
How it works: Add and manage custom order statuses.
Benefits: Provides more granular order management, improves workflow organization, and enables custom business process integration.

**Enable Custom Order Columns:**
What is it: Custom Order Columns adds extra columns to the admin orders table, like payment method, shipping details, and customer info.
How it works: Adds additional columns to the WooCommerce orders table including payment method, shipping details, customer information, order totals, and more.
Benefits: Provides comprehensive order overview at a glance, improves order management efficiency, and enables better customer service.

### My Account

**Remove Display Name:**
What is it: Remove Display Name takes the display name field out of the account settings, removing an unnecessary option from customer profiles.
How it works: Removes the display name field from the WooCommerce My Account settings area, so customers no longer see or edit it.
Benefits: Simplifies the account settings page, reduces customer confusion about profile fields, and creates a cleaner account experience.

**Remove Order Number Column:**
What is it: Remove Order Number Column hides the order number column from the admin orders page for a cleaner table.
How it works: Removes the order number column from the WooCommerce admin orders table when enabled.
Benefits: Simplifies the admin orders view, reduces visual clutter, and lets you focus on the order columns that matter most.

### Optimization

**Disable WooCommerce scripts and styles on non-Woo pages:**
What is it: Disable WooCommerce scripts and styles on non-Woo pages stops WooCommerce from loading its CSS and JavaScript on pages that are not related to the shop.
How it works: Detects whether the current page uses WooCommerce functionality and, when it does not, prevents the store's scripts and styles from loading on that page.
Benefits: Makes non-shop pages load faster with less code, improves page speed scores, and reduces unnecessary browser work on blog and content pages.

**Disable WooCommerce cart fragmentation:**
What is it: Disable WooCommerce cart fragmentation stops the cart fragment refresh that can cause performance problems, especially with caching.
How it works: Prevents WooCommerce from fragmenting the cart for caching, which can cause performance issues with some caching solutions.
Benefits: Improves caching compatibility, enhances site performance, and reduces server resource usage.

**Disable WooCommerce status meta box:**
What is it: Disable WooCommerce status meta box removes the status widget from the WordPress dashboard.
How it works: Removes the WooCommerce status widget from the WordPress admin dashboard to reduce admin clutter.
Benefits: Simplifies admin dashboard, improves page load speed, and reduces unnecessary admin functionality.

**Disable All Admin Features:**
What is it: Disable All Admin Features turns off the entire WooCommerce admin interface, useful for headless stores or sites that only need the frontend shop.
How it works: Disables all WooCommerce admin-facing features and screens while leaving the frontend store functionality working.
Benefits: Removes WooCommerce admin clutter for stores managed elsewhere, reduces backend complexity, and keeps the dashboard focused.

**Disable Marketplace Suggestions:**
What is it: Disable Marketplace Suggestions removes WooCommerce's marketplace and promotional suggestions from your admin.
How it works: Removes WooCommerce marketplace suggestions and promotional content from the admin interface.
Benefits: Reduces admin clutter, eliminates distracting promotional content, and provides cleaner admin experience.

**Disable Gutenberg Blocks Styles:**
What is it: Disable Gutenberg Blocks Styles stops WooCommerce's Gutenberg block styles from loading, which can reduce page weight.
How it works: Prevents the stylesheet for WooCommerce Gutenberg blocks from loading on the frontend when those blocks are not in use.
Benefits: Reduces unnecessary CSS on the frontend, improves page speed, and avoids style conflicts with your theme.

**Disable All WooCommerce Widgets:**
What is it: Disable All WooCommerce Widgets removes every WooCommerce widget from the widgets area, preventing accidental use.
How it works: Removes all WooCommerce widgets from the widgets admin area to prevent accidental use and reduce options.
Benefits: Simplifies widget management, prevents widget conflicts, and reduces admin complexity.

### Redirection

**Redirect if cart is empty:**
What is it: Redirect if cart is empty sends visitors who land on an empty cart page to the shop instead of a dead end.
How it works: Redirects customers away from the cart page to the shop page (or custom URL) when their cart is empty, preventing visitors from encountering a dead-end empty cart page.
Benefits: Guides visitors back to browsing and shopping, reduces bounce rates from empty cart pages, and increases potential sales by redirecting to product discovery pages.

**Redirect logged-in users from login page:**
What is it: Redirect logged-in users from login page sends users who are already signed in away from the login page straight to My Account.
How it works: Detects when a logged-in user visits the login page and redirects them to their My Account page instead of showing the login form.
Benefits: Eliminates a pointless step for returning customers, prevents confusion about already being logged in, and guides users straight to their account area.

**Redirect after logout:**
What is it: Redirect after logout lets you choose where users land after they log out, instead of staying on the current page.
How it works: Configures a custom redirect destination for users after they log out, allowing you to send them to a specific page, the home page, or the login page instead of staying on the current page.
Benefits: Provides a controlled post-logout experience, enables branded logout workflows, and prevents users from lingering on protected pages after logout.

**Redirect My Account for non-logged in users:**
What is it: Redirect My Account for non-logged in users sends guests who visit My Account to the login page.
How it works: Configure redirection for non-logged users.
Benefits: Prevents unauthorized access to account pages, improves security, and provides appropriate landing pages for guest users.

### Email

**Disable WooCommerce Emails:**
What is it: Disable WooCommerce Emails turns off every WooCommerce transactional email, like order confirmations and shipping notices.
How it works: Completely disables all WooCommerce email notifications including order confirmations, shipping notices, and admin notifications.
Benefits: Prevents email overload, allows custom email solutions, and provides complete control over customer communication timing and content.

**Allow Reset Password Email:**
What is it: Allow Reset Password Email is the selective version of disabling WooCommerce email, keeping only password reset messages active.
How it works: Disables all WooCommerce transactional emails except password reset emails, which remain active so account recovery still works.
Benefits: Silences routine store notifications while keeping essential account recovery emails functional.

---

## Bricks Builder Tab

### Setup

**Start Bricks Setup:**
What is it: Start Bricks Setup imports ready-made Bricks Builder Theme Styles, Global Settings, and Templates to give you a head start on a new build.
How it works: Import Bricks Builder Theme Styles, Global Settings and Templates through an automated setup process with file selection options for theme styles, global settings, and templates.
Benefits: Provides quick setup for new Bricks installations, ensures consistent design implementation, and saves hours of manual configuration work.

**Live Code Sync & Import:**
What is it: Live Code Sync & Import adds a native HTML, CSS, and JS panel inside the Bricks builder so you can edit code and see changes in real time, or import HTML directly into Bricks elements.
How it works: Adds a native HTML, CSS, and JS sync panel inside the Bricks builder for live bi-directional editing and HTML to Bricks import workflows.
Benefits: Accelerates development with real-time code editing and enables seamless HTML-to-Bricks conversion.

**BEM Class Generator:**
What is it: BEM Class Generator creates Block__Element class names automatically from the right-click context menu, keeping your CSS naming consistent.
How it works: Adds a BEM Generator to the Bricks builder right-click context menu. Generates Block__Element class names.
Benefits: Enforces consistent CSS naming conventions and speeds up class management.

**Variable Picker:**
What is it: Variable Picker lets you right-click any Bricks control to see and insert compatible CSS variables instead of typing their names from memory.
How it works: Right-click any Bricks element control to open a popover listing compatible CSS variables.
Benefits: Eliminates the need to remember variable names and promotes consistent use of design tokens.

**SVG <> Image Converter:**
What is it: SVG <> Image Converter swaps SVG elements to Image elements and back with a right-click action, keeping your workflow flexible.
How it works: Adds a context menu action to convert SVG elements to Image elements and vice versa.
Benefits: Provides flexible SVG workflow and maintains visual fidelity during conversions.

**Auto-select First Class:**
What is it: Auto-select First Class automatically activates the first unlocked class when you select an element that has a CSS class, saving a click.
How it works: Automatically activates the first unlocked class in the classes panel when an element with a CSS class is selected.
Benefits: Reduces manual clicks during styling and speeds up class-based editing.

**Auto Complete var():**
What is it: Auto Complete var() automatically wraps CSS custom properties in var() as you type, keeping your syntax correct.
How it works: Automatically wraps CSS custom properties in var() when pressing Enter or semicolon.
Benefits: Saves keystrokes during CSS editing and ensures proper var() syntax.

**Auto Complete calc():**
What is it: Auto Complete calc() automatically wraps arithmetic expressions in calc() when you finish typing them.
How it works: Automatically wraps arithmetic expressions in calc() when pressing Enter or semicolon.
Benefits: Speeds up responsive calculations and ensures proper calc() syntax.

**Move Bricks Toolbar to Bottom:**
What is it: Move Bricks Toolbar to Bottom moves the builder toolbar from the top to the bottom of the screen.
How it works: Moves the Bricks Builder toolbar from top to bottom of the screen for improved accessibility and visibility with custom CSS positioning.
Benefits: Improves accessibility for shorter screens, provides better visibility of design elements, and enables more natural workflow positioning.

**Hide Elements Icons:**
What is it: Hide Elements Icons removes the icons next to elements in the Bricks panel for a cleaner, text-only look.
How it works: Hides icons next to elements in the Bricks Builder interface for a cleaner look with optional text-only element listings.
Benefits: Provides cleaner interface design, reduces visual clutter, and enables focus on element names rather than icons.

**Compact Elements With Icons:**
What is it: Compact Elements With Icons makes the elements list more compact while keeping the icons so you can scan more items on screen.
How it works: Makes elements more compact while retaining their icons through optimized spacing and layout adjustments.
Benefits: Saves interface space, maintains visual recognition, and provides more efficient element browsing.

**Wide Elements Panel:**
What is it: Wide Elements Panel makes the elements panel wider so element names are easier to read and select.
How it works: Makes elements wider in the Bricks Builder interface for better readability and easier selection through expanded panel width.
Benefits: Improves element readability, enables easier selection, and provides better element name visibility.

**Improve Builder UI Basics:**
What is it: Improve Builder UI Basics polishes the padding, spacing, and basic elements of the Bricks interface for a cleaner feel.
How it works: Optimizes padding, spacing, and basic elements of the Bricks Builder interface with refined CSS styling and layout improvements.
Benefits: Provides cleaner interface design, improves usability, and enhances overall builder experience through better visual hierarchy.

**Enhanced Active Element Highlighting:**
What is it: Enhanced Active Element Highlighting makes the element you are working on more prominent with stronger contrast.
How it works: Makes active elements more prominent with better color contrast and visibility through enhanced styling and visual indicators.
Benefits: Improves element selection feedback, reduces design confusion, and provides clearer visual cues during editing.

**Enhance Style Panel Visibility:**
What is it: Enhance Style Panel Visibility improves the background contrast of open style panels so it is clear which panel is active.
How it works: Improves the visibility of open style panels with better background contrast and visual separation for clearer panel identification.
Benefits: Reduces panel confusion, improves workflow efficiency, and provides clearer visual organization of builder interface.

**Enhance Control Separators:**
What is it: Enhance Control Separators makes the dividers between controls more distinct, so sections are easier to scan.
How it works: Makes control separators more visually distinct with improved styling and spacing for better organization.
Benefits: Improves interface organization, reduces visual clutter, and provides clearer separation between control groups.

**Improve Setting Indicators:**
What is it: Improve Setting Indicators makes modified settings more visible, so you can always see what you have changed.
How it works: Enhances the visibility of indicators for settings that have been modified with better visual feedback and status indicators.
Benefits: Provides clear modification feedback, improves setting management, and prevents accidental setting loss.

**Exclude Bricks Builder from Sitemap:**
What is it: Exclude Bricks Builder from Sitemap removes the Bricks Builder sitemap from WordPress, Rank Math, and other sitemap plugins to avoid duplicates.
How it works: Disables Bricks Builder Sitemap from Default WordPress Sitemap, Rank Math Sitemap & XML Sitemap Generator for Google plugins to prevent duplicate sitemaps.
Benefits: Eliminates sitemap conflicts, prevents SEO duplicate content issues, and provides clean sitemap management.

### Elements

#### Core Elements

**Dismissible Notice:**
What is it: Dismissible Notice is a notification bar you can place anywhere, with a close button so visitors can dismiss it.
How it works: Adds a customizable notification bar that users can dismiss, with options for styling, positioning, content, and persistence settings that can be displayed site-wide or on specific pages.
Benefits: Improves user communication for announcements and promotions, provides non-intrusive messaging, and allows temporary notifications that don't overwhelm users.

**Number Counter:**
What is it: Number Counter animates numbers from zero to a target value when the element scrolls into view, perfect for stats and achievements.
How it works: Creates smooth number animations that trigger when entering the viewport, with customizable start/end values, animation duration, number formatting, and scroll-based triggering.
Benefits: Creates engaging visual presentations for statistics and achievements, improves user engagement through interactive animations, and provides professional data visualization.

**Like/Dislike:**
What is it: Like/Dislike adds an upvote/downvote control to an element, with the votes stored in the database.
How it works: Allows users to like or dislike anything with database storage, tracking user preferences, displaying vote counts, and preventing duplicate voting from same users.
Benefits: Increases user engagement and interaction, provides valuable feedback on content quality, and builds community participation through voting mechanisms.

**Text Image Split:**
What is it: Text Image Split creates balanced layouts that pair text with complementary images for better readability.
How it works: Enhance readability and improve visual appeal by creating layouts that intelligently split text content with complementary images in responsive, balanced compositions.
Benefits: Improves content readability and visual hierarchy, creates more engaging page layouts, and helps break up long text blocks for better user experience.

**Negative Click:**
What is it: Negative Click lets you trigger actions on an element from a click anywhere on the page, giving you remote control over sliders, tabs, and modals.
How it works: Add click triggers to elements from anywhere on the page using CSS selectors, enabling remote control of sliders, tabs, modals, and other interactive elements.
Benefits: Creates more intuitive user interfaces, enables creative interaction design, and allows flexible control schemes for complex page layouts.

**Falling Items:**
What is it: Falling Items adds a physics-based falling animation, like items dropping onto the page, with adjustable gravity and bounce.
How it works: Adds physics-based falling items animation with customizable gravity, bounce effects, item types, and trigger conditions for engaging visual effects.
Benefits: Creates memorable interactive experiences, adds playful elements to serious content, and provides unique visual effects that differentiate your site.

**Hovering Text Image:**
What is it: Hovering Text Image reveals an image smoothly when a visitor hovers over text, adding a dynamic storytelling element.
How it works: Reveals images smoothly on text hover with customizable transition effects, positioning options, and image sources that create dynamic visual feedback.
Benefits: Creates engaging interactive experiences, improves visual storytelling, and provides elegant way to showcase related imagery without cluttering layouts.

**Classic Swatches:**
What is it: Classic Swatches adds a swatches element to Bricks that shows WooCommerce product variations as visual color, image, and label selectors.
How it works: Add Swatches Element in Bricks Builder that displays product variations as visual swatches with color, image, and label options for WooCommerce products.
Benefits: Improves product presentation and user experience, increases conversion rates through better product visualization, and provides professional e-commerce functionality.

**Remaining Swatches:**
What is it: Remaining Swatches displays a count of hidden variation swatches using the `{cm_remaining_swatches}` tag, so customers know more options exist.
How it works: Use `{cm_remaining_swatches}` to display count of hidden variation swatches, calculating and showing how many additional swatches are available beyond the displayed limit.
Benefits: Informs customers about additional product options, improves product discovery, and provides transparency about available variations.

**Selected Variables:**
What is it: Selected Variables displays the product variations a customer has currently chosen, confirming their selection in real time.
How it works: Add Selected Variables Element to display dynamic product variation selections, showing currently chosen options with styling and formatting controls.
Benefits: Provides clear confirmation of customer selections, reduces ordering errors, and improves checkout confidence through visual selection feedback.

**Image Hotspots:**
What is it: Image Hotspots places interactive markers on an image that reveal tooltips or links when clicked, great for product showcases and diagrams.
How it works: Add interactive hotspots to images with tooltips and links, supporting multiple hotspot types, custom styling, and responsive positioning.
Benefits: Creates interactive image experiences, enables detailed product showcases, and provides engaging way to present complex visual information.

**Classic Hotspots (Nestable):**
What is it: Classic Hotspots (Nestable) lets you add interactive hotspots to any Bricks element using CSS selectors, not just images.
How it works: Add interactive hotspots to any Bricks element using CSS selectors, enabling hotspot functionality on containers, sections, and custom elements.
Benefits: Provides flexible interactivity options, enables complex user interfaces, and allows creative hotspot implementations beyond just images.

**Stacked Images:**
What is it: Stacked Images arranges multiple images in a stacked, overlapping layout with tooltips and hover effects.
How it works: Adds stacked/overlapping images element with tooltip support, depth effects, hover animations, and responsive stacking options.
Benefits: Creates visually appealing image galleries, showcases multiple related images efficiently, and provides space-saving image presentation solutions.

**Animated Borders:**
What is it: Animated Borders adds CSS-based animated borders to elements with triggers like hover, scroll, or page load.
How it works: Adds CSS-based animated borders for elements with various animation styles, trigger conditions (hover, scroll, load), and customizable appearance options.
Benefits: Enhances visual appeal with subtle animations, draws attention to important elements, and provides modern design effects without performance impact.

**PDF Viewer:**
What is it: PDF Viewer embeds a PDF on your page with a download option, so documents can be viewed without external services.
How it works: Adds PDF viewer element with download option, supporting embedded viewing, custom controls, responsive sizing, and download protection features.
Benefits: Enables document sharing without external services, provides secure document viewing, and improves user experience for document-heavy sites.

**Infinite Scroller:**
What is it: Infinite Scroller is a continuously moving image carousel for showcasing large collections of images.
How it works: Adds an infinite scrolling image carousel element with continuous movement, customizable speed, direction control, and smooth transitions.
Benefits: Creates engaging visual displays, showcases large image collections efficiently, and provides modern scrolling experiences that capture user attention.

**Classic Tables:**
What is it: Classic Tables builds advanced data tables with sorting, searching, and pagination built in.
How it works: Adds advanced tables with sorting, searching and pagination features, supporting custom styling, responsive design, and data import/export capabilities.
Benefits: Presents complex data in user-friendly format, improves data accessibility and navigation, and provides professional data presentation without coding.

**Image Compare:**
What is it: Image Compare is a before/after slider that lets visitors drag between two versions of an image to see the difference.
How it works: Adds an image comparison slider element with before/after views, supporting vertical/horizontal sliding, custom handles, and responsive design.
Benefits: Effectively demonstrates changes and improvements, perfect for portfolios and case studies, and provides engaging way to showcase transformations.

**Gallery Zoom:**
What is it: Gallery Zoom builds an interactive gallery with lightbox viewing, zoom, thumbnail navigation, and swipe support.
How it works: Adds interactive gallery with zoom and navigation features, supporting lightbox viewing, thumbnail navigation, and touch/swipe controls.
Benefits: Provides professional image viewing experience, showcases photography and products effectively, and improves user engagement with visual content.

**Nestable Gallery Zoom:**
What is it: Nestable Gallery Zoom is a version of the gallery zoom that can be placed inside other Bricks elements and complex layouts.
How it works: Adds nestable version of the gallery zoom with container capabilities, allowing gallery functionality within other Bricks elements and complex layouts.
Benefits: Enables flexible gallery implementations, supports complex page designs, and provides gallery functionality within custom layouts and sections.

**Saved Amount:**
What is it: Saved Amount displays how much money a customer saves on a sale product by comparing the regular and sale prices.
How it works: Displays the amount saved on sale products by calculating the difference between regular and sale prices, with customizable formatting and styling options.
Benefits: Highlights value propositions to customers, increases sales conversion rates, and provides clear savings information that motivates purchases.

**Percentage Off:**
What is it: Percentage Off shows the discount percentage on sale products, like "15% off", right on the product page.
How it works: Shows the percentage discount on sale products by calculating the discount rate from original prices, with custom formatting and display options.
Benefits: Creates urgency and value perception, improves sales conversion rates, and provides easily understood discount information for customers.

**Click to Copy:**
What is it: Click to Copy adds a one-click button that copies content, like a code snippet or link, to the clipboard.
How it works: Adds a button to click and copy content to clipboard, supporting various content types, custom success messages, and fallback options for unsupported browsers.
Benefits: Improves user experience for sharing codes or text, reduces friction in content sharing, and provides convenient functionality for reference materials.

**Web Share API:**
What is it: Web Share API adds a share button that uses the device's native sharing options, like a normal mobile app share sheet.
How it works: Adds OS based native sharing using the Web Share API, supporting modern browsers with fallback to custom sharing options for older browsers.
Benefits: Provides seamless sharing experience using device native sharing, improves mobile user experience, and increases content sharing rates.

**Animated Text:**
What is it: Animated Text styles your headings and text with animations like typewriter effects, fade-ins, and sliding text.
How it works: Adds multi-style text animations including typewriter effects, fade-ins, sliding text, and custom animation sequences with timing controls.
Benefits: Creates engaging text presentations, draws attention to important messages, and provides dynamic content experiences that improve user engagement.

**Wishlist Icon:**
What is it: Wishlist Icon adds an interactive heart-style toggle that lets customers save products to a wishlist.
How it works: Adds an interactive wishlist icon for adding/removing items with visual feedback, user authentication integration, and customizable styling options.
Benefits: Enables wishlist functionality for e-commerce sites, improves user experience for product saving, and provides valuable customer behavior insights.

**Lottie Animation:**
What is it: Lottie Animation displays lightweight Lottie JSON animations with scroll, hover, and click interactions.
How it works: Adds an advanced Lottie Animation element with scroll, hover, and click interactions, supporting JSON animation files with playback controls and trigger options.
Benefits: Provides high-quality animations with small file sizes, creates professional motion graphics, and enables interactive animations that enhance user experience.

**OpenStreetMap:**
What is it: OpenStreetMap adds an interactive map to your page powered by Leaflet and OpenStreetMap data, with no API key required.
How it works: Adds an interactive map element powered by Leaflet.js with markers, polylines, polygons, and various map controls supporting custom styling and data layers.
Benefits: Provides free mapping solution without API limitations, enables custom map styling and interactions, and offers privacy-focused alternative to Google Maps.

**Reviews Box:**
What is it: Reviews Box displays WooCommerce product reviews and ratings in a styled, responsive layout.
How it works: Adds a visually appealing WooCommerce product reviews and ratings display with custom styling, filtering options, and responsive design.
Benefits: Improves product page presentation, builds customer trust through social proof, and provides attractive review display that encourages customer feedback.

**Flipbox:**
What is it: Flipbox creates a card that flips in 3D on hover or click to reveal content on the other side.
How it works: Create engaging content with interactive 3D flip animations triggered by hover or click, supporting custom content on both sides with various flip directions.
Benefits: Creates memorable interactive experiences, enables creative content presentation, and provides engaging way to reveal additional information.

**Timeline:**
What is it: Timeline builds a visual, scrollable timeline for events, history, processes, and milestones.
How it works: Create interactive visual timelines to showcase events, history, processes, or milestones with customizable styling, responsive design, and content management.
Benefits: Presents chronological information clearly, improves storytelling and process explanation, and provides professional way to showcase company history or project progress.

**Classic Slideshow:**
What is it: Classic Slideshow creates responsive image slideshows with navigation dots, arrows, thumbnails, autoplay, and touch support.
How it works: Create responsive image slideshows with multiple navigation options (dots, arrows, fractions, line, thumbnails), autoplay, touch/swipe support, and smooth transitions.
Benefits: Showcases multiple images efficiently, provides professional presentation capabilities, and improves visual content engagement with interactive navigation.

**Frontend Post Submission:**
What is it: Frontend Post Submission adds a form to your site where visitors can submit posts with media uploads, without touching the admin.
How it works: Adds a comprehensive frontend post submission form with media uploads, taxonomy selection, content editor, user permissions, and advanced security features for user-generated content.
Benefits: Enables community-driven content creation, reduces admin workload, and provides secure way for users to contribute content without backend access.

**WooCommerce Buy Now:**
What is it: WooCommerce Buy Now adds a button that sends customers straight to checkout, skipping the cart entirely.
How it works: Adds a Buy Now button that skips the cart and goes directly to checkout. Supports simple products with configurable cart behavior, custom button styles, and flexible redirect options.
Benefits: Streamlines the purchase funnel for impulse buys and reduces cart abandonment.

#### Query Elements

**Comments Query:**
What is it: Comments Query displays post comments in a custom Bricks query loop with full control over filtering, sorting, and layout.
How it works: Create custom comment layouts in Bricks Builder with full control over filtering, sorting, and styling, including built-in AJAX load more functionality and support for nested comment replies.
Benefits: Provides complete design control over comment displays, improves comment section aesthetics, and enables custom comment functionality that matches site design.

**WooCommerce Reviews Query:**
What is it: WooCommerce Reviews Query displays product reviews in a query loop with rating filters and verified purchase badges.
How it works: Adds a WooCommerce Reviews Query element that displays product reviews in a Bricks query loop with support for rating filters, verified purchase badges, pagination, and custom layout designs.
Benefits: Provides complete design control over product review displays, enables custom review layouts with query loop flexibility, and supports advanced filtering for personalized review presentation.

**Product Gallery:**
What is it: Product Gallery is a query type for WooCommerce products that builds custom gallery layouts with dynamic product images.
How it works: Adds Product Gallery query type to container elements for WooCommerce products, enabling custom gallery layouts with dynamic product image loading.
Benefits: Provides complete control over product image presentation, enables custom gallery designs, and improves product page visual appeal.

**Menu Query:**
What is it: Menu Query lets you display WordPress menu items inside a Bricks query loop for custom navigation layouts.
How it works: Adds a dedicated Menu Query element that displays WordPress menu items in a query loop, supporting hierarchical navigation, custom styling, and dynamic content integration within Bricks Builder containers.
Benefits: Provides a complete menu query solution for advanced navigation layouts, enables custom menu designs with full query loop control, and supports complex multi-level navigation displays.

**Recently Viewed:**
What is it: Recently Viewed shows products the customer has browsed recently, creating a personalized shopping experience.
How it works: Adds Recently Viewed Products query type to container elements that tracks and displays user browsing history with customizable limits and styling.
Benefits: Improves user experience through personalized content, increases sales through relevant product suggestions, and provides valuable insights into user behavior.

**Wishlist Query:**
What is it: Wishlist Query displays the items a user has saved to their wishlist in a Bricks query loop.
How it works: Adds a Wishlist Query element that displays user wishlist items in a Bricks query loop, featuring product management options, user authentication integration, and comprehensive custom styling controls.
Benefits: Provides a dedicated query loop for wishlist content, enables advanced wishlist page designs with full layout control, and supports personalized shopping experiences with dynamic product displays.

#### Controls

**Element Tooltips:**
What is it: Element Tooltips adds customizable tooltips to any Bricks element, showing helpful info on hover.
How it works: Add customizable tooltips to any Bricks Builder element with position, style and animation options, supporting various trigger methods and content types.
Benefits: Provides additional information without cluttering interface, improves accessibility and user guidance, and enhances user experience through contextual help.

**Mini Cart: Quantity Controls:**
What is it: Mini Cart: Quantity Controls adds quantity inputs to WooCommerce mini cart items, updating totals without a page reload.
How it works: Adds quantity input controls and styling options to WooCommerce mini cart items with AJAX cart updates, custom styling, and validation features.
Benefits: Improves shopping cart functionality, enables quantity adjustments without page reload, and provides better user experience for cart management.

**Filter Radio: Image Support:**
What is it: Filter Radio: Image Support adds images to Bricks filter-radio elements, turning text filters into visual ones with multiple display modes.
How it works: Add image support to Bricks Builder filter-radio elements with multiple display modes (above/below/left/right text, background, image only), three image sources (meta fields, featured images, manual mapping), comprehensive styling controls (size, border radius, object fit, spacing), and hover effects (scale, opacity). Supports both regular and background image modes with overlay options.
Benefits: Creates visually appealing filter interfaces, improves user experience through visual filtering options, enables better product categorization and selection, and provides professional e-commerce filtering capabilities with custom styling and interaction effects.

**Add to Cart Swatches:**
What is it: Add to Cart Swatches adds swatch controls to the Bricks Add to Cart element, so product variations display as visual selectors while adding to cart.
How it works: Integrates swatch selection into the Bricks Add to Cart element, letting customers pick product variations from visual swatches and add the chosen item to the cart.
Benefits: Combines variation selection and checkout in one element, speeds up the purchase flow, and improves the product page experience.

**Read More/Less Buttons for Text Elements:**
What is it: Read More/Less Buttons for Text Elements truncates long text with expandable read more and read less controls.
How it works: Adds read more/less controls to text elements with character count, read more/less buttons, and responsive options for content truncation.
Benefits: Improves page layout by controlling text length, provides better mobile experience, and enables users to control content consumption.

**Read More/Less for Div:**
What is it: Read More/Less for Div adds collapsible text functionality to div and block elements, hiding content behind a button.
How it works: Adds collapsible text functionality to div and block elements with customizable height, separate read more/less buttons, and responsive options.
Benefits: Enables compact content presentation, improves page organization, and provides user control over content visibility.

**Tabs Nested: Persist Active State:**
What is it: Tabs Nested: Persist Active State remembers which tab was open and restores it after a page reload.
How it works: Adds a control to Tabs Nested element for keeping the active tab after page reload for better user experience through browser storage.
Benefits: Maintains user context across page reloads, improves navigation continuity, and provides better user experience for content browsing.

**Tabs Nested: Auto Switch:**
What is it: Tabs Nested: Auto Switch automatically cycles through tabs at a set interval, like a slideshow for tabbed content.
How it works: Adds a control to Tabs Nested element that automatically cycles through tabs at a configurable interval, creating an automatic slideshow effect for tabbed content.
Benefits: Creates engaging auto-rotating content displays without JavaScript coding, ensures all tab content gets visibility, and provides an automated presentation mode for dashboards and showcases.

**Slider Nested: Enable AutoScroll:**
What is it: Slider Nested: Enable AutoScroll adds continuous auto-scrolling to nested sliders with speed and direction controls.
How it works: Adds continuous scrolling capabilities to nested sliders with customizable speed, direction, and play/pause controls for automated content presentation.
Benefits: Creates engaging automated presentations, reduces manual interaction requirements, and provides modern slider functionality for content showcases.

**Slider Nested: Enable Slider Sync Extension:**
What is it: Slider Nested: Enable Slider Sync Extension synchronizes the movement between multiple sliders so they scroll together.
How it works: Creates synchronized movement between multiple sliders with configurable coordination patterns, enabling complex slider relationships and interactions.
Benefits: Enables advanced slider designs, creates professional presentation capabilities, and provides sophisticated content navigation options.

**Monks Cursor:**
What is it: Monks Cursor adds custom cursor effects to elements, with styles and hover feedback that give your site personality.
How it works: Adds custom mouse cursor effects to container, block, div and section elements with various cursor styles, hover effects, and interaction feedback.
Benefits: Creates unique user interface experiences, adds personality to site interactions, and provides visual feedback that enhances user engagement.

**Lazy Loading Controls:**
What is it: Lazy Loading Controls lets individual Bricks elements control their own lazy loading behavior for better performance.
How it works: Allow individual Bricks elements to control lazy loading behavior with custom thresholds, loading strategies, and performance optimization options.
Benefits: Improves page load performance, provides granular control over resource loading, and enables optimization of complex page layouts.

**Preloading Controls:**
What is it: Preloading Controls lets individual Bricks elements set their own preloading behavior, fetching key resources early for faster rendering.
How it works: Adds per-element preload settings to Bricks elements, letting you specify which images, scripts, or resources should be fetched before they are needed.
Benefits: Speeds up perceived page load, improves Core Web Vitals, and gives precise control over which assets load early.

#### Animations

**Animate On Scroll:**
What is it: Animate On Scroll triggers animations when elements scroll into view, adding smooth motion to your page.
How it works: Adds smooth scroll animations to elements with various animation types, trigger points, duration controls, and intersection observer optimization.
Benefits: Creates engaging visual experiences, improves content presentation, and provides modern animation effects that enhance user engagement.

**Parallax Scroll:**
What is it: Parallax Scroll adds depth by moving elements at different speeds as the page scrolls.
How it works: Adds smooth parallax scrolling to div, block, container & section elements with customizable speed, direction, and trigger conditions.
Benefits: Creates immersive visual experiences, adds depth to page designs, and provides modern scrolling effects that captivate users.

**Text Animation:**
What is it: Text Animation adds animation controls to headings and text elements so your words can fade, slide, or bounce in.
How it works: Adds animation controls to text, heading, text-basic, post-title, post-excerpt, post-content, post-taxonomy with various animation styles and timing options.
Benefits: Draws attention to important text content, creates engaging reading experiences, and provides professional text presentation capabilities.

**Block Tilt Effect:**
What is it: Block Tilt Effect adds a 3D tilt to elements that follows the mouse on hover.
How it works: Adds 3D tilt effect controls to div, block, container & section elements with mouse-following tilt, customizable intensity, and reset options.
Benefits: Creates interactive visual effects, adds modern design elements, and provides engaging hover interactions that enhance user experience.

### Dynamic Data

**Classic Monks Tags:**
What is it: Classic Monks Tags are dynamic tags you can insert in Bricks to show plugin values like remaining swatches, wishlist count, and recently viewed count.
How it works: Provides dynamic tags including `{cm_remaining_swatches}`, `{cm_wishlist_count}`, and `{cm_recently_viewed_count}` that pull live plugin data into any Bricks element.
Benefits: Adds plugin-powered dynamic content to your layouts, enables real-time personalization, and displays store activity without custom code.

**Menu Item Tags:**
What is it: Menu Item Tags are dynamic tags that output any property of a menu item, like its title, URL, classes, or parent.
How it works: Exposes dynamic tags for menu item properties including title, URL, target, classes, description, current state, children, ID, parent, and object type for use in Bricks queries and layouts.
Benefits: Makes menus fully customizable with dynamic data, enables advanced navigation designs, and gives complete control over menu item display.

**Product Gallery Tags:**
What is it: Product Gallery Tags output properties of WooCommerce product gallery images, like the URL, alt text, type, and position.
How it works: Provides dynamic tags for product gallery image data including image ID, URL, alt text, type, and position for use in custom gallery layouts.
Benefits: Powers custom product galleries with dynamic data, simplifies gallery building, and enables deeper product page customization.

**Comments Tags:**
What is it: Comments Tags let you pull comment content, author, and date into your Bricks layouts as dynamic values.
How it works: Provides dynamic tags for comment data including comment content, author, and date for use in custom comment layouts.
Benefits: Enables fully custom comment sections, powers rich comment displays, and gives design control over comment presentation.

**WooCommerce Reviews Tags:**
What is it: WooCommerce Reviews Tags output review content, rating stars, and verified purchase badges as dynamic values.
How it works: Provides dynamic tags for WooCommerce review data including review content, rating stars, and verified badge for custom review layouts.
Benefits: Powers customizable review displays, builds trust through verified purchase indicators, and enables design-matched review sections.

**WordPress Core Tags:**
What is it: WordPress Core Tags are a large set of dynamic tags for core site data, from the current year to word count and reading time.
How it works: Provides 30+ dynamic tags covering current year, parent title, post class, loop counter, author stats, comment/ping status, password protection, views, word count, reading time, visitor type, and more.
Benefits: Adds rich core WordPress data to any layout, enables personalized and contextual content, and reduces the need for custom code.

**Media Tags:**
What is it: Media Tags output properties of media files, like the image URL, title, alt text, caption, and description.
How it works: Provides dynamic tags for media file data including image HTML, ID, URL, title, alt, caption, and description for use in layouts.
Benefits: Powers custom media displays, simplifies image handling in designs, and gives full control over how media data appears.

**WooCommerce Tags:**
What is it: WooCommerce Tags are dynamic tags for store data like product type, stock, cart counter, totals, and customer stats.
How it works: Provides dynamic tags for WooCommerce data including product type, stock, cart counter, subtotals, shipping, sale dates, sales, reviews, ratings, customer stats, dimensions, weight, and download limits.
Benefits: Brings real store data into your layouts, enables custom shop designs, and powers personalized merchandising displays.

**Taxonomy Tags:**
What is it: Taxonomy Tags output properties of taxonomy terms, like depth, child count, and parent status, as dynamic values.
How it works: Provides dynamic tags for taxonomy term data including depth, children count, parent status, hierarchical, and public for use in Bricks layouts.
Benefits: Enables data-rich taxonomy displays, powers custom category and tag designs, and adds control over term presentation.

### Conditions

**WordPress Core Conditions:**
What is it: WordPress Core Conditions let you show or hide elements based on core site data like post views, word count, and author stats.
How it works: Provides visibility conditions based on post views, word count, reading time, update recency, images/links counts, author stats, comment/ping status, and password protection.
Benefits: Creates context-aware layouts, personalizes what visitors see, and enables content that adapts to the page.

**User Conditions:**
What is it: User Conditions show or hide elements based on who the visitor is, like whether they are new or returning.
How it works: Provides visibility conditions based on visitor type (new vs returning), registration age, and role level.
Benefits: Personalizes content by user type, improves conversion through targeted messaging, and tailors the experience to each visitor.

**Content Analysis Conditions:**
What is it: Content Analysis Conditions show or hide elements based on the structure of the page content, like heading count or media presence.
How it works: Provides visibility conditions based on content analysis including headings, paragraphs, lists, tables, external links, shortcodes, blocks, and media counts.
Benefits: Creates smart layouts that adapt to content, enables context-sensitive displays, and improves content-driven design decisions.

**Taxonomy Conditions:**
What is it: Taxonomy Conditions show or hide elements based on properties of a taxonomy term, like its depth or whether it is hierarchical.
How it works: Provides visibility conditions based on taxonomy data including depth, children, parent, hierarchy type, and public status.
Benefits: Creates term-aware layouts, powers customized category displays, and enables context-driven taxonomy content.

**Media Conditions:**
What is it: Media Conditions show or hide elements based on properties of attached media, like whether an image has a caption.
How it works: Provides visibility conditions based on media data including image HTML, ID, URL, title, alt, caption, and description.
Benefits: Makes layouts adapt to media presence, enables data-aware image displays, and gives finer control over media-driven content.

**WooCommerce Conditions:**
What is it: WooCommerce Conditions show or hide elements based on store data like cart contents, customer history, and order timing.
How it works: Provides visibility conditions based on cart weight/items/categories, product sales/reviews/gallery, customer orders/reviews/spending, order timing, shipping, tax, and dimensions.
Benefits: Personalizes shop pages by cart and customer state, enables smart merchandising displays, and powers conversion-focused layouts.

### Interactions

**21 Triggers:**
What is it: 21 Triggers is a full set of interaction triggers that fire actions at the right moment, from scroll direction to key presses and idle time.
How it works: Provides 21 triggers covering scroll direction, resize, tab active, double/right click, focus, theme change, checkbox, paste, network, print, key press, swipe, long press, idle, scroll progress, copy/cut, orientation, before unload, scroll stop, and fullscreen.
Benefits: Enables powerful interactive designs, gives fine-grained control over when actions fire, and supports complex interaction patterns without code.

**22 Actions:**
What is it: 22 Actions is a library of ready-made actions that run when a trigger fires, like copying content, playing media, or navigating pages.
How it works: Provides 22 actions including copy content, play/pause media, toggle mute, submit form, focus/disable element, navigate (back/forward/reload), print, remove element, toggle scroll, toggle class, animate number, download, toggle password/fullscreen, lazy load, and set cookie.
Benefits: Makes advanced interactions easy to build, reduces custom JavaScript requirements, and enables responsive, automated page behavior.

### Import/Export

**Export/Import Settings:**
What is it: Export/Import Settings backs up your Bricks components as JSON and restores them later with conflict resolution.
How it works: Exports selected Bricks components (including setup data) to a JSON file for backup or transfer, and imports them with conflict resolution for safe restoration.
Benefits: Protects your Bricks work with reliable backups, makes migrating builds between sites easy, and prevents data loss with import conflict handling.

**Reset Settings:**
What is it: Reset Settings lets you permanently delete selected Bricks components from the database for a clean slate.
How it works: Select specific Bricks components to permanently delete from the database.
Benefits: Enables targeted cleanup of Bricks data.

### Optimization

**Disable Bricks Assets:**
What is it: Disable Bricks Assets stops Bricks Builder's frontend CSS and JavaScript from loading on pages that do not use Bricks, trimming unused code.
How it works: Detects whether a page was built with Bricks and, when it was not, skips loading the builder's frontend CSS and JavaScript on that page.
Benefits: Makes non-Bricks pages load faster, reduces page weight, and improves performance for mixed-content sites.

**CSS Minification:**
What is it: CSS Minification compresses the CSS that Bricks outputs, removing whitespace and redundant characters to shrink file size.
How it works: Minifies the Bricks stylesheet by stripping unnecessary characters and optimizing the CSS output served to visitors.
Benefits: Reduces CSS file size, improves page load speed, and boosts performance scores on Bricks-built pages.

---

## Security Tab

### WP Protection

**Enable Custom Login URL:**
What is it: Custom Login URL replaces wp-login.php with a private address of your choosing, so bots and attackers cannot find your login page.
How it works: Creates a custom login URL to hide the default wp-login.php, redirecting unauthorized access attempts while maintaining secure access through the custom URL.
Benefits: Significantly reduces brute force attacks by obscuring the login page, improves overall site security, and eliminates automated login attempts targeting the default WordPress login URL.

**Enable Login Lockdown:**
What is it: Login Lockdown temporarily blocks an IP address after too many failed login attempts, stopping brute force attacks in their tracks.
How it works: Limits login attempts to prevent brute force attacks by tracking failed login attempts per IP address and temporarily blocking access after reaching the configured threshold.
Benefits: Prevents automated password cracking attempts, reduces server load from malicious login attempts, and provides immediate protection against credential stuffing attacks.

**Enable Extended Lockout:**
What is it: Extended Lockout applies a longer block, like 24 hours, to repeat offenders who keep trying to log in after a temporary lockout.
How it works: After multiple lockout periods, applies a longer block (e.g., 24 hours) for repeat offenders who continue attempting to login after being temporarily locked out.
Benefits: Escalates security for persistent attackers, reduces long-term attack effectiveness, and provides progressive deterrents against sustained brute force campaigns.

**Hide Username Validity:**
What is it: Hide Username Validity shows the same generic error for every failed login, so attackers cannot tell if a username exists.
How it works: Replaces specific WordPress error messages ("Invalid username" vs "Invalid password") with generic messages that don't reveal whether a username exists in the system.
Benefits: Prevents username enumeration through error message analysis, removes information attackers use to identify valid accounts, and strengthens authentication security.

**Hide Login Form During Lockout:**
What is it: Hide Login Form During Lockout completely removes the login form when an IP is blocked, leaving nothing to attack.
How it works: Completely hides the login form when an IP address is blocked during a lockout period, preventing any further login attempts.
Benefits: Eliminates lockout bypass attempts, prevents attackers from testing additional credentials, and provides clear visual indication that access is blocked.

**Enable Activity Logging:**
What is it: Activity Logging records every login attempt, successful or failed, with IP and time details, in the Classic Monks Logs section.
How it works: Logs all login attempts (successful and failed) with IP addresses, timestamps, and attempt details. Adds a Login Lockdown tab to Classic Monks > Logs submenu.
Benefits: Provides audit trail for security analysis, enables proactive identification of attack patterns, and assists in forensic investigation of unauthorized access attempts.

**Enable Cloudflare Turnstile:**
What is it: Cloudflare Turnstile adds a privacy-friendly, invisible-style CAPTCHA to your forms that blocks bots without annoying real users.
How it works: Enables Cloudflare Turnstile CAPTCHA on forms to prevent spam and automated submissions, supporting WordPress login forms, WooCommerce forms, and comment forms with privacy-focused verification.
Benefits: Blocks bot submissions effectively, provides better user experience than traditional CAPTCHAs, and offers privacy-focused spam protection without compromising user data.

**Turnstile: WordPress Login Forms:**
What is it: Turnstile on WordPress Login Forms adds Cloudflare Turnstile protection to the login, registration, and password reset forms.
How it works: Applies Cloudflare Turnstile verification to WordPress login, registration, and password reset forms, blocking automated attempts against authentication forms.
Benefits: Stops bots from attacking login and registration forms, keeps password reset flows spam-free, and protects account takeovers with a human check.

**Turnstile: WooCommerce Forms:**
What is it: Turnstile on WooCommerce Forms adds Cloudflare Turnstile protection to store login, registration, and checkout forms.
How it works: Applies Cloudflare Turnstile verification to WooCommerce login, registration, and checkout forms, preventing automated spam and fake orders.
Benefits: Blocks fake accounts and bot checkout attempts, reduces spam orders, and protects store forms with a human verification check.

**Turnstile: Comment Forms:**
What is it: Turnstile on Comment Forms adds Cloudflare Turnstile to your comment forms, keeping spam bots out of your comment sections.
How it works: Applies Cloudflare Turnstile verification to WordPress comment forms, blocking automated spam comments before they are submitted.
Benefits: Cuts comment spam dramatically, reduces moderation workload, and keeps your discussion sections clean without annoying commenters.

**Turnstile: Frontend Post Submission:**
What is it: Turnstile on Frontend Post Submission protects user-submitted content forms with Cloudflare Turnstile.
How it works: Applies Cloudflare Turnstile verification to frontend post submission forms, stopping bots from flooding user-generated content with spam.
Benefits: Keeps user submissions legitimate, reduces spam content in queues, and protects community features from automated abuse.

**Enable Math Captcha:**
What is it: Math Captcha protects your forms by asking visitors to solve a simple arithmetic question, proving they are human.
How it works: Protects forms with a math-based captcha system that presents simple arithmetic problems to verify human users before form submission.
Benefits: Provides effective bot protection with simple user interaction, maintains accessibility for users with disabilities, and offers lightweight spam protection without external dependencies.

**Math Captcha: WordPress Login Forms:**
What is it: Math Captcha on WordPress Login Forms adds a simple math question to the login, registration, and password reset forms.
How it works: Applies a math captcha to WordPress login, registration, and password reset forms, requiring a correct answer before submission.
Benefits: Blocks automated attacks on authentication forms, stops bot registrations, and keeps login flows human-only with a lightweight challenge.

**Math Captcha: WooCommerce Forms:**
What is it: Math Captcha on WooCommerce Forms adds a math challenge to store login, registration, and checkout forms.
How it works: Applies a math captcha to WooCommerce login, registration, and checkout forms, preventing automated submissions and fake orders.
Benefits: Prevents bot-driven store abuse, reduces spam registrations and orders, and protects WooCommerce forms with a simple human check.

**Math Captcha: Comment Forms:**
What is it: Math Captcha on Comment Forms adds a math question to comment forms to stop spam comments.
How it works: Applies a math captcha to WordPress comment forms, requiring visitors to solve a simple problem before their comment is accepted.
Benefits: Slashes comment spam, lowers moderation effort, and keeps discussions spam-free with a lightweight human check.

**Math Captcha: Frontend Post Submission:**
What is it: Math Captcha on Frontend Post Submission adds a math challenge to user submission forms.
How it works: Applies a math captcha to frontend post submission forms, blocking bots from submitting spam user-generated content.
Benefits: Keeps user content submissions authentic, reduces spam in content queues, and protects community features from automation.

**Hide Remember Me Checkbox:**
What is it: Hide Remember Me Checkbox removes the "Remember Me" option from the login page, so sessions end when the browser closes.
How it works: Removes the "Remember Me" checkbox from the login page to force users to authenticate for each session, improving security for shared computers.
Benefits: Enhances security on shared devices, prevents accidental persistent logins, and reduces security risks from abandoned browser sessions.

**Enable Auto Logout:**
What is it: Auto Logout signs inactive users out after a set time, protecting accounts from abandoned sessions.
How it works: Automatically logs out inactive users after a specified time period, monitoring user activity and terminating sessions to prevent unauthorized access.
Benefits: Prevents unauthorized access from abandoned sessions, improves security compliance, and reduces server resource usage from idle sessions.

**Disable User Enumeration:**
What is it: Disable User Enumeration stops attackers from discovering valid usernames through author archives, API endpoints, and login errors.
How it works: Prevents user enumeration attacks by blocking requests that attempt to discover usernames through author archives, REST API user endpoints, and login error messages.
Benefits: Protects user privacy by preventing username discovery, reduces reconnaissance opportunities for attackers, and maintains user anonymity.

**Email & Phone Protection:**
What is it: Email & Phone Protection hides email addresses and phone numbers from spam bots by obfuscating them on your pages.
How it works: Protects email addresses and phone numbers from spam bots and harvesters through multiple obfuscation methods including content filters and full-page protection. Supports protection scope selection for targeted or comprehensive coverage.
Benefits: Prevents email harvesting for spam, protects phone numbers from scrapers, reduces unwanted communications, and maintains usability for legitimate visitors.

**Disable .htaccess File Access:**
What is it: Disable .htaccess File Access blocks direct browser access to your .htaccess file, returning a 403 error.
How it works: Prevents direct access to .htaccess files through HTTP requests by adding server-level restrictions that return 403 Forbidden errors for .htaccess access attempts.
Benefits: Protects server configuration from exposure, prevents sensitive rule disclosure, and blocks potential security reconnaissance attempts.

**Disable all changes to all files via admin area:**
What is it: This feature removes file editing from the admin area, blocking theme editor, plugin editor, and file management to stop code tampering.
How it works: Removes file editing capabilities from the WordPress admin area, including theme editor, plugin editor, and file management functions to prevent unauthorized code modifications.
Benefits: Prevents malicious code injection through admin interface, protects against privilege escalation attacks, and maintains code integrity by forcing changes through secure methods.

**Disable file changes via plugin and theme editors:**
What is it: Disable file changes via plugin and theme editors turns off the built-in code editors in WordPress so theme and plugin files cannot be modified from the dashboard.
How it works: Specifically disables the built-in WordPress theme and plugin editors that allow direct code modification through the admin interface.
Benefits: Prevents unauthorized code modifications, reduces attack surface for compromised admin accounts, and forces secure development practices through proper file system access.

**Disable XML-RPC:**
What is it: Disable XML-RPC turns off the XML-RPC system, removing a common vector for brute force, pingback, and DDoS attacks.
How it works: Completely disables the XML-RPC functionality in WordPress, which is often targeted for brute force attacks, DOS attacks, and pingback abuse.
Benefits: Eliminates a major attack vector for brute force attempts, prevents pingback spam and DDOS attacks, and reduces server resource consumption from malicious XML-RPC requests.

**Remove REST API Links:**
What is it: Remove REST API Links strips REST API discovery links from the page head and HTTP headers to reduce exposure.
How it works: Removes REST API discovery links from the HTML head and HTTP headers while optionally restricting API access for non-authenticated users.
Benefits: Reduces API endpoint discovery by attackers, provides granular access control over REST API functionality, and maintains API functionality while improving security through obscurity.

**REST API Access:**
What is it: REST API Access controls who can use the WordPress REST API, from full access to admins-only or logged-in users only.
How it works: Configures REST API access levels with options for default access, restricting to admins only, logged-in users only, or complete disabling of REST API access.
Benefits: Provides granular control over API access, prevents unauthorized data access, and enables secure API usage while blocking malicious requests.

**REST API Exclusions:**
What is it: REST API Exclusions whitelists specific API namespaces, so essential plugins keep working even when the REST API is restricted.
How it works: When REST API access is restricted, you can whitelist specific API namespaces to keep them accessible. Includes registered namespaces from plugins (Bricks, WooCommerce, Contact Form 7, etc.) and custom namespace patterns.
Benefits: Maintains compatibility with essential plugins while enforcing API restrictions.

### Two-Factor Authentication

**Enable Authenticator App (TOTP):**
What is it: Authenticator App (TOTP) lets users secure their accounts with a time-based one-time password from apps like Google Authenticator or Authy.
How it works: Allows users to set up two-factor authentication using authenticator apps like Google Authenticator, Authy, or Microsoft Authenticator, generating time-based one-time passwords for enhanced login security.
Benefits: Significantly improves account security, prevents unauthorized access even with compromised passwords, and provides industry-standard 2FA protection that users are familiar with.

**Enable Email OTP:**
What is it: Email OTP sends a one-time password to the user's email at login, adding a second verification step without needing an app.
How it works: Sends one-time passwords via email when users log in, providing an additional authentication layer that requires access to the user's email account.
Benefits: Provides accessible 2FA for users without smartphone apps, ensures email account control verification, and offers backup authentication method for enhanced security.

**Allow Trusted Devices:**
What is it: Allow Trusted Devices lets users mark a device as trusted and skip the 2FA prompt on it for a set period.
How it works: Enables users to mark devices as trusted for a configurable period, reducing 2FA prompts on frequently used devices while maintaining security for new or untrusted devices.
Benefits: Balances security with user convenience, reduces authentication fatigue, and maintains protection while improving user experience on trusted devices.

**Enable 2FA Rate Limiting:**
What is it: 2FA Rate Limiting blocks brute force attempts against the second verification step by limiting failed 2FA tries.
How it works: Limits repeated failed two-factor authentication verification attempts within a time window, blocking brute force attacks on the second authentication factor.
Benefits: Prevents brute force attacks on 2FA codes, protects against credential stuffing on the second factor, and adds another security layer beyond password protection.

### Content Protection

**Enable Site-Wide Password Protection:**
What is it: Site-Wide Password Protection puts your entire site behind a single password, perfect for development and maintenance phases.
How it works: Protects the entire website with a site-wide password requirement, blocking all access until the correct password is entered, with optional IP address bypass functionality.
Benefits: Provides immediate site protection during development or maintenance, enables temporary access control, and offers simple but effective protection for sensitive content or work-in-progress sites.

**Block AI Crawlers:**
What is it: Block AI Crawlers stops AI training bots like GPTBot, Claude, and others from scraping your content.
How it works: Identifies and blocks known AI crawlers and scraping bots from accessing website content, using user agent detection and behavior analysis to prevent unauthorized content harvesting.
Benefits: Protects intellectual property from AI training datasets, prevents unauthorized content scraping, and maintains control over content usage while allowing legitimate search engine access.

**Enable Spam Comment/Review Protection:**
What is it: Spam Comment/Review Protection makes it much harder for bots to submit spam by hiding form targets behind JavaScript.
How it works: Prevents bots from submitting spam comments and product reviews by hiding form action URLs and dynamically adding them through JavaScript, making automated submissions significantly more difficult.
Benefits: Dramatically reduces spam submissions, improves content quality, and reduces moderation workload while maintaining accessibility for legitimate users.

**Disable Text Selection:**
What is it: Disable Text Selection prevents visitors from selecting and copying text on your site, with options to apply it site-wide or per post type.
How it works: Prevents visitors from selecting and copying text content on the website using CSS and JavaScript techniques, with options for site-wide application or specific post types.
Benefits: Protects written content from easy copying, discourages content theft, and provides basic intellectual property protection while maintaining readability.

**Restrict Editor Access to Specific Posts:**
What is it: Restrict Editor Access to Specific Posts lets administrators block editors from accessing particular posts.
How it works: Allows administrators to prevent editors from accessing specific posts by modifying post capabilities and admin queries, providing granular content access control.
Benefits: Enables content access management beyond role-based permissions, protects sensitive content from unauthorized editing, and provides flexible content security for multi-author sites.

**Disable Right Click:**
What is it: Disable Right Click blocks the right-click context menu on your site, deterring casual copying.
How it works: Prevents users from accessing the right-click context menu using JavaScript event handlers, blocking common methods for accessing developer tools and copy functions.
Benefits: Provides basic content protection against casual copying attempts, deters non-technical users from accessing browser tools, and adds a layer of content security.

**Disable View Source (CTRL+U/CMD+U):**
What is it: Disable View Source blocks the view source keyboard shortcut so visitors cannot peek at your page code.
How it works: Intercepts the view source keyboard shortcut (Ctrl+U on Windows, Cmd+U on Mac) and prevents the browser from opening the page source.
Benefits: Deters casual code inspection, adds a layer of source protection, and discourages visitors from examining your frontend code.

**Disable Inspect Element (F12 or CTRL+Shift+I/CMD+OPT+I):**
What is it: Disable Inspect Element blocks the developer tools shortcuts, keeping visitors from inspecting your page code.
How it works: Intercepts the inspect element keyboard shortcuts (F12, Ctrl+Shift+I, Cmd+Opt+I) and prevents developer tools from opening.
Benefits: Deters code inspection and casual scraping, protects frontend markup from easy viewing, and discourages tampering with page elements.

**Disable Copy/Cut/Paste (CTRL+C/X/V / CMD+C/X/V):**
What is it: Disable Copy/Cut/Paste blocks the keyboard shortcuts used for copying, cutting, and pasting on your site.
How it works: Intercepts the copy, cut, and paste keyboard shortcuts (Ctrl+C/X/V, Cmd+C/X/V) and prevents them from working.
Benefits: Protects text content from casual copying, discourages content theft, and keeps page content from being easily duplicated.

**Disable Select All (CTRL+A/CMD+A):**
What is it: Disable Select All blocks the select all shortcut so visitors cannot quickly highlight all the text on a page.
How it works: Intercepts the select all keyboard shortcut (Ctrl+A, Cmd+A) and prevents the browser from selecting all content.
Benefits: Adds another barrier to copying full page content, discourages bulk copying, and helps protect large blocks of text.

**Disable Save (CTRL+S/CMD+S):**
What is it: Disable Save blocks the save page shortcut to discourage visitors from saving your page locally.
How it works: Intercepts the save keyboard shortcut (Ctrl+S, Cmd+S) and prevents the browser's save action on your pages.
Benefits: Deters visitors from saving pages for offline use, protects page content, and adds a layer of content security.

**Disable Print (CTRL+P/CMD+P):**
What is it: Disable Print blocks the print shortcut so visitors cannot easily print your page content.
How it works: Intercepts the print keyboard shortcut (Ctrl+P, Cmd+P) and prevents the browser print dialog from opening.
Benefits: Deters printing of your content, protects written material from physical copies, and adds another layer of content protection.

**Disable Text Selection (Mouse Selection):**
What is it: Disable Text Selection (Mouse Selection) makes it impossible to highlight text by dragging the mouse.
How it works: Prevents text selection using mouse dragging through CSS user-select properties and JavaScript event handling, making text highlighting impossible.
Benefits: Provides comprehensive text protection against copying, prevents easy content selection, and discourages casual content theft while maintaining readability.

**Disable Image Drag (Mouse Drag):**
What is it: Disable Image Drag (Mouse Drag) prevents visitors from dragging images to save them to their computer.
How it works: Prevents images from being dragged and saved using CSS and JavaScript techniques, blocking the common drag-to-desktop image saving method.
Benefits: Protects images from easy downloading, prevents casual image theft, and maintains visual content security while preserving display functionality.

**Disable Safari Reader Mode (CMD+Shift+R):**
What is it: Disable Safari Reader Mode stops Safari's Reader Mode from loading your content in clean, copyable form.
How it works: Intercepts the Safari Reader Mode shortcut (Cmd+Shift+R) and prevents Reader Mode from activating on your pages.
Benefits: Prevents clean-format copying of articles, keeps styling and branding visible, and protects written content from easy extraction.

**Apply to Administrators:**
What is it: Apply to Administrators extends all content protection measures to admins and editors too, leaving no role exempt.
How it works: Also applies text selection restrictions to administrators and editors, ensuring consistent protection regardless of user role.
Benefits: Provides comprehensive security coverage, prevents privilege-based bypasses, and ensures consistent content protection across all user types.

### Stay Logged In

**Enable Stay Logged In:**
What is it: Stay Logged In extends WordPress login sessions to a full year, so users are not logged out constantly.
How it works: Extends WordPress login sessions to one year duration, modifying the default session timeout to provide persistent login functionality for improved user convenience.
Benefits: Eliminates frequent re-authentication requirements, improves user experience for trusted devices, and provides convenience while maintaining security through other protection measures.

**Auto-check "Remember Me" on Login Page:**
What is it: Auto-check "Remember Me" on Login Page ticks the Remember Me box automatically so users stay logged in by default.
How it works: Automatically checks the Remember Me checkbox on the WordPress login page, so login sessions persist by default when a user signs in.
Benefits: Reduces repeat logins for returning users, improves convenience on trusted devices, and pairs with Stay Logged In for persistent sessions.

### Staging Protection

**Enable Staging Protection:**
What is it: Staging Protection locks down your staging or development site so the public and search engines cannot see unfinished work.
How it works: Protects staging and development sites from public access by requiring authentication, with multiple protection methods including password protection, HTTP authentication, and URL token-based access.
Benefits: Prevents search engine indexing of development sites, protects unfinished content from public view, and enables secure client review without exposing work-in-progress.

**Generate Temporary Access Token:**
What is it: Generate Temporary Access Token creates time-limited tokens that expire automatically, great for temporary client reviews.
How it works: Creates time-limited access tokens that expire after a set period, allowing temporary access for client reviews or testing without permanent bypass.
Benefits: Enables time-limited client access, provides secure temporary access for reviews, and automatically revokes access after the review period.

**Enable HTTP Authentication:**
What is it: Enable HTTP Authentication adds a browser-level password check that blocks strangers before WordPress even loads.
How it works: Adds HTTP Basic Authentication as an additional security layer on top of password protection, requiring proper credentials before WordPress even loads.
Benefits: Provides a server-level authentication layer, prevents WordPress from loading for unauthorized users, and adds defense-in-depth for staging environments.

**Allow Performance Testing Tools:**
What is it: Allow Performance Testing Tools whitelists PageSpeed, GTmetrix, and similar services so they can test your protected staging site.
How it works: Auto-whitelists known performance testing services like Google PageSpeed Insights, GTmetrix, and Pingdom, allowing them to bypass staging protection to run performance audits.
Benefits: Enables performance monitoring of staging sites, allows automated page speed testing, and maintains protection while permitting legitimate testing services.

**Allow Development Endpoints:**
What is it: Allow Development Endpoints lets API clients, webhooks, and CI/CD systems reach your staging site for integration testing.
How it works: Auto-whitelists API clients, CI/CD systems, and webhook endpoints that need to access the staging site for integration and testing purposes.
Benefits: Enables continuous integration workflows, permits automated testing tools access, and supports development tool integration without compromising security.

**IP Whitelist:**
What is it: IP Whitelist lets you specify trusted IPs that bypass staging protection, like your own or your client's.
How it works: Specifies IP addresses (CIDR-compatible) that bypass staging protection, allowing trusted IPs like developers, clients, and testing services to access the site without authentication.
Benefits: Enables seamless developer access, allows trusted testing tools to bypass protection, and provides convenient access for authorized stakeholders.

**Only Protect URL Pattern:**
What is it: Only Protect URL Pattern restricts staging protection to specific URLs, leaving other parts of the site public.
How it works: Restricts staging protection to specific URL patterns, leaving other site areas publicly accessible while protecting sensitive sections.
Benefits: Enables selective protection of development areas, allows public access to stable content, and provides flexible protection for staged rollouts.

**Show Staging Environment Indicator:**
What is it: Show Staging Environment Indicator displays a banner that clearly marks the site as staging, preventing mix-ups with production.
How it works: Displays a visible banner or indicator showing the current site is a staging environment, preventing confusion between development and production sites.
Benefits: Prevents accidental content creation on staging sites, provides clear visual distinction between environments, and reduces errors from working on wrong sites.

---

## Interface Tab

### Folders

**Enable Folder Manager:**
What is it: Folder Manager organizes your Media Library and post types into folders with a drag-and-drop sidebar, folder colors, and quick filtering.
How it works: Organizes your Media Library and post types into folders with a sidebar folder tree for drag-and-drop organization, folder colors, and quick filtering. Adds a dedicated submenu under Classic Monks.
Benefits: Dramatically improves media and content organization, provides visual folder structure for quick navigation, and enables efficient management of large libraries.

**Multiple Folders Per Item:**
What is it: Multiple Folders Per Item lets you assign a single media item or post to more than one folder.
How it works: Allows assigning a single media item or post to multiple folders instead of limiting it to one.
Benefits: Enables flexible content categorization, supports cross-referenced organization, and eliminates the need to duplicate items for multiple categories.

**Uncategorized Removes from All Folders:**
What is it: Uncategorized Removes from All Folders clears every folder assignment when you drag an item into "Uncategorized".
How it works: Dragging an item into the "Uncategorized" category removes all existing folder assignments for that item.
Benefits: Provides quick way to reset folder assignments, enables batch un-categorization, and simplifies content reorganization.

**Show in 'Add New' Media Screen:**
What is it: Show in 'Add New' Media Screen adds a folder dropdown to the Media > Add New screen so uploads land in the right folder automatically.
How it works: Adds a folder selection dropdown to the Media > Add New screen. The selected folder persists for future uploads, automatically assigning files to your saved folder preference.
Benefits: Streamlines upload workflow with automatic folder assignment, eliminates manual categorization after upload, and saves time for bulk uploads.

**Default Open Folder:**
What is it: Default Open Folder sets which folder is selected when you first open the media library, like All Files or the last one you used.
How it works: Configures which folder is selected by default when opening the media library, with options for All Files, Uncategorized, or Last Opened.
Benefits: Provides consistent starting point for media management, reduces navigation time, and matches user workflow preferences.

**Folder Download (ZIP):**
What is it: Folder Download (ZIP) adds a "Download ZIP" option to folders so you can grab a whole folder and its contents as one file.
How it works: Adds a "Download ZIP" option to the folder context menu, allowing you to download a folder and its contents as a ZIP file.
Benefits: Enables easy folder backup and sharing, simplifies bulk content export, and provides offline access to organized media.

**Folder Duplication:**
What is it: Folder Duplication adds a "Duplicate" option that copies a folder's structure, not the files inside, for quick setup of similar layouts.
How it works: Adds a "Duplicate" option to the folder context menu that duplicates the folder structure (not the files inside).
Benefits: Speeds up folder setup for similar content structures, provides template folder creation, and reduces manual organization effort.

**Gallery Shortcode:**
What is it: Gallery Shortcode lets you display images from a specific folder on the frontend using a shortcode.
How it works: Enables the [cm_foldermanager_gallery] shortcode to display images from a specific folder. Right-click any folder to access the Gallery Builder with options for columns, size, lightbox, captions, and more.
Benefits: Creates dynamic galleries from folder contents, provides frontend display of organized media, and offers customizable gallery layouts.

**Quick Inspect:**
What is it: Quick Inspect adds an "Inspect" toggle that shows which folders an item belongs to when you hover over it.
How it works: Adds an "Inspect" toggle to the sidebar. When active, hovering over an item shows which folders it belongs to.
Benefits: Provides quick folder membership visibility, eliminates need to open items for folder info, and streamlines content organization workflows.

**Display Mode:**
What is it: Display Mode controls which post types can use folder organization, like only selected types or all but selected types.
How it works: Configures which post types are eligible for folder organization, "Enable only on selected", "Enable except on selected", or "Enable on all post types".
Benefits: Provides flexible folder assignment scoping and allows excluding certain post types from the folder system.

**Post Type Selection:**
What is it: Post Type Selection lets you choose exactly which post types, like pages, posts, or products, get folder organization.
How it works: Select individual post types (pages, posts, products, etc.) to enable folder organization, with per-post-type toggles.
Benefits: Enables folder management only for relevant content types and keeps the folder interface focused on needed post types.

**Show in Admin Menu:**
What is it: Show in Admin Menu adds a folder management link to the admin sidebar for easy access.
How it works: For post types without native category support, adds a folder management link to the admin menu for quick access.
Benefits: Provides convenient folder access directly from the admin sidebar and eliminates navigation to other screens.

**Use Default Category:**
What is it: Use Default Category connects your folders to the native WordPress category system for posts and products.
How it works: For posts and products, integrates folders with the native WordPress Category or Product Category taxonomy.
Benefits: Keeps folder organization aligned with existing content workflows and reduces taxonomy duplication.

### Menu

**Admin Menu Manager:**
What is it: Admin Menu Manager gives you one place to rearrange, hide, rename, and reorder every item in the admin sidebar and top toolbar.
How it works: Replaces individual toolbar and menu managers with a unified interface for customizing both the WordPress admin sidebar menu and the top admin toolbar. Supports SVG and custom icon overrides for any menu item, menu spacers to add visual separators between items, inline menu-title editing directly in the menu, role and per-user visibility controls to show or hide items, and custom toolbar placement for adding branded items to the admin bar.
Benefits: Provides complete control over the entire admin navigation experience from a single interface, enables white-label customization with custom icons and branded toolbar items, streamlines admin interfaces for client sites by hiding unnecessary entries, and adds visual organization through menu spacers and direct title editing.

**Top Toolbar Manager:**
What is it: Top Toolbar Manager lets you rearrange, hide, and control what shows in the admin top bar.
How it works: Rearrange, hide, and control visibility of admin top bar menu items. Supports role-based visibility and custom toolbar placement.
Benefits: Provides granular control over the admin toolbar, streamlines the top navigation for different user roles, and creates a cleaner admin experience by removing unnecessary toolbar items.

**Alphabetical Menu Sorting:**
What is it: Alphabetical Menu Sorting rearranges your admin menu into alphabetical order, with core items first, for easier navigation.
How it works: Sorts the main WordPress admin menu items alphabetically with a single toggle, reorganizing all top-level menu entries in A-Z order regardless of their original registration order. Core items stay first, then plugin/theme items A-Z. Also sorts Settings, Appearance, Tools, and Dashboard submenus alphabetically.
Benefits: Eliminates the need to hunt for menu items in non-alphabetical plugin-determined order, provides consistent menu navigation across all admin users, and reduces cognitive load when finding specific settings pages.

**Wider Admin Sidebar:**
What is it: Wider Admin Sidebar sets a custom width for the admin sidebar so longer menu labels fit without truncating.
How it works: Sets a wider WordPress admin navigation sidebar using a custom width value in pixels, providing more space for longer menu labels that would otherwise truncate or wrap awkwardly.
Benefits: Prevents menu label truncation for plugins with long names, improves readability of the admin navigation, and creates a more professional admin interface without CSS overrides.

**Quick Post Nav:**
What is it: Quick Post Nav adds shortcuts in the admin bar that jump straight to your post types, pages, and posts.
How it works: Adds quick navigation menus in the admin bar for post types, pages, and posts, providing fast access to content management.
Benefits: Speeds up content management workflow, provides quick access to frequently edited content, and improves admin navigation efficiency.

**Move Admin Bar to Bottom:**
What is it: Move Admin Bar to Bottom places the WordPress admin bar at the bottom of the screen instead of the top.
How it works: Moves the WordPress admin bar to the bottom of the screen instead of the default top position.
Benefits: Provides more screen space for content editing, reduces visual clutter at the top, and offers alternative admin bar placement for improved workflow.

### Admin Notices

**Admin Notices Manager:**
What is it: Admin Notices Manager gives you one modal where you can dismiss and manage all the admin notices that clutter your dashboard.
How it works: Collects all active admin notices into a single management modal where you can dismiss, snooze, or hide them instead of leaving them scattered across admin pages.
Benefits: Declutters the admin interface, removes distracting notice banners, and gives you control over which notifications stay visible.

### Form Desk

**Form Desk:**
What is it: Form Desk is a single place to manage form submissions with list and kanban views, status tracking, email replies, and internal notes.
How it works: Provides a comprehensive form submission management system with list and kanban views, status tracking, email reply capabilities, and internal notes. Supports submissions from Bricks Builder forms and Fluent Forms with search, filter, and bulk actions.
Benefits: Centralizes form submission management in one interface, enables efficient workflow with visual kanban boards, streamlines customer communication with inline email replies, and provides complete submission tracking with status management.

### Preloader

**Enable Preloader:**
What is it: Enable Preloader shows a loading animation before your page finishes loading, making the wait feel shorter.
How it works: Adds a preloader or loading animation that displays before the page loads completely, creating a buffer between navigation and content display to improve perceived performance and user experience.
Benefits: Improves perceived loading times, provides professional user experience, masks slow loading content, and gives users visual feedback that the page is loading.

**Disable Preloader inside Bricks Builder:**
What is it: Disable Preloader inside Bricks Builder turns the preloader off while you are editing in Bricks, so it does not get in the way.
How it works: Automatically detects when users are working within the Bricks Builder interface and disables the preloader to prevent interference with the editing experience.
Benefits: Improves builder workflow efficiency, prevents editing interruptions, and ensures smooth development experience while maintaining preloader functionality for site visitors.

### Laser Loader

**Enable Laser Loader:**
What is it: Enable Laser Loader adds a smooth progress bar, like the ones on YouTube and Medium, that shows how far your page has loaded.
How it works: Adds a smooth loading progress bar at the top or bottom of the page similar to YouTube and Medium, providing real-time visual feedback about page loading progress.
Benefits: Provides modern, professional loading experience, gives users real-time progress feedback, and improves perceived performance with familiar loading patterns.

**Disable Laser Loader inside Bricks Builder:**
What is it: Disable Laser Loader inside Bricks Builder keeps the laser loader off while you edit in Bricks.
How it works: Automatically detects the Bricks Builder editing environment and disables the laser loader to prevent interference with the builder interface and editing workflow.
Benefits: Maintains clean builder experience, prevents editing workflow interruptions, and ensures the loader only appears for site visitors without affecting development work.

### Experience

**Page Transitions:**
What is it: Page Transitions adds smooth fade transitions between pages as visitors navigate, giving your site a polished, app-like feel.
How it works: Applies smooth fade transitions between page navigations using the CSS View Transitions API with a JavaScript fallback for broader browser support.
Benefits: Makes navigation feel smooth and modern, improves perceived site quality, and adds a professional, seamless browsing experience.

**Shared Element Transitions:**
What is it: Shared Element Transitions animates specific elements, like a header or post title, so they flow naturally between pages during navigation.
How it works: Animates specific shared elements (header, content, post title/thumbnail) between pages so they transition smoothly instead of appearing abruptly on each new page.
Benefits: Creates a connected, continuous browsing feel, draws attention to key content, and makes multi-page navigation feel intentional.

**Reduced Motion Support:**
What is it: Reduced Motion Support respects users who prefer less animation, disabling transitions for those who are sensitive to motion.
How it works: Respects the user's system-level reduced motion preference (prefers-reduced-motion) by disabling or simplifying page transitions and animations for users who have indicated sensitivity to motion effects.
Benefits: Improves accessibility for users with vestibular disorders and motion sensitivity, complies with WCAG accessibility guidelines, and provides a comfortable browsing experience for all users.

**Admin Transitions:**
What is it: Admin Transitions extends the smooth page transition effect into the WordPress admin area.
How it works: Extends page transition effects to the WordPress admin interface, applying smooth navigation transitions between admin pages for a more polished administration experience.
Benefits: Provides visual continuity in the admin area, improves perceived performance of admin navigation, and creates a more modern, polished admin interface.

---

## White Label Tab

### Branding

**Customize Admin Bar Greeting:**
What is it: Customize Admin Bar Greeting replaces the default "Howdy" text in the admin bar with your own greeting.
How it works: Replaces the default "Howdy" greeting in the admin bar with custom text that matches your brand voice or professional requirements.
Benefits: Creates more professional admin experience, maintains brand consistency, and provides personalized user experience that aligns with company culture.

**Customize Admin Footer:**
What is it: Customize Admin Footer swaps the default WordPress footer text in the admin for your own branding or copyright.
How it works: Replaces the default WordPress footer text in the admin area with custom branding, copyright information, or company details.
Benefits: Reinforces brand presence throughout admin experience, provides consistent professional appearance, and allows client-facing customization for agency use.

**Replace WordPress Admin Bar Logo:**
What is it: Replace WordPress Admin Bar Logo swaps the WordPress logo in the admin bar for your own image.
How it works: Replaces the WordPress logo in the admin bar with a custom image, allowing complete branding of the admin interface header.
Benefits: Provides complete visual branding of admin interface, removes WordPress branding for white-label solutions, and creates professional client-facing admin experience.

**Remove Dashboard Widgets:**
What is it: Remove Dashboard Widgets removes the default WordPress widgets, like news, quick draft, and activity, from the dashboard.
How it works: Removes default WordPress dashboard widgets including news, quick draft, and activity widgets to create cleaner admin experience.
Benefits: Reduces dashboard clutter, improves focus on custom content, speeds up dashboard loading, and provides cleaner interface for client-facing admin areas.

**Remove WordPress Footer Text and Version:**
What is it: Remove WordPress Footer Text and Version hides the WordPress version number and "Thank you for creating with WordPress" text from the admin footer.
How it works: Hides the WordPress version number and footer text from the admin area to remove WordPress branding and version information.
Benefits: Enhances security by hiding version information, provides cleaner admin appearance, and supports white-label implementation for client sites.

**Hide WP Version:**
What is it: Hide WP Version removes WordPress version information from the frontend HTML source and other locations.
How it works: Removes WordPress version information from various locations including admin footer, meta tags, and API responses.
Benefits: Improves security by hiding version information from potential attackers, creates cleaner admin interface, and supports professional white-label presentation.

**Add Blank Favicon:**
What is it: Add Blank Favicon uses a blank favicon to stop browsers from showing an unwanted or default site icon.
How it works: Adds a blank favicon to replace any default or theme-specific favicons, providing neutral branding or preparation for custom favicon implementation.
Benefits: Removes unwanted branding from browser tabs, provides neutral starting point for custom branding, and ensures consistent favicon experience.

**Disable Admin Email Check During Login:**
What is it: Disable Admin Email Check During Login skips the periodic admin email verification prompts WordPress shows.
How it works: Skips the periodic admin email verification prompts that WordPress displays to ensure admin email addresses are current.
Benefits: Reduces admin interruptions, streamlines login experience, and eliminates unnecessary email verification prompts for managed sites.

**Remove Help Tabs:**
What is it: Remove Help Tabs takes the "Help" tab off all WordPress admin pages.
How it works: Removes help tabs from admin pages that provide WordPress documentation and guidance links.
Benefits: Creates cleaner admin interface, reduces visual clutter, and provides more focused admin experience without distracting help information.

**Clean Head Tags:**
What is it: Clean Head Tags strips unnecessary meta tags and WordPress-specific markup from your page head.
How it works: Removes unnecessary meta tags, generator tags, and WordPress-specific markup from the HTML head section.
Benefits: Creates cleaner HTML output, reduces page size, removes WordPress fingerprinting, and provides better white-label implementation.

### Login Page

**Login Page Customization:**
What is it: Login Page Customization changes the login page background to a color, image, or video that matches your brand.
How it works: Customizes the entire login page background with color, image, or video options, providing complete visual transformation of the login experience with responsive backgrounds that adapt to all screen sizes.
Benefits: Creates branded login experience, improves visual appeal, and provides professional appearance that matches site or company branding.

**Custom Login Logo:**
What is it: Custom Login Logo replaces the default WordPress logo on the login page with your own image.
How it works: Uploads and configures a custom login page logo to replace the default WordPress logo, with configurable dimensions including Logo Width, Logo Height, Max Width (10-500px), Max Height (10-500px), Padding, Margin, Border Radius, and Background Color settings.
Benefits: Provides complete branding of login experience, creates professional first impression, and supports white-label implementation for client sites. Fine-grained dimension controls ensure perfect logo display across all devices.

**Login Form Styling:**
What is it: Login Form Styling customizes the colors, padding, borders, and shadows of the login form to match your brand.
How it works: Customizes login form colors, borders, button styling, and visual elements including form background, border radius, padding, shadow effects, and responsive design options.
Benefits: Provides consistent visual branding, improves user experience with professional styling, and creates cohesive brand experience from login through admin.

**Navigation Links Styling:**
What is it: Navigation Links Styling customizes the "Back to site" link and other navigation links on the login page.
How it works: Customizes the appearance of the "Go back to site" link and other navigation links on the login page, including link color and hover color.
Benefits: Creates branded navigation experience, improves visual consistency, and enables design coherence across the entire login page.

**Notices & Messages Styling:**
What is it: Notices & Messages Styling customizes how error, success, and info messages appear on the login page.
How it works: Customizes the appearance of error, success, and info notices on the login page with separate color controls for each type.
Benefits: Creates branded notice styling, improves visual consistency of error messages, and enhances user experience with clear, branded notifications.

**Disable Language Dropdown on Login Page:**
What is it: Disable Language Dropdown on Login Page removes the language switcher from the login screen.
How it works: Removes the language switcher dropdown from the WordPress login page, preventing users from changing the interface language during login.
Benefits: Streamlines the login page for monolingual sites, reduces visual clutter on the login form, and prevents accidental language changes during authentication.

---

## Options Tab

### Environment

**Enable Quick WordPress Setup:**
What is it: Enable Quick WordPress Setup re-enables the one-time guided setup wizard after it has already been run.
How it works: Re-enables the initial WordPress setup feature that guides users through basic site configuration and essential settings.
Benefits: Provides guided setup experience for new sites, ensures proper initial configuration, and helps users configure essential settings correctly.

**Enable Bricks Setup:**
What is it: Enable Bricks Setup lets you run the Bricks Builder setup process again to reconfigure its settings.
How it works: Allows running the Bricks Builder setup process again to reconfigure Bricks settings, templates, and initial configuration.
Benefits: Enables reconfiguration of Bricks Builder settings, provides fresh start for Bricks implementation, and allows setup correction if initial configuration needs adjustment.

**Launch Setup Wizard:**
What is it: Launch Setup Wizard runs the interactive onboarding flow that helps you pick starter profiles and configures the plugin.
How it works: Launches the interactive onboarding wizard that guides users through configuring starter profiles for the plugin, selecting feature presets (Performance Focus, Hardened Security, AI Suite, Minimalist Admin), and completing initial setup tasks.
Benefits: Provides a guided onboarding experience for new installations, helps users configure the optimal feature set for their needs, and reduces the initial learning curve with step-by-step setup assistance.

**Enable White Label:**
What is it: Enable White Label customizes the plugin's branding to match your agency or company identity.
How it works: Activates white label functionality that customizes the plugin branding to match your agency or company identity throughout the admin interface.
Benefits: Provides complete branding solution for agencies, creates professional client experience, and removes plugin branding for seamless white-label implementation.

**Hide Plugin from Plugins List:**
What is it: Hide Plugin from Plugins List makes Classic Monks disappear from the WordPress plugins list entirely.
How it works: Completely hides the plugin from the WordPress plugins list for ultimate white-label protection, requiring direct URL or FTP access for management.
Benefits: Provides maximum client-facing stealth, removes plugin visibility entirely, and prevents client interference with plugin settings.

**Hide Version Number:**
What is it: Hide Version Number removes the plugin version number from the plugins list.
How it works: Hides the plugin version number from the WordPress plugins list, removing version identification information.
Benefits: Removes version identification for security, prevents version comparison by clients, and maintains cleaner plugin presentation.

**Hide White Label Settings Access:**
What is it: Hide White Label Settings Access removes the white label settings section from the plugin interface so clients cannot change it.
How it works: Removes the white label settings section from the plugin interface, preventing clients from seeing or modifying white label configuration through an access URL.
Benefits: Protects white label configuration from client modification, maintains brand integrity, and ensures settings remain consistent.

**Hide Forum Link:**
What is it: Hide Forum Link removes the community forum link from the plugin's License page.
How it works: Removes the community forum link from the plugin's License page to reduce external navigation options for end users.
Benefits: Declutters the plugin interface, prevents users from accessing community forums for support, and provides a cleaner administrative experience.

**Hide Support Link:**
What is it: Hide Support Link removes the support dashboard link from the plugin's License page.
How it works: Removes the support dashboard link from the plugin's License page, controlling where users seek assistance.
Benefits: Directs support requests through preferred channels, prevents users from accessing external support portals, and maintains control over the support experience.

**Hide Facebook Link:**
What is it: Hide Facebook Link removes the Facebook group link from the plugin's License page.
How it works: Removes the Facebook group link from the plugin's License page, restricting social media navigation from the admin interface.
Benefits: Reduces distractions from the admin interface, controls external social media referrals, and provides a more focused plugin experience.

**Enable Not Paid:**
What is it: Enable Not Paid gradually fades your website out after a payment deadline, encouraging clients to pay you on time.
How it works: Gradually reduces website opacity after a payment deadline, encouraging timely payments from clients by making the site progressively less visible. Configurable due date, fade duration, and minimum opacity.
Benefits: Provides a professional way to encourage timely payments, creates gradual visual urgency without breaking the site, and maintains a professional approach to payment collection.

**Block Zoom and Context Menu:**
What is it: Block Zoom and Context Menu stops visitors from zooming or opening the context menu while the Not Paid effect is active.
How it works: Prevents visitors from zooming in or accessing the browser context menu during the Not Paid opacity effect period.
Benefits: Increases payment urgency, prevents inspection of the faded site, and reinforces the payment request message.

### Import

**Import Settings:**
What is it: Import Settings restores plugin settings from a JSON backup file, with the option to import only selected tabs.
How it works: Lets you upload a plugin settings JSON backup file and import it, with selective per-tab import and overwrite options so you control exactly what gets restored.
Benefits: Simplifies site migration and restoration, gives you control over what is imported, and lets you recover settings selectively.

### Export

**Export Settings:**
What is it: Export Settings saves your selected plugin settings to a JSON file as a backup or for moving to another site.
How it works: Exports the selected plugin settings to a JSON backup file that can be stored or imported on another site for migration.
Benefits: Creates reliable settings backups, makes migrating between sites easy, and lets you preserve your configuration.

### Reset

**Reset All Settings:**
What is it: Reset All Settings turns off every toggle across all tabs, returning the plugin to a clean, disabled state.
How it works: Turns off all plugin toggles across all tabs, returning plugin to default disabled state while preserving configuration options.
Benefits: Provides quick way to disable all features, enables troubleshooting by eliminating plugin effects, and allows fresh configuration start.

### Uninstall

**Remove Plugin Data on Uninstall:**
What is it: Remove Plugin Data on Uninstall permanently deletes all plugin data when you uninstall Classic Monks, leaving nothing behind.
How it works: When the plugin is uninstalled, all stored plugin data, settings, and database entries are permanently removed from your site.
Benefits: Leaves no residual data after uninstall, keeps your database clean, and ensures a complete removal of plugin traces.

### WP Reset

**Reset Database:**
What is it: Reset Database reverts the WordPress database to its default installation state while keeping your user accounts.
How it works: Reverts the WordPress database to its default installation state while preserving user accounts and basic site settings.
Benefits: Provides clean slate for development, removes problematic content or settings, and enables fresh start while maintaining user access.

**Delete Content:**
What is it: Delete Content removes all posts, pages, comments, terms, and taxonomies while keeping your other settings intact.
How it works: Removes all Posts, Pages, Comments, Terms, and Taxonomies while preserving site structure and user accounts.
Benefits: Quickly clears all content for fresh start, removes test content efficiently, and provides clean content slate for new site development.

**Empty wp-content Folders:**
What is it: Empty wp-content Folders clears out your uploads, cache, and other wp-content directories to reclaim space.
How it works: Clears contents of wp-content directories including uploads, themes (except active), and plugins (except essential ones).
Benefits: Reclaims storage space, removes unused files, and provides clean file system for optimized site performance.

**Delete All Plugins:**
What is it: Delete All Plugins uninstalls every plugin except Classic Monks, giving you a clean environment.
How it works: Uninstalls all plugins except Classic Monks to provide clean plugin environment while maintaining reset functionality.
Benefits: Removes plugin conflicts, provides clean plugin slate, and eliminates potential compatibility issues for fresh site development.

**Delete All Themes:**
What is it: Delete All Themes removes all your installed themes except the active one.
How it works: Removes all installed themes except the currently active theme to clean up theme directory and reduce file clutter.
Benefits: Reduces file system clutter, improves site security by removing unused themes, and simplifies theme management.

**Complete WordPress Reset:**
What is it: Complete WordPress Reset performs a full site reset in one action, combining all the reset operations.
How it works: Performs all above reset operations in a single action, providing complete site reset to default state.
Benefits: Provides comprehensive site reset, saves time with single-action cleanup, and ensures complete fresh start for site redevelopment.

---

## Performance Tab

### WordPress Optimizations

**Force HTTPS Links:**
What is it: Force HTTPS Links automatically converts all HTTP links on your site to HTTPS when you are using SSL, eliminating mixed content warnings.
How it works: Automatically converts all HTTP links to HTTPS when the site is using SSL by rewriting URLs in content, ensuring all internal links use secure connections.
Benefits: Improves site security by eliminating mixed content warnings, enhances SEO rankings with secure connections, and provides consistent HTTPS experience across the entire website.

**Disable All Updates:**
What is it: Disable All Updates turns off WordPress core, plugin, and theme updates entirely, giving you full control over what gets updated.
How it works: Disables all WordPress core, plugin, and theme updates by removing update notifications, blocking update checks, and preventing automatic updates from running.
Benefits: Prevents unexpected changes that could break functionality, maintains stable environment for production sites, and provides complete control over update timing and testing.

**Disable Search Functionality:**
What is it: Disable Search Functionality turns off the native WordPress search, removing search forms and replying to search attempts.
How it works: Disables the native WordPress search functionality by blocking search queries, removing search forms, and redirecting search attempts.
Benefits: Reduces server resource usage from search queries, eliminates search-based security vulnerabilities, and forces users to rely on navigation or external search solutions.

**Disable Google Fonts:**
What is it: Disable Google Fonts stops themes and plugins from loading fonts from Google's servers, using system or local fonts instead.
How it works: Prevents Google Fonts from loading by blocking font API requests and removing Google Fonts stylesheets from page loading.
Benefits: Improves page loading speeds by eliminating external font requests, enhances privacy by reducing Google tracking, and forces use of system or local fonts.

**Disable WordPress Font Library:**
What is it: Disable WordPress Font Library turns off the WordPress 6.5+ font management feature that lets you manage fonts and Google Fonts in the admin.
How it works: Disables the WordPress 6.5+ Font Library feature that allows font management and Google Fonts integration through the WordPress admin interface.
Benefits: Reduces admin interface complexity, prevents unwanted font loading, and maintains control over typography choices without automated font suggestions.

**Disable Emojis:**
What is it: Disable Emojis removes the emoji scripts and styles WordPress loads by default, trimming unnecessary code from your pages.
How it works: Removes WordPress emoji scripts and styles from the frontend by deregistering emoji-related JavaScript and CSS files that WordPress loads by default.
Benefits: Reduces page load times by eliminating unnecessary JavaScript and CSS, decreases HTTP requests, and improves performance for sites that don't use emojis.

**Disable Dashicons:**
What is it: Disable Dashicons stops the Dashicons icon font from loading on the frontend for visitors who are not logged in.
How it works: Disables Dashicons on the front-end for non-logged-in users by preventing the icon font from loading when not needed for admin functionality.
Benefits: Reduces frontend resource usage, improves page load speeds for visitors, and eliminates unnecessary font downloads for users who don't need admin icons.

**Disable Embeds:**
What is it: Disable Embeds turns off the oEmbed feature, stopping automatic video and content embeds and their related scripts.
How it works: Disables the oEmbed feature in WordPress by removing embed-related scripts, preventing automatic embed generation, and blocking embed discovery endpoints.
Benefits: Reduces external API calls, improves page loading performance, eliminates potential security risks from embed endpoints, and reduces server resource usage.

**Remove jQuery Migrate:**
What is it: Remove jQuery Migrate drops the jQuery Migrate compatibility script from the frontend, which most modern sites no longer need.
How it works: Removes the jQuery Migrate script that WordPress includes for backward compatibility with older jQuery versions and deprecated functions.
Benefits: Reduces JavaScript file size and loading time, eliminates unnecessary backward compatibility overhead, and improves page performance for modern implementations.

**Disable WP Responsive Images:**
What is it: Disable WP Responsive Images turns off WordPress's automatic responsive image (srcset) handling, giving you manual control.
How it works: Disables WordPress responsive image features including srcset and sizes attributes that are automatically added to image tags.
Benefits: Provides manual control over image responsive behavior, reduces HTML complexity, and allows custom responsive image implementations.

**Disable Google Maps:**
What is it: Disable Google Maps stops themes and plugins from loading the Google Maps API, cutting external requests.
How it works: Disables Google Maps API loading by blocking Google Maps JavaScript libraries and preventing automatic map script inclusion.
Benefits: Improves page loading performance by eliminating external API calls, reduces dependency on Google services, and provides privacy benefits for users.

**Remove RSD Link:**
What is it: Remove RSD Link removes the Really Simple Discovery (RSD) link from your page head, which is only used by remote publishing tools.
How it works: Removes the Really Simple Discovery (RSD) link from the HTML head that's used for blog clients and remote publishing tools.
Benefits: Reduces HTML head clutter, eliminates unnecessary HTTP header, and removes potential information disclosure about site capabilities.

**Remove Shortlink:**
What is it: Remove Shortlink strips the shortlink meta tag from your page head, simplifying your HTML output.
How it works: Removes the shortlink meta tag from the HTML head that WordPress generates for shorter URL alternatives to posts and pages.
Benefits: Reduces HTML head size, eliminates redundant URL information, and simplifies HTML output for better performance and cleaner code.

**Disable RSS Feeds:**
What is it: Disable RSS Feeds turns off all RSS feeds on your site, redirecting feed URLs so they are not generated.
How it works: Disables all RSS feeds by redirecting feed URLs to the homepage or 404 pages, preventing feed generation and access.
Benefits: Reduces server resource usage from feed generation, eliminates potential content scraping through feeds, and simplifies site architecture for non-blog sites.

**Remove RSS Feed Links:**
What is it: Remove RSS Feed Links takes the RSS feed links out of your page head, stopping feed discovery by tools.
How it works: Removes RSS feed links from the HTML head section while optionally maintaining feed functionality for direct access.
Benefits: Reduces HTML head clutter, eliminates feed discovery for automated tools, and provides control over feed visibility and access.

**Disable Self Pingbacks:**
What is it: Disable Self Pingbacks stops WordPress from sending pingbacks to itself when you link between pages on your own site.
How it works: Prevents self-pingbacks when linking to internal content by blocking pingback notifications for links within the same domain.
Benefits: Reduces unnecessary notifications and comments, eliminates self-referential spam, and improves comment management by focusing on external interactions.

**Disable Year/Month Folders for Uploads:**
What is it: Disable Year/Month Folders for Uploads saves all uploads into a single folder instead of the default year/month structure.
How it works: Organizes all uploads into a single folder instead of the default year/month folder structure, simplifying media organization and URL structure.
Benefits: Simplifies media management, creates cleaner URL structure, reduces folder complexity, and makes media migration and backup processes more straightforward.

**Enable Classic Widgets:**
What is it: Enable Classic Widgets restores the classic WordPress widgets screen, replacing the block-based widget editor.
How it works: Restores the classic WordPress widgets settings screens by reverting to the traditional widget interface instead of the Gutenberg block-based widget editor.
Benefits: Provides familiar interface for users accustomed to classic widgets, maintains compatibility with legacy widget configurations, and offers simpler widget management workflow.

### Heartbeat

**Limit Post Revisions:**
What is it: Limit Post Revisions caps how many revisions WordPress stores for each post, keeping your database from growing out of control.
How it works: Configures the maximum number of post revisions that WordPress stores by setting limits on revision history to control database growth.
Benefits: Reduces database size and improves performance, limits storage usage from excessive revisions, and maintains revision functionality while controlling resource consumption.

**Autosave Interval:**
What is it: Autosave Interval controls how often WordPress automatically saves your draft while you edit.
How it works: Sets the frequency of automatic post saving during editing sessions, controlling how often WordPress saves draft content automatically.
Benefits: Balances data protection with performance by reducing excessive autosave requests, provides customizable backup frequency, and reduces server load during content editing.

**Disable Heartbeat:**
What is it: Disable Heartbeat turns off the WordPress Heartbeat API, which runs constant background requests to the server.
How it works: Completely disables the WordPress heartbeat functionality that maintains connection between browser and server for real-time features.
Benefits: Significantly reduces server resource usage, eliminates constant AJAX requests, and improves performance for sites that don't need real-time features.

**Heartbeat Frequency:**
What is it: Heartbeat Frequency sets how often the WordPress Heartbeat API polls the server, balancing real-time features with performance.
How it works: Configures the frequency of WordPress heartbeat requests to balance real-time functionality with server performance requirements.
Benefits: Optimizes server resource usage while maintaining necessary real-time features, provides granular control over update frequency, and balances functionality with performance.

### Media Enhancements

**Enable Secure Downloads:**
What is it: Secure Downloads adds access control and protection for downloadable files, including expiring download links.
How it works: Adds secure download management for protected files by providing access control, logging, and protection for downloadable content.
Benefits: Protects downloadable content from unauthorized access, provides download tracking and analytics, and enables secure file distribution.

**Image Converter:**
What is it: Image Converter turns your images into modern WebP and AVIF formats, which load much faster than JPEG and PNG.
How it works: Converts images to WebP and AVIF formats for faster loading, providing modern image formats while maintaining compatibility options.
Benefits: Significantly reduces image file sizes, improves page loading speeds, and provides modern image format benefits while maintaining quality.

**Enable Unused Media Checker:**
What is it: Unused Media Checker scans your site and flags images in the Media Library that are not used anywhere.
How it works: Identifies and marks unused images in the Media Library by scanning content and detecting media files that aren't referenced anywhere.
Benefits: Helps clean up media library, reduces storage usage, and identifies media files that can be safely removed to optimize storage.

**Enable Missing Media Checker:**
What is it: Missing Media Checker finds media files where the database record exists but the actual file is missing from your server.
How it works: Detects orphaned media entries where database records exist but actual files are missing from the server filesystem.
Benefits: Identifies broken media references, helps maintain database integrity, and provides tools to clean up corrupted media entries.

**Media Trash Management:**
What is it: Media Trash Management safely handles deleted media, letting you recover files you removed by accident.
How it works: Safely manages and recovers accidentally deleted media files by providing trash functionality and recovery options for media items.
Benefits: Prevents permanent accidental media loss, provides safety net for media management, and enables recovery of mistakenly deleted files.

**Image Watermark:**
What is it: Image Watermark automatically adds an image or text watermark to your pictures, either on upload or in bulk.
How it works: Applies a configurable image or text watermark to your media automatically or in bulk, protecting your images from unauthorized use.
Benefits: Protects your images from being used without credit, adds a professional brand mark to your media, and automates watermarking across your library.

**Check and Delete Images by Dimensions:**
What is it: Check and Delete Images by Dimensions lets you find and delete image files of specific sizes to reclaim storage.
How it works: Provides tools to delete existing images of specific dimensions, helping clean up unnecessary image variations and reclaim storage space.
Benefits: Reduces storage usage by removing unused image sizes, improves media library management, and helps optimize storage costs.

**Enable Media Replacement:**
What is it: Media Replacement lets you swap out a media file for a new one while keeping the same attachment ID and all existing URLs.
How it works: Replaces media files while maintaining the same ID and file name, preserving all references, links, and integrations while updating content.
Benefits: Maintains all existing references and links, prevents broken media connections, and allows seamless media updates without affecting content structure.

**SVG Support:**
What is it: SVG Support lets you upload SVG vector graphics to WordPress, with preview support and built-in security.
How it works: Adds SVG upload support with previews and security features, enabling vector graphics while maintaining safety through sanitization.
Benefits: Enables scalable vector graphics for better design flexibility, reduces file sizes for icons and graphics, and maintains image quality at all sizes.

**SVG Security Sanitization:**
What is it: SVG Security Sanitization scans uploaded SVG files for malicious code before allowing them onto your site.
How it works: Enables security checks for SVG uploads by scanning for malicious code, scripts, and external references before allowing file uploads.
Benefits: Prevents SVG-based security attacks, maintains vector graphics functionality safely, and provides protection against malicious file uploads.

**Enable Bulk Media Download:**
What is it: Bulk Media Download lets you select multiple files in the Media Library and download them together as a ZIP archive.
How it works: Adds bulk download functionality to the Media Library, allowing selection of multiple files for download as a single ZIP archive with options for original files or scaled versions.
Benefits: Enables efficient bulk media export, simplifies media migration between sites, and provides convenient bulk archive creation for backups.

**Auto Resize Images After Upload:**
What is it: Auto Resize Images After Upload automatically shrinks large images to a maximum size when you upload them, keeping your library lean.
How it works: Automatically resizes large images to specified maximum dimensions when uploaded to the Media Library, helping reduce storage space and improve page load times.
Benefits: Reduces storage requirements, improves site performance with properly sized images, prevents accidental upload of oversized images, and maintains consistent image dimensions across the site.

**Skip Smaller Images:**
What is it: Skip Smaller Images leaves images below the target size untouched during auto-resize, so they are not needlessly re-encoded.
How it works: Skips the resize process for images that are already smaller than the configured maximum dimensions, leaving them unchanged.
Benefits: Prevents unnecessary processing of already-optimized images, saves server resources, and avoids quality degradation from re-encoding small images.

**Disable Unnecessary Image Sizes:**
What is it: Disable Unnecessary Image Sizes stops WordPress from generating intermediate image sizes you do not use, saving storage and processing.
How it works: Prevents generation of specific image sizes during upload, reducing storage usage and processing time for unused image variations.
Benefits: Reduces storage requirements, improves upload performance, and eliminates generation of unused image sizes that consume server resources.

**Disable Big Image Size Threshold:**
What is it: Disable Big Image Size Threshold stops WordPress from automatically scaling down large uploaded images, preserving their original quality.
How it works: Prevents automatic scaling of large uploaded images, maintaining original image dimensions and quality without forced resizing.
Benefits: Preserves original image quality and dimensions, maintains photographer intent, and prevents unwanted automatic image compression.

**Enable Media File Renaming:**
What is it: Media File Renaming lets you rename media files with custom naming patterns, updating references automatically.
How it works: Adds a "Rename File" action to the Media Library list view and a rename panel on the Edit Media screen. Renaming a file updates the attachment slug, the file path on disk, and common content references.
Benefits: Enables SEO-friendly filename updates and maintains content integrity by updating references automatically.

**Enable Media Duplicator:**
What is it: Media Duplicator creates copies of media files in the Media Library, each with its own new ID.
How it works: Adds duplicate functionality to media items, allowing creation of copies of existing media files with new IDs and references.
Benefits: Enables easy media replication for variations, provides backup options for media edits, and allows multiple uses of similar media without conflicts.

**Enable Media Library Infinite Scrolling:**
What is it: Media Library Infinite Scrolling replaces pagination with infinite scroll in the Media Library grid, so more items load as you scroll.
How it works: Adds infinite scrolling to the WordPress Media Library grid view, automatically loading more media items as you scroll down instead of using pagination.
Benefits: Improves media browsing experience for large libraries, eliminates pagination clicks, and provides seamless navigation through extensive media collections. Only works in grid view mode.

**Media List View Default:**
What is it: Media List View Default makes the Media Library open in list view instead of grid view by default.
How it works: Automatically redirects the media library to list view instead of grid view, providing detailed information and easier management interface.
Benefits: Improves media management efficiency, provides more detailed file information, and offers better control over media selection and organization.

**Enable Clean Image Filenames:**
What is it: Clean Image Filenames converts special characters and accents in uploaded filenames to plain ASCII equivalents.
How it works: Automatically converts language accent characters and special characters in filenames to ASCII equivalents during upload.
Benefits: Prevents filename compatibility issues, improves cross-platform compatibility, and ensures consistent URL structure across different systems.

### CDN Enabler

**Enable CDN Rewrite:**
What is it: CDN Rewrite swaps your site asset URLs for CDN URLs, so images and files are served from a network of fast servers worldwide.
How it works: Enables rewriting of site URLs with CDN URLs, automatically replacing local asset references with CDN equivalents for faster content delivery.
Benefits: Dramatically improves global loading speeds, reduces server bandwidth usage, and provides better user experience through geographically distributed content delivery.

**Disable for Admin Users:**
What is it: Disable for Admin Users turns off CDN rewriting when you are logged in as an admin, so your admin experience is unaffected.
How it works: Disables CDN rewriting for logged-in admin users, ensuring admin functionality works correctly while maintaining CDN benefits for visitors.
Benefits: Prevents admin interface conflicts with CDN delivery, ensures proper admin functionality, and maintains development workflow while optimizing visitor experience.

### Assets Manager

**Enable Assets Manager:**
What is it: Assets Manager lets you conditionally disable scripts and styles on specific pages, trimming unused code and speeding up your site.
How it works: Conditionally disables scripts and styles across your site based on page context, content type, and user-defined rules to reduce unnecessary loading.
Benefits: Significantly improves page loading speeds, reduces bandwidth usage, and eliminates loading of unused CSS and JavaScript files for better performance.

**Disable WordPress Emoji:**
What is it: Disable WordPress Emoji (within Assets Manager) removes the emoji scripts specifically for logged-in users.
How it works: Specifically removes WordPress emoji functionality within the Assets Manager context, providing granular control over emoji-related resources.
Benefits: Reduces page load times by eliminating emoji scripts, decreases HTTP requests, and provides targeted optimization for sites not using emoji features.

**Disable For Logged-In Users:**
What is it: Disable For Logged-In Users stops the Assets Manager from disabling any assets while you are logged in, so editing stays predictable.
How it works: Prevents Assets Manager from disabling any assets or plugins for logged-in users, keeping the frontend management experience predictable while still applying rules to visitors.
Benefits: Maintains consistent admin experience, prevents unexpected behavior during site editing, and ensures development tools remain accessible.

**Show Non-Loaded Assets:**
What is it: Show Non-Loaded Assets hides assets that are not actually loading on the current page, decluttering the Assets Manager panel.
How it works: When disabled, only assets that are actually loaded on the current page will be shown in the Assets Manager, improving performance and reducing clutter by hiding unnecessary assets.
Benefits: Reduces interface clutter in the Assets Manager panel, improves management performance, and focuses attention on relevant assets only.

**Hide Admin Bar Control:**
What is it: Hide Admin Bar Control removes the Assets Manager button from the admin bar, keeping the panel accessible another way.
How it works: Hides Assets Manager controls from the admin bar while keeping the panel accessible through other means.
Benefits: Provides a cleaner admin bar interface, reduces visual clutter for non-technical users, and allows alternative access methods for asset management.

**Show Frontend Icon:**
What is it: Show Frontend Icon adds a floating button on the frontend that opens the Assets Manager, so admins can optimize from the live page.
How it works: Displays a floating icon button on the frontend that provides quick access to the Assets Manager panel. The icon only appears for admin users.
Benefits: Enables quick frontend access to asset management, provides convenient testing workflow, and allows real-time optimization directly from the frontend.

### Lazy Loading

**Enable Lazy Loading:**
What is it: Lazy Loading defers loading images, videos, and iframes until they enter the viewport, so pages load much faster.
How it works: Enables lazy loading for images, iframes, and other media elements by deferring loading until elements enter the viewport.
Benefits: Dramatically improves initial page load times, reduces bandwidth usage, and provides better user experience by loading content as needed.

**Disable for Admin Users:**
What is it: Disable for Admin Users turns off lazy loading when you are logged in as an admin, so your editing view is not affected.
How it works: Disables lazy loading for logged-in admin users, keeping the admin experience consistent while visitors still get the performance benefit.
Benefits: Prevents admin interface conflicts, ensures proper admin functionality, and maintains a smooth development workflow while optimizing the visitor experience.

**Lazy Load Images:**
What is it: Lazy Load Images defers image loading until each image is about to scroll into view.
How it works: Enables lazy loading specifically for image elements, loading images only when they're about to enter the user's viewport.
Benefits: Reduces initial page load times, saves bandwidth for users, and improves perceived performance by prioritizing above-the-fold content.

**Lazy Load iFrames:**
What is it: Lazy Load iFrames defers loading of embedded iframes, like videos and external widgets, until they are needed.
How it works: Enables lazy loading for iframe elements, deferring loading of embedded content like videos and external widgets until needed.
Benefits: Prevents slow external content from blocking page loading, reduces initial resource usage, and improves control over third-party content loading.

**Lazy Load Background Images:**
What is it: Lazy Load Background Images defers loading of CSS background images until they scroll into view.
How it works: Enables lazy loading for CSS background images by detecting background image usage and applying lazy loading techniques.
Benefits: Optimizes background image loading, reduces initial CSS processing time, and provides comprehensive image optimization beyond standard img tags.

**Lazy Load HTML5 Videos:**
What is it: Lazy Load HTML5 Videos defers loading of HTML5 video elements until they are about to be seen.
How it works: Enables lazy loading for HTML5 `<video>` elements including source elements and poster images, deferring video loading until the element enters the viewport.
Benefits: Reduces initial page load for video-heavy pages, prevents loading of off-screen videos, and improves overall page performance while preserving video functionality.

**Lazy Load YouTube Videos:**
What is it: Lazy Load YouTube Videos defers loading YouTube embeds, showing a placeholder until the visitor interacts with it.
How it works: Enables lazy loading specifically for YouTube embeds, replacing video embeds with placeholder images until user interaction.
Benefits: Dramatically improves page loading by preventing YouTube script loading, reduces external requests, and provides better control over video content loading.

**Use Native Lazy Loading When Available:**
What is it: Use Native Lazy Loading When Available uses the browser's built-in lazy loading when supported, falling back to JavaScript for older browsers.
How it works: Uses the browser's built-in lazy loading functionality when supported, falling back to JavaScript implementation for older browsers.
Benefits: Provides optimal performance through native browser features, ensures compatibility across all browsers, and leverages built-in optimizations when available.

**Preload Critical Images:**
What is it: Preload Critical Images loads the images above the fold right away, so above-the-fold content appears instantly.
How it works: Preloads above-the-fold images to ensure critical content loads immediately while maintaining lazy loading for below-the-fold content.
Benefits: Balances performance optimization with user experience, ensures critical content loads quickly, and maintains lazy loading benefits for non-critical content.

**Exclude Above-the-Fold Images:**
What is it: Exclude Above-the-Fold Images keeps the most important images from being lazy-loaded, so they appear immediately.
How it works: Prevents critical images from being lazy-loaded to ensure immediate visibility of important content without loading delays.
Benefits: Ensures immediate visibility of critical content, prevents perceived performance issues, and maintains user experience while optimizing non-critical content.

**Enable Fade-in Animation:**
What is it: Enable Fade-in Animation adds a smooth fade-in effect as lazy-loaded content appears during scrolling.
How it works: Adds fade-in effects for lazy-loaded elements, creating smooth visual transitions as content appears during scrolling.
Benefits: Provides polished user experience, creates smooth content appearance, and adds visual interest to the loading process while maintaining performance benefits.

**Enable Lazy Rendering:**
What is it: Enable Lazy Rendering defers rendering of entire sections of content, not just individual elements.
How it works: Lazily loads entire sections of content, not just individual elements, providing comprehensive performance optimization for complex layouts with configurable selectors, delay, and target element types.
Benefits: Dramatically reduces initial page complexity, improves loading performance for content-heavy pages, and provides granular control over content rendering.

**Enable Negative Loading:**
What is it: Enable Negative Loading unloads off-screen elements when they leave the viewport, freeing up memory on long pages.
How it works: Unloads elements when they exit the viewport, freeing up memory and resources for better performance on long pages, with configurable unloading of CSS styles, images, videos, and iframes.
Benefits: Optimizes memory usage on long pages, improves performance for infinite scroll implementations, and maintains browser responsiveness with large content volumes.

**Unload CSS Styles:**
What is it: Unload CSS Styles removes the stylesheets of off-screen elements from the page when negative loading is active, reducing CSS processing.
How it works: Removes stylesheets of off-screen elements from the DOM when negative loading is active, freeing up CSS processing resources.
Benefits: Reduces CSS processing overhead, improves style recalculation performance, and prevents style conflicts from hidden elements.

**Unload Images:**
What is it: Unload Images clears the image sources of off-screen elements to free browser memory, restoring them when they scroll back into view.
How it works: Clears image sources (src) of off-screen elements to free browser memory, restoring them when elements re-enter the viewport.
Benefits: Significantly reduces memory usage from image-heavy pages, prevents browser tab crashes on long pages, and maintains responsive user experience.

**Unload Videos:**
What is it: Unload Videos stops off-screen videos from playing and buffering, releasing their resources until they come back into view.
How it works: Unloads video elements when they exit the viewport, stopping playback and releasing video resources until the video comes back into view.
Benefits: Prevents continued video buffering off-screen, reduces bandwidth waste, and frees CPU resources for visible content.

**Unload iFrames:**
What is it: Unload iFrames stops off-screen iframes from processing and releases their resources until they return to the viewport.
How it works: Unloads iframe elements when they exit the viewport, stopping iframe processes and releasing their resources until they return to the viewport.
Benefits: Eliminates hidden iframe processing, reduces memory usage from embedded content, and prevents background iframe activity.

### Monks Preloading

**Enable Intelligent Preloading:**
What is it: Intelligent Preloading predicts which page a visitor will click next and loads it in advance, making navigation feel instant.
How it works: Automatically preloads pages as users browse by predicting navigation patterns and prefetching likely next destinations.
Benefits: Dramatically improves perceived navigation speed, provides near-instant page transitions, and enhances user experience through predictive loading.

**Disable for Admin Users:**
What is it: Disable for Admin Users turns off preloading when you are logged in as an admin.
How it works: Disables preloading for logged-in admin users, keeping the admin experience consistent while visitors still benefit from predictive loading.
Benefits: Prevents admin interface conflicts, ensures proper admin functionality, and maintains a smooth development workflow while optimizing the visitor experience.

**Enable on Mobile Devices:**
What is it: Enable on Mobile Devices turns on preloading for mobile visitors, taking data usage and battery into account.
How it works: Allows preloading on mobile devices with consideration for data usage and battery life concerns.
Benefits: Provides mobile performance optimization, improves mobile user experience, and offers configurable mobile-specific optimization strategies.

**Enable on Slow Connections:**
What is it: Enable on Slow Connections turns on preloading even for visitors on slow networks, adapting to their connection speed.
How it works: Allows preloading on slow connections with adaptive behavior that considers connection speed and data limitations.
Benefits: Provides performance benefits even on slow connections, adapts to user's network conditions, and maintains optimization effectiveness across different connection types.

**Stop on Errors:**
What is it: Stop on Errors automatically halts preloading when errors are detected, so resources are not wasted on broken content.
How it works: Automatically stops preloading when errors are encountered, preventing continued resource usage on problematic content.
Benefits: Prevents waste of resources on broken content, maintains site stability, and provides automatic error handling for preloading operations.

**Enable Selective Media Preload:**
What is it: Enable Selective Media Preload lets you specify which media files should be preloaded on a specific page.
How it works: Adds a metabox to posts and pages that allows specifying which media files should be preloaded, enabling page-specific resource hints for critical assets.
Benefits: Improves critical page performance by preloading only essential media, reduces bandwidth waste from bulk preloading, and provides fine-grained control over resource prioritization.

**Enable Custom URL Preload Method:**
What is it: Enable Custom URL Preload Method lets you preload specific URLs of your choosing instead of relying on predictive preloading.
How it works: Allows you to specify custom URLs for preloading instead of relying on predictive preloading algorithms, giving you direct control over which pages are preloaded for visitors.
Benefits: Provides precise control over which pages get preloaded, enables targeted preloading for key conversion pages, and ensures critical pages are always ready for instant navigation.

---
