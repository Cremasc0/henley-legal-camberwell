# Henley Legal — Camberwell

Website for **Henley Legal**, an independent law practice and Public Notary at
1378A Toorak Road, Camberwell VIC 3124. Practising on Toorak Road since April 2006.

- **Live site:** https://cremasc0.github.io/henley-legal-camberwell/

> **This deployment is a design demonstration, not a live site.** It is not operated
> by, endorsed by, or affiliated with Henley Legal. The practice information shown is
> drawn from the practice's publicly listed website, which the banner and footer both
> state. Watermarks, a `noindex` directive, a printed specimen mark and a footer
> disclaimer are in place to make the demo nature clear. See [Demo mode](#demo-mode)
> for how to strip them out.

## Demo mode

The preview is marked in four places, each tagged `[DEMO LAYER` so `grep` finds them all:

| Where | What it does |
| --- | --- |
| `<head>` | `[DEMO]` title prefix; `noindex, nofollow, noarchive, nosnippet, noimageindex` |
| Banner | Sticky oxblood bar above the header. It slides out of view as you scroll down and returns when you scroll back up, so it no longer covers content permanently. A 4px threshold stops it flickering on tiny scrolls, and it always shows within 80px of the top. States that the preview uses publicly listed information from the practice's website |
| Overlay | Fixed, tiled `DEMO / DESIGN PREVIEW` watermark at 5.5% opacity, `pointer-events: none` so the form stays fully usable |
| Footer | Disclaimer naming the demo nature and the source of the practice information |

Two further safeguards:

- **Print.** The stylesheet isolates Form HL-01, so a printed or PDF'd copy is the most
  convincing "official" artifact this preview can produce. Printing therefore shows the
  banner, a `SPECIMEN ONLY — NOT A VALID HENLEY LEGAL FORM` strip across the sheet, and
  the watermark.
- **Logo export.** The footer's "Download vector logo (.svg)" button is hidden, so the
  preview does not hand the practice's vector logo to anyone who clicks it.

### Copyright position

The design is retained by its author, not signed over to the practice:

> Design preview © 2026 Jenson Cremasco. The design, code and assembly of this page are
> supplied for evaluation only. They are not licensed for use, publication or
> redistribution until an engagement is agreed in writing.

The practice's name and the factual information about the practice remain the
practice's own. Do not send a preview that asserts the practice owns the copyright in
the design.

### Removing demo mode for production

1. Delete every block containing `[DEMO LAYER` (four in `index.html`).
2. Delete the `<meta name="robots" ...>` tag and the `[DEMO]` prefix in `<title>`.
3. Delete the `.logo-download-btn { display: none; }` rule to restore logo export.
4. Replace the copyright notice, the banner text and the footer notice with the
   practice's own wording once the work is engaged.

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
3. **The firm** — admitted since 1990, business and property specialism, notary in-house
4. **What we act on** — the thirteen practice areas
5. **Accreditations** — principal, qualifications, and admissions/accreditation ledger
6. **Plain advice and clear costs** — fee assessment, rates, volume discounts, reporting
7. **Book an appointment** — contact details and enquiry
8. **Disclaimer and copyright** — general-information disclaimer and copyright position

## Content source

Copy and facts are aligned to the practice's live site at <https://henleylegal.com/>, whose
public pages are Home (*The Firm*, *Legal Costs*), Contact Us, Practice Area, Accreditations,
and Disclaimer & Copyright. The Joomla-only elements there — *Library (staff access only)*
and the *Who's Online* widget — are deliberately not reproduced.

The thirteen practice areas are taken from the live Practice Area page: Building &
Construction, Business & Commercial Law, Contract, Corporations, Equity & Trusts, Evidence,
Insolvency & Bankruptcy, Insurance, Intellectual Property, Leases & Tenancies, Litigation
Practice & Procedure, Product Liability, and Real Property.

### Details not confirmed by the live site

These appear in the demo but are **not** on the practice's current website. Confirm with the
client before sign-off:

| Detail | Status |
| --- | --- |
| `mail@henleylegal.com` | Not published on the live site; Contact Us offers only a web enquiry form |
| Opening hours (Mon–Fri, 9:00–5:00) | Not published; the live site only says staff are reachable during and after office hours |
| ABN 46 109 556 149 / ACN 109 556 149 | Not published anywhere on the live site |
| "Near Burwood Station" | Not on the live site, and the station near 1378A Toorak Road is Camberwell, not Burwood |
| "Established April 2006" | Removed. The live site says admitted to practise since **1990**; the 2006 date was unsupported |

### Claims to confirm before the site goes live

Legal advertising rules (Legal Profession Uniform Law; Australian Solicitors' Conduct Rules
r 36) make "specialist" wording sensitive, especially where accreditation has lapsed. The
preview therefore avoids asserting current specialist status:

| Claim | Position in this preview |
| --- | --- |
| "specialist law firm" | Softened to "law practice" in the hero, metadata and The Firm section |
| "Property Law Specialists" logo tagline | Shortened to "Business & Property Law" in the wordmark, aria-label and SVG export |
| "specialist accreditation" heading | Reduced to "Admissions and accreditation" |
| LIV accreditation titles | Kept verbatim, because they are the official names of the accreditations. The page footnotes them as **past** professional accreditations per the live site — the practice should confirm whether they are still current |
| "Public Notary" (hero, brand, Form HL-01) | Kept, on the basis of the 2004 appointment and 2009 fellowship on the live site. Worth confirming the appointment is **current** before publication, as the notary checklist is the centrepiece of the page |

Residual uses of the word are deliberate: the two accreditation titles, the "Accredited
Specialist logo" line naming the Law Institute of Victoria's mark, and the rate comparison
against "non-specialist" firms, which is the practice's own published claim.

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
| Principal | Henry Wong, B.Juris., LLB., GDipFin&Invest, GDipIWeb, LLM, LLM (Applied Law — Commercial Litigation) |
| Address | 1378A Toorak Road, Camberwell VIC 3124 |
| Phone | (03) 9889 7988 |
| Email | mail@henleylegal.com *(unconfirmed — see above)* |
| ABN | 46 109 556 149 *(unconfirmed — see above)* |

## Notes

- The design, code and assembly of this page are © 2026 Jenson Cremasco and are not
  licensed for use, publication or redistribution until an engagement is agreed. The
  practice's name and the factual information about the practice remain its own; see
  [Copyright position](#copyright-position).
- The page is a static front end only. The appointment enquiry is handled client-side; it
  does not post to a backend, so connecting it to a form endpoint is required before it can
  deliver mail.
