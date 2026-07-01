---
title: "How to Use Quick WordPress Setup in WordPress | CM"
slug: core/quick-wp-setup
description: "Run the Quick WordPress Setup wizard in Classic Monks to configure a fresh WordPress site in 2-3 minutes. Installs plugins, creates pages, sets permalinks, and optimizes your environment."
last_updated: 2026-06-24
author: Joy
reading_time: 10 min
canonical: https://classicmonks.com/docs/core/quick-wp-setup/
---

# How to Use Quick WordPress Setup in WordPress

> Quick WordPress Setup is a one-time automated wizard that configures your WordPress site with recommended settings, installs essential plugins and themes, creates standard pages, and optimizes your environment. It compresses 20-30 minutes of manual setup into a 2-3 minute wizard.

## Key Takeaways

- One-time wizard for fresh WordPress installations
- 7 configuration sections with detailed sub-options
- Installs plugins and themes from the WordPress repository or local ZIP upload
- Creates standard pages (Home, About, Contact, Services, Blog, Privacy, Terms, FAQ)
- Configures site identity, timezone, membership, permalinks, and homepage
- Removes default content (Hello World, Sample Page, default plugins)
- Includes self-hosted Google Analytics v4 setup
- Re-runnable via Options > Environment

---

## What Is Quick WordPress Setup?

Quick WordPress Setup is a guided wizard that automates the manual configuration steps you would normally perform on a fresh WordPress installation. Instead of clicking through WordPress Settings, installing plugins one at a time, creating pages manually, and editing the database, you check the boxes you want and the wizard handles the rest.

The wizard is split into 7 configuration sections, each with detailed sub-options:

1. **Site Identity**, Site title, tagline, logo, favicon, language, week start day, timezone, and date/time formats
2. **Membership**, User registration and default user role
3. **Install Plugins and Themes**, Search WordPress.org or upload ZIP files
4. **Homepage Settings**, Latest posts or static page with page selection
5. **Search Engine Visibility**, Indexing, permalinks, comments, and page creation
6. **Cleanup and Optimization**, Remove default content, plugins, themes, and config files
7. **Media Settings**, Thumbnail sizes, upload folders, and avatars
8. **Dashboard and Interface**, Screen options, patterns, and welcome guide

## Why You Need It

A clean WordPress install ships with default content (Hello World post, Sample Page, default plugins like Akismet and Hello Dolly), unset permalinks, UTC timezone, generic site identity, and no standard pages. Manually addressing all of this takes 20-30 minutes of clicking through settings screens, plugin searches, and page creation.

Quick WordPress Setup compresses that into a 2-3 minute wizard. For agencies building client sites, the savings multiply across every project.

---

## How to Use Quick WordPress Setup in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Core Tab

Click on the **Core** menu. The Setup subtab opens by default.

### Step 3: Enable Quick WordPress Setup

The Setup subtab shows a **Start WordPress Setup** button. Click it to open the setup modal.

### Step 4: Configure Each Section

The modal walks through 7 sections. Use the **Select All** or **Deselect All** buttons in the modal footer to quickly toggle all options. Check the boxes you want and fill in the relevant fields.

### Step 5: Run Setup

Click **Run Setup** in the modal footer. The wizard shows real-time progress with a progress bar and log. The whole process takes 2-3 minutes.

### Step 6: Reload and Verify

After setup completes, reload the WordPress admin. The configured settings are now in effect. The Setup subtab will show a "Re-run WordPress Setup" button if you want to run the wizard again with different options.

---

## Section 1: Site Identity

The Site Identity section configures your WordPress site's identity and regional settings.

| Option | Type | Description | Default |
|--------|------|-------------|---------|
| **Site Title** | Text input | The name of your site. Appears in the browser tab, search results, and theme header. | Current site title |
| **Tagline** | Text input | A short description of your site. Appears below the site title in the theme header. | Current tagline |
| **Set Site Logo** | Toggle | Upload a logo to use as your site's main logo. Opens the WordPress Media Library. | Off |
| **Set Site Icon (Favicon)** | Toggle | Upload a square image (512x512px minimum) for the browser tab icon. Opens the WordPress Media Library. | Off |
| **Site Language** | Dropdown | Select the WordPress admin language. Shows all available translations. | English (United States) |
| **Week Starts On** | Dropdown | Which day the week starts on (used by calendars and week-based queries). | Sunday |
| **Set Timezone & Date Format** | Toggle | Opens sub-options for timezone, date format, and time format. | Off |

