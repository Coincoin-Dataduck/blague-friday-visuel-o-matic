# Partner carousel generator

A tiny static web page where event partners add their logo (or photo) and their games, then download a ready-to-post Instagram carousel.

- **One file** (`index.html`) + an `assets/` folder. No server, no database, no dependency, no build step.
- **Nothing is uploaded or stored**: everything runs in the partner's browser. No cookies, no tracking.
- **No AI**: background removal is a "plain background" magic wand or clicking the box corners.
- Free hosting on **GitHub Pages**.
- The **partner interface is in French** (strings live in `index.html`). The designer space, settings, code and docs are in English so anyone can reuse it.

> The images in `assets/` are **demo visuals** built with the Blague Friday logos and palette. Designers replace them (see `DESIGNER-GUIDE.md`).

## Folder

```
index.html
README.md
DESIGNER-GUIDE.md            <- give this to designers
assets/
  settings.txt               <- texts, colors, fonts... (plain text)
  event-logo.png             <- shown in the page header (optional)
  fonts/                     <- TITLE FONT and BODY FONT files
  cover/background.png
  cover/foreground-one-prize.png
  cover/foreground-several-prizes.png
  cover/zones.png
  game/background.png
  game/foreground.png        <- optional
  game/zones.png
  fixed-pages/01-tombola.png ...
```

## Test it on your computer

Double-clicking `index.html` does **not** work: browsers block reading `assets/` from a local file.

- **Mac**: open Terminal, type `cd ` (with a space), drag the folder into the window, press Enter, then run `python3 -m http.server 8000`. Open http://localhost:8000. Press Ctrl+C to stop.
- **Windows**: same from PowerShell with `py -m http.server 8000`, or simply publish on GitHub Pages (below) and test online.

Things to try: brand and person modes, a dark logo (the tool should ask for a badge), a JPG box photo on a white background (background removal), a very long game name, the download on a phone, and `#designer` (password).

## Publish on GitHub Pages (about 10 min, no command line)

1. On github.com, click **New repository**, name it (e.g. `blague-friday-visuels`), choose **Public** (required for free Pages; it only contains visuals meant to be published anyway).
2. **Add file -> Upload files**, drag **the content** of this folder (`index.html`, `assets/`...), then **Commit changes**.
3. **Settings -> Pages**: Branch `main`, folder `/ (root)`, **Save**.
4. After a minute or two the address appears, e.g. `https://your-account.github.io/blague-friday-visuels/`. Send this link to partners.

Custom domain (optional): **Settings -> Pages -> Custom domain** (e.g. `visuels.blaguefriday.fr`), then add a CNAME record pointing to `your-account.github.io` at your domain registrar.

**Updating visuals**: upload new files with **the same names**; they replace the old ones. Live in 1-2 minutes.

## Designer space

`https://.../#designer` - password protected. Designers pick their folder **from their own computer** (nothing is uploaded), get a plain-English report, can show the zones and fill the preview with sample content.

The password is only a curtain to keep the public out (the site is static and public, so it is not real security). To change it, replace `DESIGNER_PASSWORD_SHA256` in `index.html` with the output of `echo -n "new-password" | shasum -a 256`.

## Reusing it for another event

1. Replace everything in `assets/` (see `DESIGNER-GUIDE.md`) and edit `assets/settings.txt`.
2. Change the password hash.
3. Partner texts are in French in `index.html` (HTML and the "9. PRE-DOWNLOAD CHECKS" / "7. COVER" sections). Translate them there if your partners speak another language.

## Notes

- **Fonts**: Google Fonts are under the SIL Open Font License, so self-hosting them is fine. They are served from your site, not from Google (no third-party request, GDPR-friendly).
- **GitHub Pages limits**: 1 GB per site, ~100 GB traffic per month. Plenty for a few images.
- **Browsers**: recent Chrome, Edge, Firefox, Safari, desktop and mobile.

## For developers

- Everything is in `index.html`: HTML, CSS and ~950 lines of framework-free JavaScript in 12 commented sections.
- Zones are read from `zones.png` (pure color blobs, RGB distance tolerance 70) and reduced to their bounding box.
- The ZIP is written by hand (store-only, PNGs are already compressed), with CRC32 and UTF-8 file names.
- The only network requests are for `assets/` on the same origin.
