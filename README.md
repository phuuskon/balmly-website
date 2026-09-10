# Balmly website

Static site for balmly.pekkahuuskonen.com. No build step, no dependencies —
plain HTML/CSS, deliberately simple, same pattern as
gigscript.pekkahuuskonen.com and chordsnap.pekkahuuskonen.com.

English-only: Balmly's market is deliberately US-only, so there is no
translation workflow (no `locales/`, no i18n JS).

## Structure

```
privacy/index.html   Privacy policy (own path /privacy/)
css/styles.css        All styles; brand tokens in :root
assets/favicon.svg    Wine lowercase-serif "b" mark with a brown dot
CNAME                 Custom domain for GitHub Pages
.nojekyll             Disable GitHub Pages Jekyll processing
```

There is no `index.html` yet. The privacy page alone satisfies the App Store
Connect requirement; a fuller marketing page can come later.

## Brand tokens

Established in the mobile app — do not invent new ones. See `:root` in
`css/styles.css`.

- Wine `#6E2A38` (primary accent), darker variant `#5A1F2C`
- Warm near-black `#2E2622` (body text)
- Cream backgrounds `#FBF7F1` / `#F8F3EC`
- Earthy brown `#8A6A4F` (secondary accent)
- Sand `#EADFCB` (borders, hairlines)
- Icon background cream `#F4EDE3`
- Headings: Lora (serif). Body/UI: Source Sans 3.

## Publishing on GitHub Pages

1. Push this repo to GitHub (e.g. `balmly-website`).
2. Repo → Settings → Pages → Source: "Deploy from a branch" → `main`, `/ (root)`.
3. Settings → Pages → Custom domain → `balmly.pekkahuuskonen.com` (reads `CNAME`).
4. DNS: under `pekkahuuskonen.com` add a CNAME record —
   Name `balmly`, Target `<github-username>.github.io`. If proxied through
   Cloudflare, set SSL/TLS to "Full" or stricter, not "Flexible".
5. Wait for DNS propagation, then tick "Enforce HTTPS" once the certificate
   is issued.

## Note on the privacy policy

Written from known facts about the project's architecture, not legal advice.
The full Terms of Service is a separate piece of work with a US attorney
(see `docs/balmly-crisis-copy-final.md`).
