# Classic Monks Documentation

Official documentation for the Classic Monks WordPress plugin.

---

## Structure

```
docs/
├── templates/
│   ├── style-guide.md          # Writing conventions for all docs
│   └── article-template.md     # Copy this for new articles
├── general/                    # Per-tab feature guides
│   ├── code-manager.md         # Standalone (Code Manager submenu)
│   ├── short-links-tracking.md # Standalone (Short Links submenu)
│   ├── email.md                # Email tab index
│   ├── email/                  # Email tab docs (10 files)
│   │   ├── email-logging.md
│   │   ├── email-smtp-settings.md
│   │   ├── email-notifications.md
│   │   ├── email-comment-reply-email.md
│   │   ├── email-disable-password-change-email.md
│   │   ├── email-disable-new-user-email.md
│   │   ├── email-disable-admin-email-change.md
│   │   ├── email-disable-auto-update-core.md
│   │   ├── email-disable-auto-update-plugins.md
│   │   └── email-disable-auto-update-themes.md
│   ├── ai/                     # AI tab docs (8 files)
│   │   ├── ai-features-master.md
│   │   ├── ai-provider.md
│   │   ├── vision-image-provider.md
│   │   ├── ai-agent.md
│   │   ├── ai-tools.md
│   │   ├── ai-advanced.md
│   │   ├── ai-status.md
│   │   └── ai-systems-prompt.md (coming)
│   ├── core/                   # Core tab docs (39 files)
│   │   ├── core-quick-wp-setup.md
│   │   ├── core-self-hosted-analytics.md
│   │   ├── core-file-downloader.md
│   │   ├── core-content-management.md
│   │   ├── core-content-management/ (sub-options, all docs split)
│   │   ├── core-custom-columns.md
│   │   ├── core-content-utilities.md
│   │   ├── core-comments.md
│   │   ├── core-shortcodes.md
│   │   ├── core-gutenberg.md
│   │   ├── core-users.md
│   │   ├── core-plugins.md
│   │   ├── core-advanced-plugin-manager.md
│   │   ├── core-logs.md
│   │   ├── core-post-type-switcher.md
│   │   ├── core-taxonomy-switcher.md
│   │   ├── core-order-post-types.md
│   │   ├── core-custom-taxonomy-filters.md
│   │   ├── core-global-404-redirect.md
│   │   ├── core-conditional-menu-items.md
│   │   ├── core-disable-author-edit.md
│   │   ├── core-content-duplication.md
│   │   ├── core-public-post-preview.md
│   │   ├── core-auto-featured-image.md
│   │   ├── core-classic-feedback.md
│   │   ├── core-disable-scheduled-deletion.md
│   │   ├── core-disable-comments.md
│   │   ├── core-allow-duplicate-comments.md
│   │   ├── core-disable-link-in-comments.md
│   │   ├── core-remove-comment-urls.md
│   │   ├── core-html5-comment-support.md
│   │   ├── core-tags-no-comma-shortcode.md
│   │   ├── core-rm-excerpt-shortcode.md
│   │   ├── core-time-format-conversion.md
│   │   ├── core-currency-converter.md
│   │   ├── core-nofollow-external-links.md
│   │   ├── core-nofollow-post-types.md
│   │   ├── core-disable-core-sitemaps.md
│   │   ├── core-exclude-noindex-from-search.md
│   │   └── core-search-engine-visibility-status.md
│   ├── bricks.md              # Bricks tab index
│   ├── bricks/                 # Bricks tab docs (10 files)
│   │   ├── bricks-ai-builder.md
│   │   ├── bricks-status.md
│   │   ├── bricks-setup.md
│   │   ├── bricks-ui-improvements.md
│   │   ├── bricks-elements-overview.md
│   │   ├── bricks-dynamic-data-overview.md
│   │   ├── bricks-conditions-overview.md
│   │   ├── bricks-interactions-overview.md
│   │   ├── bricks-optimization.md
│   │   └── bricks-import-export.md
│   ├── woocommerce.md          # WooCommerce tab index
│   ├── woocommerce/            # WooCommerce tab docs (50 files)
│   │   ├── woocommerce-product-swatches.md
│   │   ├── woocommerce-customize-add-to-cart-button.md
│   │   ├── woocommerce-customize-out-of-stock-button.md
│   │   ├── woocommerce-disable-product-reviews.md
│   │   ├── woocommerce-allow-duplicate-reviews.md
│   │   ├── woocommerce-show-price-savings.md
│   │   ├── woocommerce-show-percentage-off.md
│   │   ├── woocommerce-remove-clear-variation-link.md
│   │   ├── woocommerce-auto-select-first-variation.md
│   │   ├── woocommerce-disable-out-of-stock-variations.md
│   │   ├── woocommerce-update-price-on-variation.md
│   │   ├── woocommerce-hide-default-variation-price.md
│   │   ├── woocommerce-remove-company-field.md
│   │   ├── woocommerce-enable-checkout-field-placeholders.md
│   │   ├── woocommerce-enable-inline-checkout-field-validation.md
│   │   ├── woocommerce-remove-order-notes.md
│   │   ├── woocommerce-show-product-images-checkout.md
│   │   ├── woocommerce-custom-order-review-heading.md
│   │   ├── woocommerce-custom-place-order-button.md
│   │   ├── woocommerce-enable-checkout-product-selector.md
│   │   ├── woocommerce-enable-woocommerce-direct-checkout.md
│   │   ├── woocommerce-enable-thank-you-page-link-orders.md
│   │   ├── woocommerce-enable-custom-order-status.md
│   │   ├── woocommerce-enable-custom-order-columns.md
│   │   ├── woocommerce-enable-woocommerce-auto-completion.md
│   │   ├── woocommerce-enable-coupon-max-discount.md
│   │   ├── woocommerce-enable-auto-apply-coupons.md
│   │   ├── woocommerce-enable-url-coupons.md
│   │   ├── woocommerce-enable-user-role-restrictions.md
│   │   ├── woocommerce-enable-bogo-deals.md
│   │   ├── woocommerce-enable-first-time-customer-coupons.md
│   │   ├── woocommerce-enable-single-coupon-restriction.md
│   │   ├── woocommerce-remove-woocommerce-display-name-option.md
│   │   ├── woocommerce-remove-order-number-column.md
│   │   ├── woocommerce-disable-woocommerce-scripts.md
│   │   ├── woocommerce-disable-woocommerce-cart-fragmentation.md
│   │   ├── woocommerce-disable-woocommerce-status-meta-box.md
│   │   ├── woocommerce-disable-woocommerce-admin-features.md
│   │   ├── woocommerce-disable-marketplace-suggestions.md
│   │   ├── woocommerce-disable-woocommerce-blocks-styles.md
│   │   ├── woocommerce-disable-woocommerce-widgets.md
│   │   ├── woocommerce-remove-woocommerce-connect-store-notice.md
│   │   ├── woocommerce-remove-all-woocommerce-notices.md
│   │   ├── woocommerce-redirect-empty-cart.md
│   │   ├── woocommerce-redirect-logged-in-users-from-login.md
│   │   ├── woocommerce-redirect-to-login-after-logout.md
│   │   ├── woocommerce-enable-redirect-my-account.md
│   │   ├── woocommerce-disable-woocommerce-emails.md
│   │   ├── woocommerce-allow-reset-password-email.md
│   │   └── woocommerce-product-price-history.md
│   ├── security.md             # Security tab index
│   ├── security/               # Security tab docs (39 files)
│   │   ├── security-custom-login-url.md
│   │   ├── security-login-lockdown.md
│   │   ├── security-cloudflare-turnstile.md
│   │   ├── security-math-captcha.md
│   │   ├── security-auto-logout.md
│   │   ├── security-email-phone-protection.md
│   │   ├── security-remove-rest-api-links.md
│   │   ├── security-disable-user-enumeration.md
│   │   ├── security-hide-remember-me.md
│   │   ├── security-disable-htaccess-file-access.md
│   │   ├── security-disallow-file-mods.md
│   │   ├── security-disable-xmlrpc.md
│   │   ├── security-2fa-totp.md
│   │   ├── security-2fa-email.md
│   │   ├── security-2fa-trusted-devices.md
│   │   ├── security-2fa-rate-limiting.md
│   │   ├── security-site-wide-password.md
│   │   ├── security-ai-bot-blocking.md
│   │   ├── security-spam-comment-protection.md
│   │   ├── security-post-access-restriction.md
│   │   ├── security-disable-text-selection.md
│   │   ├── security-disable-right-click.md
│   │   ├── security-disable-view-source.md
│   │   ├── security-disable-inspect-element.md
│   │   ├── security-disable-copy-paste.md
│   │   ├── security-disable-select-all.md
│   │   ├── security-disable-save.md
│   │   ├── security-disable-print.md
│   │   ├── security-disable-image-drag.md
│   │   ├── security-disable-safari-reader.md
│   │   ├── security-protection-for-admin.md
│   │   ├── security-stay-logged-in.md
│   │   ├── security-auto-check-remember-me.md
│   │   ├── security-staging-protection.md
│   │   ├── security-http-auth.md
│   │   ├── security-allow-performance-tools.md
│   │   ├── security-allow-dev-endpoints.md
│   │   └── security-staging-indicator.md
│   ├── interface.md            # Interface tab index
│   ├── interface/              # Interface tab docs (18 files)
│   │   ├── interface-folder-manager.md
│   │   ├── interface-folder-download.md
│   │   ├── interface-folder-duplication.md
│   │   ├── interface-gallery-shortcode.md
│   │   ├── interface-quick-inspect.md
│   │   ├── interface-admin-notices-manager.md
│   │   ├── interface-form-desk.md
│   │   ├── interface-preloader.md
│   │   ├── interface-preloader-bricks.md
│   │   ├── interface-laser-loader.md
│   │   ├── interface-laser-loader-bricks.md
│   │   ├── interface-page-transitions.md
│   │   ├── interface-shared-element-transitions.md
│   │   ├── interface-reduced-motion.md
│   │   ├── interface-transitions-admin.md
│   │   ├── interface-admin-bar-bottom.md
│   │   ├── interface-admin-menu-manager.md
│   │   └── interface-top-toolbar-manager.md
│   ├── performance.md          # Performance tab index
│   ├── performance/            # Performance tab docs (48 files)
│   │   ├── performance-perf-force-https.md
│   │   ├── performance-perf-disable-all-updates.md
│   │   ├── performance-perf-disable-search.md
│   │   ├── performance-perf-disable-google-fonts.md
│   │   ├── performance-perf-disable-font-library.md
│   │   ├── performance-perf-disable-emojis.md
│   │   ├── performance-perf-disable-dashicons.md
│   │   ├── performance-perf-disable-embeds.md
│   │   ├── performance-perf-remove-jquery-migrate.md
│   │   ├── performance-perf-disable-responsive-images.md
│   │   ├── performance-perf-disable-google-maps.md
│   │   ├── performance-perf-remove-rsd-link.md
│   │   ├── performance-perf-remove-shortlink.md
│   │   ├── performance-perf-disable-rss-feeds.md
│   │   ├── performance-perf-remove-rss-feed-links.md
│   │   ├── performance-perf-disable-self-pingbacks.md
│   │   ├── performance-perf-disable-year-month-folders.md
│   │   ├── performance-perf-enable-classic-widgets.md
│   │   ├── performance-perf-secure-downloads.md
│   │   ├── performance-perf-image-converter.md
│   │   ├── performance-perf-unused-media.md
│   │   ├── performance-perf-missing-media.md
│   │   ├── performance-perf-media-trash.md
│   │   ├── performance-perf-delete-image-sizes.md
│   │   ├── performance-perf-media-replace.md
│   │   ├── performance-perf-svg-support.md
│   │   ├── performance-perf-svg-sanitization.md
│   │   ├── performance-perf-bulk-media-download.md
│   │   ├── performance-perf-auto-resize-images.md
│   │   ├── performance-perf-skip-smaller-images.md
│   │   ├── performance-perf-media-file-renaming.md
│   │   ├── performance-perf-media-duplicator.md
│   │   ├── performance-perf-media-infinite-scroll.md
│   │   ├── performance-perf-media-list-view.md
│   │   ├── performance-perf-clean-filenames.md
│   │   ├── performance-perf-disable-image-sizes.md
│   │   ├── performance-perf-disable-big-image-threshold.md
│   │   ├── performance-perf-cdn-rewrite.md
│   │   ├── performance-perf-cdn-disable-admin.md
│   │   ├── performance-perf-assets-manager.md
│   │   ├── performance-perf-disable-emoji-assets.md
│   │   ├── performance-perf-assets-manager-admin.md
│   │   ├── performance-perf-show-non-loaded-assets.md
│   │   ├── performance-perf-hide-assets-manager-panel.md
│   │   ├── performance-perf-show-frontend-icon.md
│   │   ├── performance-perf-lazy-loading.md
│   │   ├── performance-perf-monks-preload.md
│   │   └── performance-perf-selective-media-preload.md
│   ├── white-label.md          # White Label tab index
│   ├── white-label/            # White Label tab docs (18 files)
│   │   ├── white-label-wl-admin-greeting.md
│   │   ├── white-label-wl-admin-footer.md
│   │   ├── white-label-wl-admin-logo.md
│   │   ├── white-label-wl-remove-dashboard-widgets.md
│   │   ├── white-label-wl-remove-footer-text.md
│   │   ├── white-label-wl-hide-version.md
│   │   ├── white-label-wl-blank-favicon.md
│   │   ├── white-label-wl-disable-admin-email-check.md
│   │   ├── white-label-wl-remove-help-tabs.md
│   │   ├── white-label-wl-clean-head-tags.md
│   │   ├── white-label-wl-login-customization.md
│   │   ├── white-label-wl-login-logo.md
│   │   ├── white-label-wl-login-form-styling.md
│   │   ├── white-label-wl-login-nav-styling.md
│   │   ├── white-label-wl-hide-back-link.md
│   │   ├── white-label-wl-login-notices-styling.md
│   │   ├── white-label-wl-disable-language-dropdown.md
│   │   └── white-label-wl-quick-post-nav.md
│   ├── options.md              # Options tab index
│   ├── options/                # Options tab docs (7 files)
│   │   ├── options-opt-environment.md
│   │   ├── options-opt-import.md
│   │   ├── options-opt-export.md
│   │   ├── options-opt-reset.md
│   │   ├── options-opt-uninstall.md
│   │   ├── options-opt-wp-reset.md
│   │   └── options-opt-license.md
├── comparison/                 # Competitor comparison pages
│   ├── classic-monks-vs-ase.md        # Parity comparison
│   ├── classic-monks-features-ase-does-not-have.md  # CM-only conversion
│   ├── README.md
│   └── cm-vs-ase--internal/           # Internal evidence and roadmaps
├── installation/               # Setup, activation, first-time config
│   └── getting-started.md
├── tips/                       # Best practices, comparisons, optimization
│   └── ...
├── troubleshooting/            # Common issues and fixes
│   └── ...
└── updates/                    # Changelog, feature requests
    └── changelog.md
```

