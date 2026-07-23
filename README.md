# Flag Pond Mushroom Farm — website

Single-file static site for **Flag Pond Mushroom Farm** (John Oliver · Flag Pond / Unicoi County, TN).
Fresh gourmet mushrooms — wholesale, direct to kitchens across the Tri-Cities and the Asheville corridor.

Built by **MycoAI** (Guy Stewart) · mycoai.net

---

## ⚠️ This is a PREVIEW deploy — not a public launch yet

This copy is published to GitHub Pages so it can be shown and reviewed. Two deliberate guards are on:

1. **`<meta name="robots" content="noindex, nofollow">`** in `index.html` keeps it out of Google until John approves a real launch.
2. **The order form is not wired to an inbox.** Its `action` is the placeholder `__SET_FORM_ENDPOINT__`; a built-in script catches submits and shows a friendly "ordering opens at launch" message instead of erroring.

Nothing here is John's live business presence until the go-live steps below are done.

## Go-live checklist (flip preview → real launch)

1. **Wire the order form.** GitHub Pages has no backend — use a free form relay:
   - Create a free **Formspree** form → set `<form action="https://formspree.io/f/XXXXXX" method="POST">` (replace the `__SET_FORM_ENDPOINT__` placeholder; the `data-netlify`/`bot-field` bits are Netlify-only and can be removed).
   - Point it at a **real farm inbox** (not the cold-email sending domain). Send a live test — confirm it lands.
2. **Remove the `noindex`** — delete the two preview lines above the `robots` meta in `index.html`.
3. **Custom domain + HTTPS** — follow [`flag-pond-farm/03-site/DEPLOY.md`](../Claude/flag-pond-farm/03-site/DEPLOY.md) §1, §4–§5 (`flagpondmushrooms.com`, GitHub Pages custom domain, four A records, Enforce HTTPS).
4. **Get John's written OK** to publish before it's indexed and live.

## Hard privacy rule (never break)

**John's personal cell must NEVER appear on the public site.** The "Order Line" is a marked "coming soon" placeholder. Publish a real number only if it's a **dedicated** business line John chooses to publish, and only after he says yes in writing. Pre-deploy gate — this must return nothing:

```bash
grep -R "895-4459\|14238954459" .
```

## Files

- `index.html` — the whole site (all CSS + JS inline; only external request is Google Fonts, and the page is fully legible without it).
- `.nojekyll` — tells GitHub Pages to serve the files as-is (no Jekyll build).

## Editing

It's one file. Menu, species, delivery days, and terms are all plain HTML in `index.html`. Commit to `main` and GitHub Pages redeploys in ~1 minute.

The canonical source lives in the MycoAI workspace at `flag-pond-farm/03-site/index.html`; brand rules are in `flag-pond-farm/03-site/BRAND.md`.
