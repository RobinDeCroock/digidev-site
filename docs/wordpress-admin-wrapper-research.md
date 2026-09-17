> Archived. This repository is now the DigiDev website. The admin wrapper plugin was dropped
> on 2026-09-17 on the evidence below.

# Phase 1 — market research

Data pulled from the WordPress.org plugin API on 2026-09-17. Installs are the directory's
order-of-magnitude buckets, not exact numbers.

## The incumbents

| Plugin | Active installs | Rating | Last update | What it actually does |
|---|---|---|---|---|
| Admin Menu Editor | 300,000 | 92% (312) | 2026-08-19 | Reorder, rename, hide menu items per role |
| White Label CMS | 200,000 | 94% (114) | 2026-07-09 | Branding, dashboard widgets, menu hiding per role |
| Adminimize | 200,000 | 94% (254) | 2026-06-10 | Hide admin UI parts per role, very granular |
| Admin and Site Enhancements (ASE) | 200,000 | 100% (422) | 2026-09 | All-in-one: menu editor, dashboard widgets, notices, and ~40 more |
| Ultimate Dashboard | 60,000 | 92% (114) | 2026-06-06 | Replace dashboard widgets with custom tiles |
| WP Custom Admin Interface | 30,000 | 94% (160) | 2026-02-10 | Drag-and-drop menu + toolbar, colour schemes |
| Branda | 20,000 | 90% (30) | 2026-08-19 | White labelling, login pages |
| Adminify | 6,000 | 86% (109) | 2026-09-17 | White label, menu editor, login customizer |
| Client Dash | closed | — | — | Removed from the directory |

ASE is the one to beat: free, all-in-one, 100% rating over 422 ratings, actively maintained.

## What none of them do

All of them subtract from wp-admin: hide, rename, restyle. None replaces the screens where the
work happens. Hide "Posts" and the user still lands in the stock list table and then in Gutenberg.
The learning curve lives in the editor and in the concepts (post vs page vs template vs block),
not in the sidebar. The sidebar is the cheap part of the problem, which is why five plugins solve
it and nobody solves the rest.

## Recurring complaints (White Label CMS and Ultimate Dashboard support forums)

- **Leaks.** "Elementor Template not hidden", "Gravity Forms won't show up", "Motors Plugin not
  showing up on menu", "Items still available from Admin Bar". Every plugin the site owner installs
  reopens the hole, because these tools work from a deny-list of known menu items.
- **Lock-outs.** "No admin access. The setup admin is no longer available.", "Redirect loop on
  /wp-admin/ when White Label CMS is enabled."
- **Roles.** "Problems with multiple roles", "Granular control based on user roles."
- **Fragility.** Ultimate Dashboard's forum shows fatal errors, memory exhaustion in its menu
  editor, an XSS advisory, and multisite breakage.

Deny-by-default ("hide any menu that appears later") already exists in WPFront User Role Editor Pro
and Admin Menu Editor Pro, so the leak complaint is served by paid tiers, not unserved.

## Core is moving

WordPress 7.0 and 7.1 ship a design system for admin components: admin colour theming, roundness
and cursor tokens, the Site Editor shell following the admin colour scheme. Admin redesign is an
active core project. Anything built on custom admin CSS inherits that churn.

## Conclusion

Recommend dropping the general-purpose admin wrapper. The category is crowded, well served and
free at the top, and the part of the problem that is actually worth solving (the editing screens)
is not reachable with `admin_menu` and CSS.

## Not checked

- 2- and 3-star review text for ASE and Admin Menu Editor (WordPress.org renders it behind filters
  this research did not open).
- Whether ASE's menu editor has deny-by-default.
- Current WordPress.org plugin review queue time.