When **Set Timezone & Date Format** is enabled, three additional fields appear:

| Sub-Option | Type | Description |
|------------|------|-------------|
| **Timezone** | Dropdown (grouped by region) | Select your timezone. Grouped by continent (Africa, America, Asia, Europe, etc.). |
| **Date Format** | Dropdown | 5 options: "F j, Y", "Y-m-d", "m/d/Y", "d/m/Y", "j F Y". Shows a live preview of each. |
| **Time Format** | Dropdown | 3 options: "g:i a" (lowercase AM/PM), "g:i A" (uppercase AM/PM), "H:i" (24-hour). |

---

## Section 2: Membership

The Membership section controls whether visitors can register and what role they receive.

| Option | Type | Description | Default |
|--------|------|-------------|---------|
| **Anyone Can Register** | Toggle | Allow visitors to create user accounts on your website. When enabled, users can register for new accounts. | Off |
| **New User Default Role** | Dropdown | Select the default role assigned to new users when they register. Shows all registered roles (Subscriber, Contributor, Author, Editor, Administrator, plus any custom roles). | Subscriber |

**Why this matters:** If you're building a client site, you may want to enable registration with a custom role (e.g., "Customer" for WooCommerce, or "Subscriber" for a blog). The wizard sets this once so you don't have to find it in Settings > General.

---

## Section 3: Install Plugins and Themes

The Install Plugins and Themes section lets you search the WordPress.org repository, upload ZIP files, and activate a theme.

### Plugins

| Option | Type | Description |
|--------|------|-------------|
| **Install Plugins** (Search) | Live search | Type in the search box to find plugins from the WordPress.org repository. Results appear as you type. Click a result to add it to the install queue. |
| **Upload Plugins** (Upload) | File upload | Click "Add Plugin(s)" to upload plugin ZIP files from your computer. Multiple files can be selected. Accepted format: `.zip` |

**How it works:**
1. Search for plugins in the search box (e.g., "Wordfence", "RankMath", "WPForms")
2. Click on each result to add it to the queue (shown in the "Selected" list)
3. Or click "Add Plugin(s)" to upload ZIP files directly
4. All queued plugins will be automatically installed and activated when you run the setup

### Themes

| Option | Type | Description |
|--------|------|-------------|
| **Install Themes** (Search) | Live search | Search for themes from the WordPress.org repository. Click a result to add it to the install queue. |
| **Upload Theme(s)** (Upload) | File upload | Click "Add Theme(s)" to upload theme ZIP files. Multiple files can be selected. |
| **Select Theme to Activate** | Dropdown | After adding themes, select one to activate. The dropdown populates with all installed and queued themes. |

**How it works:**
1. Search for themes or upload ZIP files
2. Select a theme from the "Select Theme to Activate" dropdown
3. The selected theme will be activated when you run the setup

**Note:** Plugins are automatically activated. Themes must be explicitly selected for activation.

---

## Section 4: Homepage Settings

The Homepage Settings section configures what visitors see on your site's front page.

| Option | Type | Description | Default |
|--------|------|-------------|---------|
| **Your latest posts** | Radio button | Show a blog-style feed of your latest posts on the homepage. | Selected (default) |
| **A static page** | Radio button | Show a specific page as the homepage. Reveals two page dropdowns when selected. |, |

When "A static page" is selected, two additional fields appear:

| Sub-Option | Type | Description |
|------------|------|-------------|
| **Homepage** | Dropdown | Select which page to use as the homepage. Lists all published pages. |
| **Posts Page** | Dropdown | Select which page to use for the blog feed. Lists all published pages. |

**Tip:** If you're creating pages in the "Search Engine Visibility" section (Auto Create Important Pages), the Homepage and Posts Page dropdowns will be populated with those newly created pages. You can also use the "Set Created Home Page as Front Page" and "Set Created Blog Page as Posts Page" toggles to automatically assign them.

