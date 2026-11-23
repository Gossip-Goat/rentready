# RentReady

A bond-back app for Australian renters. It helps tenants:

- **Inspect** a rental room by room at move-in and move-out (Clean / Undamaged / Working), with photos stamped with their capture time and a SHA-256 fingerprint.
- **Compare** move-in and move-out, highlighting what got worse and what was already there.
- **Check a bond claim** item by item against the move-in record, fair wear and tear, item age and evidence rules, then generate a reply letter.
- **Check a rent increase** against the state's notice and frequency rules.

Covers all eight states and territories. See [RULES.md](RULES.md) for the rules used, their sources, and what still needs checking.

## Files

- `index.html`: landing page with a waitlist and a $1 pre-order test.
- `app.html`: the app itself.
- `RULES.md`: the tenancy rules used, with sources.

## Running it

No build step. Open the files in a browser, or serve the folder:

```
npx serve .
```

Data is stored in the browser's IndexedDB on the user's device only. Nothing is sent to a server.

Export (reports, letters, backups) uses the claude.ai artifact `downloads` capability. Opened in a normal browser, exports fall back to a standard file download.

## Status

Prototype. Rules are general information, not legal advice, and need a lawyer's review before launch. Next steps: connect the waitlist and pre-order (below), run the demand test, then a React Native or Flutter app.

## Launching the landing page

1. Create a form backend that accepts a JSON POST (for example Formspree or Tally) and paste its URL into `WAITLIST_ENDPOINT` in `index.html`.
2. Create a Stripe Payment Link for the $1 refundable pre-order and paste it into `PREORDER_URL`.
3. Turn on GitHub Pages (Settings, Pages, deploy from the `main` branch). Note that Pages on a private repo needs a paid GitHub plan; otherwise make the repo public or use Netlify or Vercel.

The plan's success bar: 500 waitlist sign-ups and at least 5% pre-ordering.
