# Zedex Brand Assets

## Files in this folder

| File | Use | Format |
|---|---|---|
| `wordmark.svg` | "Zedex." wordmark — use in pitch decks, email signatures, invoices | SVG (vector) |
| `z-mark.svg` | Square Z monogram — 512×512 viewport, cream background, gold italic Z | SVG (vector) |
| `favicon.svg` | Browser tab icon — already wired into `index.html` and `case-studies.html` | SVG (vector) |
| `linkedin-banner.html` | Personal LinkedIn profile banner (1584×396), 3 variants. Open in browser, export to PNG. | HTML → PNG |
| `banners.jsx` | Original React components from Claude Design (reference only — use `linkedin-banner.html` instead) | React/JSX |

## Exporting to PNG (LinkedIn, favicon, etc.)

### LinkedIn profile banner (1584×396)

1. Open `linkedin-banner.html` in Chrome at 100% zoom.
2. Pick the variant you like best (A, B, or C).
3. Press `F12` → in DevTools Elements tab, right-click the `<div class="banner">` you want → **Capture node screenshot**.
4. Upload the resulting PNG to LinkedIn → your profile → banner edit.

The file already accounts for LinkedIn's profile-photo overlay: all text sits in the right half so the circle avatar in the lower-left does not obscure your headline.

### Z mark as company-page logo (300×300 PNG)

1. Open `z-mark.svg` in Chrome.
2. Press `F12` → right-click the `<svg>` element → **Capture node screenshot**.
3. Use an image resizer (e.g. squoosh.app) to downsize to 300×300 if needed.

### Favicon (32×32)

Already wired into the site. Browsers render `favicon.svg` directly — no PNG export needed unless you want fallback support for very old browsers.

## LinkedIn profile photo recommendation

**Use your face, not the Z mark.** Personal LinkedIn profiles convert better with a real human photo. Save the Z mark for the Zedex company page (if/when you create one).

## Company page assets (if you create a LinkedIn company page)

- **Company logo:** 300×300 from `z-mark.svg` (see above)
- **Cover image:** 1128×191 — this is a *different* size from the personal banner. You'd need a new variant of `linkedin-banner.html` with those dimensions. Tell Claude Code to build one when you're ready.

## Brand tokens (for reference)

| Token | Hex | Role |
|---|---|---|
| `--bg` | `#F4EFE6` | cream page bg |
| `--gold` | `#B5693A` | primary accent |
| `--gold-soft` | `#C88254` | hover |
| `--navy` | `#2A4158` | secondary accent |
| `--text` | `#0F1824` | near-black body |

Typography: **Inter** (all weights 300–800 + italics) for website and all asset text. Playfair Display was deprecated 2026-04-24 for readability.