---

## Section 5: Search Engine Visibility

The Search Engine Visibility section controls indexing, permalinks, comments, and page creation.

| Option | Type | Description | Default |
|--------|------|-------------|---------|
| **Discourage search engines from indexing this site** | Toggle | Sets the `blog_public` option to 0. Prevents Google, Bing, and other search engines from indexing your site. Useful for staging or development sites. | Off |
| **Set Permalink Structure** | Toggle | Opens a dropdown to select the permalink structure. | Off |

When **Set Permalink Structure** is enabled:

| Sub-Option | Description |
|------------|-------------|
| **Plain** | `/?p=123`, Default WordPress structure |
| **Day and name** | `/%year%/%monthnum%/%day%/%postname%/` |
| **Month and name** | `/%year%/%monthnum%/%postname%/` |
| **Post name** | `/%postname%/`, Recommended for most sites |
| **Numeric** | `/archives/%post_id%` |
| **Post name with ID** | `/%postname%/%post_id%/` |

| Option | Type | Description | Default |
|--------|------|-------------|---------|
| **Disable Comments and Pings** | Toggle | Disables comments on new posts and disables pings. Existing comments are preserved. | Off |
| **Auto Create Important Pages** | Toggle | Opens sub-options to select which standard pages to create. | Off |

When **Auto Create Important Pages** is enabled, 9 page options appear:

| Sub-Option | Default | Description |
|------------|:-------:|-------------|
| **Home Page** | On | Creates a blank "Home" page |
| **About Us** | On | Creates a blank "About Us" page |
| **Contact** | On | Creates a blank "Contact" page |
| **Services** | Off | Creates a blank "Services" page |
| **Blog** | Off | Creates a blank "Blog" page |
| **Privacy Policy** | On | Creates a "Privacy Policy" page with WordPress's default privacy policy content |
| **Terms and Conditions** | On | Creates a blank "Terms and Conditions" page |
| **FAQ** | Off | Creates a blank "FAQ" page |
| **Set Created Home Page as Front Page** | On | Automatically assigns the new Home page as the site front page |
| **Set Created Blog Page as Posts Page** | Off | Automatically assigns the new Blog page as the posts page |

---

## Section 6: Cleanup and Optimization

The Cleanup and Optimization section removes default WordPress content that clutters a fresh installation.

| Option | Type | Description | Default |
|--------|------|-------------|---------|
| **Remove "Hello World" post** | Toggle | Deletes the default "Hello World" blog post. | Off |
| **Remove Sample Page** | Toggle | Deletes the default "Sample Page". | Off |
| **Rename "Uncategorized" to "General"** | Toggle | Renames the default "Uncategorized" category to "General". | Off |
| **Remove Default Plugins** | Toggle | Deactivates and deletes default plugins (Akismet, Hello Dolly). | Off |
| **Remove Unused Themes** | Toggle | Removes all themes except the active one (Twenty Twenty-Four, etc.). | Off |
| **Remove wp-config-sample.php & readme.html** | Toggle | Deletes `wp-config-sample.php` and `readme.html` from the root directory. | Off |

**Note:** The "Remove Default Plugins" option deactivates AND deletes Akismet and Hello Dolly. If you need Akismet, install it separately after running the wizard.

---

## Section 7: Media Settings

The Media Settings section controls how WordPress handles media uploads.

| Option | Type | Description | Default |
|--------|------|-------------|---------|
| **Disable Thumbnail Sizes** | Toggle | Prevents WordPress from generating thumbnail image sizes (150x150, 300x300). Reduces disk usage and database entries. | Off |
| **Disable Year/Month Folders for Uploads** | Toggle | Saves uploads directly to `/wp-content/uploads/` instead of `/wp-content/uploads/2026/06/`. Simplifies URLs. | Off |
| **Disable Avatars** | Toggle | Disables the Gravatar avatar system. No profile pictures are loaded from Gravatar servers. | Off (respects current setting) |

---

## Section 8: Dashboard and Interface

The Dashboard and Interface section cleans up the WordPress admin interface.

