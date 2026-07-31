# ASE + Classic Monks: can you drop ASE?

Short answer: **sometimes, not automatically**.

Classic Monks covers a lot of the ASE territory: Post Type Switcher, duplication, Gutenberg and comments controls, XML-RPC, revisions, Heartbeat, SVG support, login URL, admin menus, 2FA, CAPTCHA, SMTP, redirects, media tools, and more.

But ASE still has important gaps:

- Custom Content Types, including CPTs, taxonomies, fields, and options pages. A full-featured external CM plugin is planned and awaiting WordPress.org repository approval.
- Form Builder
- Full Site Backup and Migration
- General File Manager
- Detailed Redirect Manager rules
- Some admin columns, media categories, login, role, and WordPress utility modules

CM also brings a different layer of value: AI, Bricks tools, WooCommerce, Performance, Quick Setup, Image Converter, Folder Manager, security breadth, and White Label. Those are not ASE replacements. They are CM-only reasons to use CM.

My advice: inventory the ASE modules actually enabled on each site, map them against the full matrix, and test on staging. Keep ASE where the site depends on a `No`, or where a `Partial` match misses a workflow you cannot lose.

If you run both, let one plugin own each concern. Do not run two SMTP systems, login limiters, 2FA tools, CAPTCHA providers, redirect managers, or code managers on the same site without a very specific reason.

[Full comparison: ASE vs Classic Monks](https://classicmonks.com/docs/classic-monks-vs-ase/)

What ASE modules are you actually using? Paste the enabled list. That is more useful than arguing from headline feature counts.
