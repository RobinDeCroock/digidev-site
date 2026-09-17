# DigiDev site

My personal context, the side-business goal and the shared WordPress rules are in
`~/.claude/CLAUDE.md`. This file only covers what is specific to this repository.

## What this is

The public website for DigiDev: one home page and one page per plugin, published with GitHub Pages
at digital-development.be. Plain HTML and CSS. No build step, no framework, no dependencies, no
JavaScript unless a page genuinely cannot work without it.

`README.md` has the structure, the publishing steps and the DNS records.

This repository used to hold a plan for a WordPress admin wrapper plugin. That idea was dropped
after research; the reasoning is kept in `docs/wordpress-admin-wrapper-research.md` so it does not
get proposed again.

## The argument the site makes

Every plugin does one thing and asks for the narrowest permission the platform offers. That claim
is the product, so it leads: the home page states it, and every plugin page carries the "it can
reach / it can never reach" ledger. Do not bury it under feature lists.

Copy is written for a site owner who is not a developer. Plain words, no marketing adjectives, no
exclamation marks. Say what a thing does, then say what it refuses to do.

## Design

Tokens live at the top of `assets/css/site.css` and come from the brand: `#F4F5F9` for the page,
white for raised panels, navy `#101D42` for headings, body text and the band, `#C9CDF9` for
secondary text on the band and for the price badge. Secondary text on paper is muted navy
(`--ink-soft`, `--ink-faint`), not a brand colour, and every one of them clears 4.5:1.
Space Grotesk throughout, loaded from Google Fonts — allowed here, never inside a WordPress admin.

Blue `#232ED1` means one thing only: you can act on this. Links, buttons and the small section
labels. Do not use it for a surface — white on saturated blue over a full-width band vibrates,
which is why the band is navy. `#7C84F2` is the accent for dark surfaces, so it appears on the
band and in the favicon tile, never on paper, where it fails contrast.

The site is light and has no dark mode. Do not add one on a whim; it would mean reworking every
token. The page stays neutral so the navy band is the only dark block: one strong surface per
page, nothing else competing with it.

Reuse the existing components (`.ledger`, `.band`, `.claims`, `.plugin`, `.steps`, `.codes`,
`.note`, `.facts`) before inventing new ones. One accent per page at most.

## Rules

- Relative paths between pages, so the site also works at `<username>.github.io/digidev-site`.
  `404.html` is the exception and uses absolute paths, because GitHub serves it from any depth.
- No analytics, no tracking, no cookies, no embedded third-party widgets. Google Fonts is the only
  external request, and it is a deliberate one.
- Do not invent facts about a plugin. Versions, permissions, shortcodes and settings on a plugin
  page must match what the plugin actually does; check its repository or its settings screen.
- Do not claim a plugin is on WordPress.org before it is.
- The plugin repositories are private and are expected to stay private, so the site never promises
  source on GitHub. What makes a plugin checkable is that WordPress.org publishes the PHP that
  runs; write the claim that way. Support is email until a plugin has a WordPress.org support
  forum. The GitHub link in the contact list is a profile link and nothing more.
- Placeholders are written in capitals (`GITHUB-USERNAME`, `KOFI-NAME`) and listed in the README.
  Never guess a real URL to fill one in.

## Money

Plugins are free. Donations are one-off tips through Ko-fi with nothing in return: no tiers, no
donor-only features, no priority support, because a perk turns a gift into a sale with EU VAT
obligations.

A paid add-on, if one is ever justified by demand, is a separate plugin sold through Gumroad as
merchant of record, hosted outside WordPress.org, at a one-off price. On this site it gets a
section on its own plugin's page and a `.price` badge in the home page list. The free plugin never
loses a feature to make room for it.

## Before calling a change done

1. Open every changed page in a browser at phone width and at desktop width.
2. Tab through it: every link and button needs a visible focus ring.
3. Check the links, including the relative ones from a plugin page back to the home page.
4. Confirm no `TODO` or capitalised placeholder is left on a page that is going live.
