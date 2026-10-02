# dark-mode-tester

Test your light and dark color tokens side by side. See a full UI mockup in both modes and get WCAG contrast scores for every text/background pair. Single HTML file. Browser-only.

**Live demo:** https://0xelitesystem.github.io/dark-mode-tester/

## Why this exists

Dark mode is easy to ship badly. The usual failure modes:

- The dark accent color works against the dark background but the same hue fails against the light background
- Muted/secondary text passes 4.5:1 in light mode and only 3.2:1 in dark mode
- A surface/elevation that reads fine in light mode disappears in dark mode

This tool catches those by rendering both modes from the same set of tokens and computing every important contrast pair.

It is a single HTML file with no tracking and no network calls, and it is MIT licensed.

## Use

Open `index.html` in any browser, or visit the hosted demo at `https://0xelitesystem.github.io/dark-mode-tester/` once Pages is enabled.

1. Edit the six token values in each column (bg, surface, ink, muted, accent, border)
2. The preview updates as you type
3. The contrast table below shows WCAG scores for both modes

Click "Reset defaults" to start over.

## What gets tested

| Pair | WCAG threshold |
|---|---|
| Ink on background | 4.5:1 (body text) |
| Muted on background | 4.5:1 (body text) |
| Accent on background | 3:1 (large text or UI element) |
| Ink on surface | 4.5:1 |
| Muted on surface | 4.5:1 |

The mockup includes: heading, paragraph, muted text, link, card, primary button, secondary button, code block. Cover the elements most likely to surface contrast failures.

## Tech

- Single HTML file, ~600 lines
- Vanilla JS, no frameworks, no dependencies
- Light and dark themes for the tool itself with OS preference detection
- Accepts hex (3 or 6 digit), rgb()/rgba(), and a small set of CSS named colors

## What it doesn't do

- Doesn't test arbitrary HTML (use [wcag-audit-snippet](https://github.com/0xelitesystem/wcag-audit-snippet) for that)
- Doesn't simulate color blindness (use the browser DevTools "Rendering" panel)
- Doesn't generate Tailwind config, CSS variables, or any specific framework's tokens

## Privacy

Everything runs in your browser. The page makes no network requests, loads no external scripts or fonts, and has no analytics or tracking. The colour tokens you enter never leaves your machine. The one thing the page saves is your light or dark theme choice, written to `localStorage` under the key `theme` when you press the theme toggle. Clearing site data removes it.

## Run locally

```
git clone https://github.com/0xelitesystem/dark-mode-tester
cd dark-mode-tester
```

Then open `index.html` in any modern browser, or serve the folder with `python -m http.server` and visit http://localhost:8000/.

## Build

No build step. The whole tool is one `index.html` file with inline CSS and JavaScript, and there is nothing to install or compile.

## More

Part of a catalog of single-file browser tools and plain-language references, all MIT licensed and dependency-free: [0xelitesystem.github.io](https://0xelitesystem.github.io/). Built by [elitesystem.ai](https://elitesystem.ai).

## License

MIT. See [LICENSE](LICENSE).

## Related

- [wcag-audit-snippet](https://github.com/0xelitesystem/wcag-audit-snippet), heuristic accessibility checks
- [og-image-generator](https://github.com/0xelitesystem/og-image-generator), generate Open Graph cards
- [single-file-saas-template](https://github.com/0xelitesystem/single-file-saas-template), ship a SaaS in one HTML file
