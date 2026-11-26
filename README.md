# Henley Legal — Camberwell

Website for **Henley Legal**, an independent law practice and Public Notary at
1378A Toorak Road, Camberwell VIC 3124. Practising on Toorak Road since April 2006.

- **Live site:** https://cremasc0.github.io/henley-legal-camberwell/

## What's in this repo

The site is a single, self-contained HTML file — no build step, no package manager,
no framework, no dependencies to install.

```
.
├── index.html    # The entire site: markup, styles and behaviour
├── .nojekyll     # Tells GitHub Pages to serve files as-is
├── .gitignore
└── README.md
```

### `index.html`

Everything ships in this one file:

| Part | Detail |
| --- | --- |
| Styles | Inline `<style>` block, organised into numbered sections with CSS custom properties for the palette |
| Behaviour | One inline `<script>` for the notary checklist (Form HL-01) and the appointment enquiry |
| Fonts | Google Fonts — **Newsreader** (headings) and **IBM Plex Sans** (body) |
| Icon | SVG favicon inlined as a `data:` URI — no separate asset |
| Images | None — all artwork is inline SVG |

Page sections:

1. **Hero** — practice introduction and contact ledger
2. **Public notary** — Form HL-01 appointment checklist, with the DFAT Apostille note
3. **What we act on** — practice areas
4. **Plain advice and clear costs** — how the practice works
5. **Book an appointment** — contact details and enquiry

Practice areas covered: public notary services, property and conveyancing, business and
commercial law, wills/estates/trusts/superannuation, and commercial and property disputes.

## Running locally

Because it is a single static file, you can simply open `index.html` in a browser.

To preview it over HTTP instead (closer to production):

```bash
python -m http.server 8000
# then visit http://localhost:8000
```

Any static file server works — the file has no server-side component.

## Deployment

Hosted with **GitHub Pages** from the `main` branch, repository root. Because the entry
point is named `index.html`, the site is served at the repository's Pages URL with no
configuration beyond enabling Pages.

Any push to `main` republishes the site.

## Contact

| | |
| --- | --- |
| Address | 1378A Toorak Road, Camberwell VIC 3124 |
| Phone | (03) 9889 7988 |
| Email | mail@henleylegal.com |
| ABN | 46 109 556 149 |

## Notes

- Content, branding and copy belong to Henley Legal. This repository is not licensed for
  reuse by third parties.
- The page is a static front end only. The appointment enquiry is handled client-side; it
  does not post to a backend, so connecting it to a form endpoint is required before it can
  deliver mail.
