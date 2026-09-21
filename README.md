# digidev-site

The DigiDev website: one page for the brand, one page per plugin. Plain HTML and CSS, no build
step, no dependencies, served by GitHub Pages.

## Structure

```
index.html                     Home: what DigiDev is, the three rules, the plugin list
404.html                       Not-found page (uses absolute /assets paths, see below)
CNAME                          Custom domain for GitHub Pages
sitemap.xml                    The three pages, by hand; add a line when a page is added
robots.txt                     Allows everything and points at the sitemap
.nojekyll                      Serve the files as they are, skip Jekyll
assets/css/site.css            The whole stylesheet
assets/fonts/                  Space Grotesk, self-hosted, with its OFL licence
assets/img/                    Images, currently empty; the logo is inline SVG
plugins/<slug>/index.html      One page per plugin
privacy/index.html             Privacy statement, linked from every footer
docs/                          Notes that are not part of the site
```

The font is served from `assets/fonts/` on purpose: the site makes no request to any other
company, so there is nothing to disclose and no consent to ask. Do not replace it with a font CDN.
Two `woff2` files cover weights 300 to 700, one for latin and one for latin-ext; the `@font-face`
rules sit at the top of the stylesheet, and `OFL.txt` must stay next to them.

The logo is an inline SVG in each page's `<header>` and a data URI in the favicon `<link>`. There
is no image file to lose.

## Publishing

1. The repository is `RobinDeCroock/digidev-site`, public, with `origin` already set.
2. Settings → Pages → Source: *Deploy from a branch*, branch `main`, folder `/ (root)`.
3. Settings → Pages → Custom domain: `digital-development.be`, then tick *Enforce HTTPS* once the
   certificate is issued. This can take up to an hour.

DNS for the apex domain, at whoever hosts digital-development.be:

| Type | Name | Value |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | `robindecroock.github.io` |

Those four addresses are GitHub's published Pages servers; check them against GitHub's
documentation before relying on them.

Mail for the domain is at one.com, and the records that prove it are separate from the ones above:

| Type | Name | Value |
|---|---|---|
| TXT | @ | `v=spf1 include:_spf.one.com ~all` |
| TXT | _dmarc | `v=DMARC1; p=none; rua=mailto:info@digital-development.be` |

Without these, anyone can send mail that appears to come from `info@digital-development.be`, and
mail that really is from that address is more likely to be filtered as spam. Leave DMARC at
`p=none` until the reports show that everything you send passes, then move it to `p=quarantine`.
DKIM is signed by one.com itself and is switched on in their control panel, not here. The
`MS=` and `google-site-verification=` TXT records already on the domain are verification tokens for
other services; leave them alone, they do not affect mail.

## Paths

Pages link to each other with relative paths, so the site works both at the custom domain and at
`<username>.github.io/digidev-site` while the DNS is still propagating. `404.html` is the one
exception: GitHub serves it for any missing URL at any depth, so it needs absolute paths and
therefore only renders correctly once the site is at the domain root. Delete `CNAME` and the 404
page loses its styling; nothing else breaks.

## Still to fill in

Search the HTML for `TODO`. Currently:

- `WORDPRESS-ORG-USERNAME` in `index.html`, in the profile link that stays commented out until the
  first plugin is published. WordPress.org is a separate account, so it is not necessarily the
  GitHub name.
- Plugin status is hard-coded as "In development" in two places; change both when it goes live.
- The WordPress.org support forum link on the plugin page, once the plugin is published. Until
  then the "Report an issue" button is a mailto, on purpose.

## Adding a plugin

Copy `plugins/one-folder-gallery/index.html` to `plugins/<new-slug>/index.html` and add an entry to
the plugin list in `index.html`. Keep the "it can reach / it can never reach" ledger: it is the
argument the whole site makes.

If a plugin ever gets a paid add-on, it stays a separate product on its own page section, sold
through Gumroad, with a `<span class="price">` badge in the list on the home page. The free plugin
never loses features to it.