## Categories

| Category | Articles | Purpose |
|----------|----------|---------|
| **general/ai/** | AI tab features | AI Agent, Provider, Tools, Advanced, Status |
| **general/core/** | Core tab features | Setup, File Management, Content, Gutenberg, Users, Plugins, Logs |
| **general/bricks/** | Bricks tab features | Setup, UI Improvements, Elements, Dynamic Data, Conditions, Interactions, Optimization, Import/Export |
| **general/email/** | Email tab features | SMTP, Logging, Notifications, WooCommerce email control |
| **general/woocommerce/** | WooCommerce tab features | Swatches, Single Product, Checkout, One Click Checkout, Orders, Coupons, My Account, Optimization, Redirection, Email |
| **general/security/** | Security tab features | Custom Login URL, Login Lockdown, Captcha, 2FA, Content Protection, Stay Logged In, Staging Protection |
| **general/interface/** | Interface tab features | Folder Manager, Admin Notices, Form Desk, Preloader, Laser Loader, Page Transitions, Menu management (Admin Menu, Top Toolbar, Quick Post Nav), Admin Menu Manager |
| **general/performance/** | Performance tab features | WP Optimizations, Media, CDN, Assets Manager, Lazy Loading, Preloading |
| **general/white-label/** | White Label tab features | Admin branding, Login page customization |
| **general/options/** | Options tab features | Environment, Import/Export, Reset, Uninstall, License |
| **Installation** | Setup guides | First-time install, activation |
| **Comparison** | Competitor comparisons | Classic Monks vs ASE: parity and CM-only conversion |
| **Tips** | Best practices | Optimization advice |
| **Troubleshooting** | Issue fixes | Common errors |
| **Updates** | Changelog | Version history |

## Writing a New Article

1. Copy `templates/article-template.md`
2. Save it in the appropriate tab folder (e.g., `general/ai/` for AI features, `general/core/` for Core features, `general/email/` for Email features)
3. Fill in the YAML frontmatter with all 7 required fields: `title`, `slug`, `description`, `last_updated`, `author`, `reading_time`, `canonical`. Use a flat slug (no tab prefix), e.g. `advanced-plugin-manager` not `core/advanced-plugin-manager`
4. Follow the `templates/style-guide.md` conventions, including the H1 brand-placement rule and the blocking em-dash pre-save check
5. Name the file: `kebab-case-feature-name.md`
6. Update this README with a link to the new article

## Naming Convention

- File names: `kebab-case-feature-name.md` (tab prefix optional in filenames, e.g. `core-quick-wp-setup.md`)
- Titles: `How to [Action] in WordPress` (brand in SEO title, not in H1)
- Slug (frontmatter `slug:` + canonical URL): flat, no tab prefix — `advanced-plugin-manager` not `core/advanced-plugin-manager`
- Categories match the folder they live in

## Linking Between Articles

Use relative paths:
```markdown
See the [Code Manager guide](general/code-manager.md) for more details.
```

## Maintenance

- Review articles quarterly for accuracy
- Update when features change (check CHANGELOG.md)
- Archive deprecated articles to `docs/archive/`
