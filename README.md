# Henley Legal — Camberwell

Website for **Henley Legal**, an independent law practice and Public Notary at
1378A Toorak Road, Camberwell VIC 3124. Practising on Toorak Road since April 2006.

- **Live site:** https://cremasc0.github.io/henley-legal-camberwell/

> **This deployment is a design demonstration, not a live site.** It is not operated
> by, endorsed by, or affiliated with Henley Legal. The name, address, phone, email and
> ABN are used for illustration while pitching the design. Watermarks, a `noindex`
> directive, a printed specimen mark and a footer disclaimer are in place to make that
> clear. See [Demo mode](#demo-mode) for how to strip them out.

## Demo mode

The preview is marked in four places, each tagged `[DEMO LAYER` so `grep` finds them all:

| Where | What it does |
| --- | --- |
| `<head>` | `[DEMO]` title prefix; `noindex, nofollow, noarchive, nosnippet, noimageindex` |
| Banner | Sticky oxblood bar above the header — stays on screen at every scroll position, so it lands in any screenshot |
| Overlay | Fixed, tiled `DEMO / DESIGN PREVIEW` watermark at 5.5% opacity, `pointer-events: none` so the form stays fully usable |
| Footer | Disclaimer naming the demo nature and the illustrative contact details |

Two further safeguards:

- **Print.** The stylesheet isolates Form HL-01, so a printed or PDF'd copy is the most
  convincing "official" artifact this preview can produce. Printing therefore shows the
  banner, a `SPECIMEN ONLY — NOT A VALID HENLEY LEGAL FORM` strip across the sheet, and
  the watermark.
- **Logo export.** The footer's "Download vector logo (.svg)" button is hidden, so the
  preview does not hand the practice's vector logo to anyone who clicks it.

### Removing demo mode for production

1. Delete every block containing `[DEMO LAYER` (four in `index.html`).
2. Delete the `<meta name="robots" ...>` tag and the `[DEMO]` prefix in `<title>`.
3. Delete the `.logo-download-btn { display: none; }` rule to restore logo export.
4. Replace the illustrative contact details with the client's confirmed details.

Note the deliberate omission of a `robots.txt` `Disallow`. A blocked crawler can never
read the `noindex` tag, so the URL can still be indexed from inbound links; leaving the
crawl open is what makes `noindex` effective. If the preview must be private rather than
merely unindexed, host it behind authentication instead — GitHub Pages cannot do that.

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
