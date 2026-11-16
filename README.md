# Bildschirm-Test

Testbilder für Fernseher und Monitore, lokal im Browser. Teil der inoffiziellen consolecheat-Werkzeuge rund um [consolecheat.com](https://consolecheat.com). German is the primary language, English is the other. Light and dark theme, self-hosted fonts, footer, Impressum, and Datenschutz are included. There is no Webmail link.

No account, no tracking, nothing uploaded. Fonts (Outfit, Source Sans 3) are self-hosted from `@fontsource`, so the page makes no request to Google or any other third party. The Impressum fields are placeholders until the operator fills them in. No name or address was invented.

Site: <https://robfreak.github.io/consolecheat-ex7/>

Inoffiziell. Nicht von Sony.

## What it does

Local TV and monitor patterns: solid colors (black, white, red, green, blue, gray), horizontal and vertical color gradients, a coarse checkerboard, a one-device-pixel grid, near-black and near-white steps, a moving bar, scrolling stripes, and a text sharpness sample. Nothing is uploaded. The page does not fetch pattern data.

Open a pattern from the list, or with the number keys `1`–`9` and `0` (the first ten). Arrow keys move through every pattern, including on a D-pad that sends arrows. `Esc` leaves fullscreen first; the next `Esc` returns to the list. The on-screen buttons do the same. In fullscreen the controls fade after a few seconds and come back on a key, a pointer move, or focus. If the Fullscreen API is missing or refused, which some TV browsers do, the pattern still fills the window. That is as far as an ordinary web page can go in a PS5 or other TV browser. No console API is required.

The last opened pattern is remembered only in `sessionStorage`, key `consolecheat-bildschirm-pattern` (a pattern id such as `black`, this tab only). The page reads that key once on load. It does not write it until a pattern is opened, and it removes the key when you return to the list. Closing the tab drops it. Language and appearance reuse `consolecheat-lang` and `consolecheat-theme`. No other storage is used.

## Storage

- `consolecheat-bildschirm-pattern` (sessionStorage, only this tab)
- `consolecheat-lang` and `consolecheat-theme` (localStorage, shared with the other consolecheat tools on robfreak.github.io)

The Datenschutz page has a button that removes this page's keys. Nothing else is stored.

## Run and test

```bash
npm install
npm test        # node --experimental-strip-types --test src/bildschirm/*.test.ts
npm run dev     # http://127.0.0.1:5173/consolecheat-ex7/
npm run build   # typecheck, Vite build (base /consolecheat-ex7/), offline check of dist/
npm run preview # http://127.0.0.1:4173/consolecheat-ex7/
```

Node `>=22.6` (`package.json` `engines`).

## Files

- `index.html` — the HTML entry (Vite input)
- `src/bildschirm/` — React + TypeScript source, styles, and tests
- `src/bildschirm/tools.ts` + `src/bildschirm/tool-links.tsx` — the footer list **Weitere Werkzeuge** (keep it identical across the consolecheat repos)
- `public/` — `favicon.svg`, `FONT-OFL.txt`, `.nojekyll`
- `scripts/check-dist.mjs` — offline check of `dist/` (no third-party hosts, no `.woff` fallback, woff2 fonts present)
- `.github/workflows/pages.yml` — test, build, and deploy to `gh-pages`

## Other tools

The footer group **Weitere Werkzeuge** (English: **Other tools**) links to the other consolecheat tools: Title-ID-Finder (ex1), PS-Plus-Archiv (ex2), Controller-Tester (ex3), Save-Info-Leser (ex4), Fehlercode-Nachschlager (ex5), the [Spiele-Merkliste](https://robfreak.github.io/consolecheat-ex6/), and [Download-Zeit-Rechner](https://robfreak.github.io/consolecheat-ex8/), [Tastenbelegung](https://robfreak.github.io/consolecheat-ex9/), [HDR/Helligkeit](https://robfreak.github.io/consolecheat-ex10/), [Audio-Kanal-Test](https://robfreak.github.io/consolecheat-ex11/), [USB-Stick-Checkliste](https://robfreak.github.io/consolecheat-ex12/), [Combo-Trainer](https://robfreak.github.io/consolecheat-ex13/), [Sprite-Animator](https://robfreak.github.io/consolecheat-ex14/). These are ordinary links. The page does not request those sites.

This tool was moved here from [Robfreak/consolecheat-ex6](https://github.com/Robfreak/consolecheat-ex6).

## GitHub Pages

`.github/workflows/pages.yml` runs install, test, and build on pull requests and on every push. A push to `main` also pushes `dist/` to the orphan branch `gh-pages` (`peaceiris/actions-gh-pages`, Jekyll off). Vite `base` is `/consolecheat-ex7/`, which matches the project site <https://robfreak.github.io/consolecheat-ex7/>.

Enable once in the repository settings:

1. **Settings → Actions → General → Workflow permissions → Read and write permissions.** Save.
2. **Settings → Pages → Build and deployment → Source: Deploy from a branch.** Branch: **`gh-pages`**, folder: **`/ (root)`.** Save.

After that, every push to `main` updates the site.

## Credits

Outfit and Source Sans 3 are bundled from `@fontsource` under the SIL Open Font License; see `public/FONT-OFL.txt` and `THIRD_PARTY_NOTICES.md`.

Replace the Impressum placeholders with the operator’s real details before treating that page as a legal notice.
