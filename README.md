# Raisin website

Static site for **Raisin - Have Better Sex** (iOS). Privacy policy, consumer health data policy, terms, support, safety and evidence pages, plus a landing page. No JavaScript, one stylesheet, Figtree from Google Fonts.

Live at **https://princecharming001.github.io/raisin-site/**

## Pages

| Page | Root file | Clean URL |
|---|---|---|
| Landing | `index.html` | `/` |
| Privacy policy | `privacy.html` | `/privacy/` |
| Consumer health data policy | `health-data.html` | `/health-data/` |
| Terms of use / EULA | `terms.html` | `/terms/` |
| Support and coach content policy | `support.html` | `/support/` |
| Safety: when to see a doctor | `safety.html` | `/safety/` |
| Evidence: what Raisin is built on | `evidence.html` | `/evidence/` |

Every root page also exists as `<name>/index.html` so the clean URL works on GitHub Pages. Those copies are generated: **edit the root `.html` file, then run `python3 tools/mirror.py`** to refresh them. Do not edit the copies by hand.

The app links to the clean URLs (`src/lib/links.ts` in the app repo) and App Store Connect uses `/privacy/`, `/terms/` and `/support/`.

## Deploy

This folder is its own git repo, pushed to `princecharming001/raisin-site` on GitHub. GitHub Pages serves the `main` branch root (`.nojekyll` skips the Jekyll build).

```sh
python3 tools/mirror.py        # refresh the clean-URL copies if you changed a page
git add -A
git commit -m "Describe the change"
git push                       # deploys; live within a minute or two
```

Check `https://princecharming001.github.io/raisin-site/privacy/` afterwards. Pages builds can be watched at https://github.com/princecharming001/raisin-site/actions.

## Editing notes

- Voice and vocabulary follow `content/style-guide.md` in the app repo: plain words, numbers before reassurance, no shame vocabulary, no emoji, headings in sentence case with the page title lowercase-with-period (`privacy.`).
- Design tokens live at the top of `assets/site.css` (off-white `#F1F2F4` page, white 24px cards, `#161616` text, no shadows; inverts to black in dark mode).
- Support email on every page is `support@getraisin.app`. If that mailbox changes, search and replace it across the root pages and re-run the mirror script.
- The App Store badge on the landing page is `<a id="app-store-link" href="#">`. Point it at the listing URL on release day and change "Coming soon on the" to "Download on the".
- Effective dates are in the page head (`.meta`) and the last section of each policy. Update both when a policy changes.
