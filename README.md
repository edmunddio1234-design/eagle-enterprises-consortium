# Eagle Enterprises Consortium, L3C — Website

Static site for **Eagle Enterprises Consortium, L3C (EEC)** — the umbrella entity of the
Lighthouse rural-veterans ecosystem in Louisiana. Same architecture and design DNA as the main
Lighthouse Rural Communities repo, re-tokened to EEC's navy/eagle-gold identity.

## Stack

Plain HTML + CSS + vanilla JS. No build step. Deploy the folder as-is.

- `css/styles.css` — full design system (adapted from the Lighthouse base). Tokens:
  navy-900 `#101A38`, navy-700 `#1C2E5E` (text-safe on white), steel-500 `#2F4A8F`,
  gold-500 `#F4B41A` (accents/borders only — never text on white), gold-600 `#9A6A00`
  (text-safe gold), green-700 `#1B6B3A` support. WCAG 2.2 AA throughout.
- `js/main.js` — mobile nav toggle + form handler (POST `/api/submit` with mailto fallback
  to `connect@eagleenterprisesconsortiuml3c.org`).
- `assets/logo-mark.svg` — eagle chevron rising over three consortium bars, navy + gold.
- 10 pages: index, about, m-toc, net-wircing, seismic, bootcamps, rdic, services,
  ecosystem, contact. Plus `sitemap.xml`, `robots.txt`, `vercel.json` (`cleanUrls: true`).
- `build_pages.py` — the one-shot generator used to produce the pages. Safe to delete;
  pages are committed as plain HTML and can be edited directly.

## Deploy (GitHub → Vercel)

1. Create a GitHub repo (e.g. `eagle-enterprises-consortium`) and push this folder's contents
   to the repo root.
2. In Vercel: **Add New → Project → Import** the repo. Framework preset: **Other** (static).
   No build command, no output directory — deploy the root.
3. Vercel serves it at `https://www.eagleenterprisesconsortiuml3c.org` (the placeholder URL
   used in canonicals/sitemap). `cleanUrls: true` makes `/about` serve `about.html`.

### Wiring the forms to Supabase later (optional)

The contact form POSTs JSON to `/api/submit` exactly like the main Lighthouse repo. To activate:
copy the main repo's `api/submit.js` serverless function into an `api/` folder here and set the
same Vercel environment variables (`SUPABASE_URL`, `SUPABASE_SERVICE_ROLE_KEY` — match the main
repo's names). Until then, the built-in fallback opens the visitor's email app pre-addressed to
the fallback address, so no submission is lost.

## Placeholders — owner (Sonny/Fredell) to confirm

- **Domain**: `https://www.eagleenterprisesconsortiuml3c.org` is a placeholder. When the real
  domain is purchased, update: every page's `<link rel="canonical">` and `og:url`,
  `sitemap.xml`, and `robots.txt`.
- **Email**: `connect@eagleenterprisesconsortiuml3c.org` is a **to-be-created** address (it is
  the JS fallback email and appears on the Contact page and footer). Create the mailbox or
  swap in a live address in `js/main.js` (fallback default), `contact.html`, and the footer
  of every page.
- **Tier pricing** on `services.html` is intentionally unpriced ("Entry/Standard/Family/
  Premium") — set dollar amounts at platform launch.
- **Sibling site URLs** in footers and `ecosystem.html` are placeholders until those sites
  have final domains: RV3 `https://www.rv3vanguardofvalor.org`, Guardian Angels
  `https://www.guardianangelsenterprises.org`.
- **Registered office** shown as 16458 Highway 38, Greensburg, LA 70441-3602 (from the EEC L3C
  strategic plan). Confirm this is the address to publish.
- **Phone** (504) 657-7594 — shared ecosystem number; confirm routing.
- **Stats**: index/about use L-01 research figures (39%, 65% vs 46%, 8% of 2023 new
  businesses); ecosystem.html uses the VI-PAR pilot **demo** figures (312/184/4/8), labeled
  as demo data on the page.