| Option | Type | Description | Default |
|--------|------|-------------|---------|
| **Disable Screen Options & Widgets** | Toggle | Removes the "Screen Options" tab and admin dashboard widgets. Provides a cleaner admin experience. | Off |
| **Disable Patterns & Welcome Guide** | Toggle | Disables the WordPress block pattern library and the welcome guide that appears on first login. | Off |

---

## Self-Hosted Google Analytics v4

The Setup subtab also includes the **Self-Host Google Analytics v4** toggle, which is a separate but related feature. When enabled, you can:

| Option | Type | Description | Default |
|--------|------|-------------|---------|
| **Self-Host Google Analytics v4** | Toggle | Self-host the GA4 tracking script instead of loading from Google's servers. | Off |
| **Google Analytics Tracking ID** | Text input | Your GA4 measurement ID (format: G-XXXXXXXXXX). | Empty |
| **Tracking Script** | Dropdown | **Minimal Analytics** (1.4KB, recommended) for ultra-fast tracking, or **Gtag.js** (90KB) for full GA4 features (events, ecommerce, custom dimensions). | Minimal Analytics |
| **Disable for logged in admins** | Toggle | Prevent analytics tracking for administrators. Prevents admin activity from skewing analytics data. | On |

This is a performance-focused alternative to loading the standard Google Analytics script from Google's servers. Minimal Analytics is a lightweight implementation that provides the core GA4 metrics without the overhead of the full Gtag.js library.

---

## What the Setup Wizard Configures

| Section | What it does |
|---------|-------------|
| **Site Identity** | Sets site title, tagline, logo, favicon, language, week start day, timezone, date and time formats |
| **Membership** | Enables/disables user registration, sets default user role |
| **Install Plugins and Themes** | Searches WordPress.org repository, uploads ZIP files, activates selected theme |
| **Homepage Settings** | Configures static homepage or latest posts, sets homepage and posts page |
| **Search Engine Visibility** | Toggles search engine indexing, sets permalink structure, disables comments, auto-creates standard pages |
| **Cleanup and Optimization** | Removes default content and plugins, renames Uncategorized |
| **Media Settings** | Disables thumbnail sizes, year/month folders, avatars |
| **Dashboard and Interface** | Disables screen options, patterns, welcome guide |

---

## Re-running Setup

After the first run, the button changes to **WordPress Setup Completed** and is disabled. To re-run:

1. Go to **Options > Environment** in the Classic Monks settings
2. Find the Quick WordPress Setup option
3. Enable it again
4. Reload the page
5. Return to Core > Setup, the button is now **Re-run WordPress Setup**

Re-running is useful when:

- Setting up a second site with similar configuration
- Recovering from a botched first run
- Adopting a new standard configuration across multiple sites

**Important:** Re-running the wizard applies all checked sections. Deselect any sections you want to keep current before re-running. The wizard only changes what you check.

---

## Developer Integration

The setup wizard runs as an AJAX-driven modal. The setup state is tracked in the `wp_setup_completed` option. The `wp_setup` feature flag controls whether the button is available.

**Option mapping:** The setup wizard maps its options to Classic Monks plugin options using the following mapping:

| Setup Option | Plugin Options Set |
|-------------|-------------------|
| `disable_comments` | `disable_comments`, `modify_comment_links`, `remove_comments_from_admin_bar`, `remove_comments_menu` |
| `disable_thumbnails` | `disable_wp_responsive_images`, `disable_big_image_size_threshold` |
| `disable_patterns_welcome` | `deactivate_block_directory`, `deactivate_core_block_patterns`, `auto_close_welcome_guide`, `auto_exit_fullscreen_mode` |
| `disable_screen_options` | `remove_dashboard_widgets`, `remove_help_tabs` |
| `disable_avatars` | `show_avatars` (set to 0) |
| `disable_yearmonth_folders` | `disable_year_month_folders` |
| `disable_core_sitemaps` | `disable_core_sitemaps` |

The wizard uses `cm_update_option()` to persist each setting and `cm_is_feature_enabled()` to check feature flags. After completion, it sets `wp_setup_completed` to `true` and disables the `enable_wp_setup` toggle automatically.

---

## Troubleshooting

### "WordPress Setup Completed" Button Is Greyed Out

**Cause:** The setup has been run and the wp_setup feature flag is off.
**Fix:** Go to **Options > Environment** and enable Quick WordPress Setup, then reload.

### Setup Modal Does Not Open

**Cause:** JavaScript conflict with another plugin or theme, or a console error.
**Fix:** Open browser dev tools, check the console for errors. Disable other plugins one at a time to identify the conflict.

### Setup Completes But Settings Are Not Applied

**Cause:** File system permissions prevent WordPress from writing to wp-config.php or the database.
**Fix:** Verify WordPress has write access to the filesystem. Check wp-config.php permissions.

### Plugin or Theme Installation Fails

**Cause:** The server cannot reach the WordPress.org API, or the ZIP file is invalid.
**Fix:** Check the server's internet connection. For ZIP uploads, verify the file is a valid plugin/theme ZIP. Check the PHP `upload_max_filesize` setting if the ZIP is large.

### Self-Hosted Analytics Script Does Not Track

**Cause:** Tracking ID is wrong, the Minimal Analytics script is not loaded, or caching is serving stale pages.
**Fix:** Verify the tracking ID in browser dev tools. Clear all caching layers. Test in incognito mode.

### Re-Run Setup Resets Settings I Did Not Want Changed

**Cause:** Re-running the wizard applies all checked sections, including ones you may not want to re-run.
**Fix:** Before re-running, deselect any sections you want to keep current. The wizard only changes what you check.

### Pages Are Created But Not Assigned as Homepage

**Cause:** The "Set Created Home Page as Front Page" option is off, or the page order is different than expected.
**Fix:** Enable the "Set Created Home Page as Front Page" toggle in the Search Engine Visibility section. If pages are created but not assigned, manually set them in Settings > Reading.

### The Setup Progress Bar Freezes

**Cause:** A server timeout or a slow plugin installation is blocking the AJAX request.
**Fix:** Check the server error log. Increase the PHP `max_execution_time` setting if the setup takes longer than expected. The wizard handles timeouts gracefully and retries failed steps.

---

## Frequently Asked Questions

### When should I run Quick WordPress Setup?

Only on a fresh WordPress install. The wizard is destructive: it removes default content (Hello World, Sample Page, default plugins), creates new pages, and changes settings. Running it on an existing site will overwrite your configuration.

### Can I run it more than once?

The first run is one-time. After completion, the button changes to "Re-run WordPress Setup" and is disabled by default. To re-run, go to **Options > Environment** in Classic Monks settings, enable Quick WordPress Setup, reload, then re-run from Core > Setup.

### What if the wizard fails partway through?

The wizard shows real-time progress for each section. If it fails (e.g., a plugin install times out), check the setup log. The sections that completed successfully stay applied; the failed section can be retried individually by re-running the wizard.

### Does it work with `DISALLOW_FILE_MODS` enabled?

No. The wizard needs to install plugins and themes, which `DISALLOW_FILE_MODS` blocks. If your wp-config.php has this constant, the Quick WordPress Setup button is disabled with a warning notice. Remove the constant temporarily, run the wizard, then re-enable it.

### What plugins does it install by default?

The wizard searches the WordPress.org repository for plugins you select. It does not auto-install a fixed list. Common picks include security (Wordfence, Sucuri), SEO (RankMath, Yoast), and forms (WPForms, Contact Form 7), but the choice is yours.

### Can I use it on multisite?

The wizard is designed for single-site installs. On multisite, the wizard may not correctly configure network-wide settings. Use it on individual subsites with caution.

### What happens to existing content?

The wizard only removes default WordPress content (Hello World, Sample Page). Your existing posts, pages, media, and custom content are not affected. The "Remove Default Plugins" option only removes Akismet and Hello Dolly, not your custom plugins.

### Is there a way to automate the wizard for deployment?

The wizard is designed for manual use in the admin interface. For automated deployment, use WP-CLI or a custom migration script that sets the same options the wizard uses.

---

## Related Articles

- [How to Use Self-Hosted Google Analytics v4 in Classic Monks](core-self-hosted-analytics.md)
- [How to Add Code Snippets in WordPress (PHP, CSS, JS)](../code-manager.md)
- [How to Use the Environment Manager in WordPress](../options/options-environment.md)
