# Designer guide: preparing the generator assets

No code. You deliver **a folder of images with exact names** and a short text file of settings.

## 1. Format

- All images have **exactly the same size** as `cover/background.png`. Recommended: **1080 x 1350 px** (Instagram 4:5 portrait).
- **PNG**. Foregrounds are **transparent** except for their elements.

## 2. Files (exact names)

| File | Role |
|---|---|
| `cover/background.png` | Cover background (under the logo or photo) |
| `cover/foreground-one-prize.png` | Elements above the logo (title, "vous fait gagner **un lot**" bubble...), used when the partner offers 1 copy in total |
| `cover/foreground-several-prizes.png` | Same, "vous fait gagner **des lots**" version |
| `cover/zones.png` | Where the logo and/or photo go (see 3) |
| `game/background.png` | Game page background |
| `game/foreground.png` | *(optional)* Elements above the game box |
| `game/zones.png` | Where the game name, box and number of copies go |
| `fixed-pages/01-tombola.png`... | Pages identical for every partner, added at the end |
| `fonts/...` | Title font and body font (TTF, OTF, WOFF, WOFF2) |
| `event-logo.png` | *(optional)* Logo shown at the top of the tool |
| `settings.txt` | Texts, colors, settings (see 4) |

Stacking order: **background -> logo / photo / box -> texts -> foreground**.

## 3. Drawing zones (`zones.png`)

On a transparent layer at the visual size, draw **flat pure-color shapes** where the tool should place each element:

| Color | Hex | What goes there |
|---|---|---|
| Red | `#FF0000` | Partner **logo** (as large as possible, never distorted, centred) |
| Blue | `#0000FF` | Partner **photo** (draw a circle: its diameter is used) |
| Green | `#00FF00` | **Game name** (auto-sized, 2 lines max) |
| Purple | `#8000FF` | **Game box** |
| Yellow | `#FFFF00` | "**10 exemplaires a gagner !**" text |

- Red and blue go in `cover/zones.png`. Draw only one of them and only that mode (brand or person) is offered.
- Green, purple and yellow go in `game/zones.png`.
- One shape per color; only its bounding rectangle matters. No gradients, no shadows.

## 4. `settings.txt`

Open it with any plain text editor. One setting per line: `NAME : value`. Lines starting with `#` are comments. Delete a line to use the default value. Texts that appear on the visuals are written in the partners' language.

| Setting | Example | Notes |
|---|---|---|
| EVENT NAME | Blague Friday | Page header and file names |
| YEAR | 2026 | Same |
| EVENT LOGO | event-logo.png | File at the root of the folder |
| TITLE FONT | LondrinaSolid-Regular.ttf | In `fonts/`. Used on the visuals and UI headings |
| BODY FONT | AtkinsonHyperlegibleMono-Regular.ttf | In `fonts/`. Used for the tool interface |
| FIXED PAGES | 01-tombola.png, 02-live.png | Added at the end, in this order |
| GAME NAME COLOR | #FFFFFF | |
| GAME NAME IN CAPITALS | yes | yes / no |
| COPIES COLOR | #FAD752 | |
| TEXT FOR 1 COPY | 1 exemplaire à gagner ! | |
| TEXT FOR SEVERAL COPIES | [n] exemplaires à gagner ! | `[n]` is replaced by the number |
| MAX NUMBER OF GAMES | 17 | A carousel holds 20 pages max |
| PHOTO OUTLINE COLOR | #FAD752 | Round photo outline |
| PHOTO OUTLINE WIDTH | 12 | px, 0 = none |
| FALLBACK BADGE COLOR | #FFFFFF | Added behind an unreadable dark logo |
| DARK BADGE COLOR | #002F2E | Added behind an unreadable light logo (e.g. white) |
| BADGE CORNER RADIUS | 24 | px |
| BADGE PADDING | 30 | px |
| READABILITY THRESHOLD | 2.5 | Minimum logo/background contrast (3 = stricter) |
| MIN LOGO SIZE | 800 | px |
| MIN PHOTO SIZE | 800 | px |
| MIN BOX SIZE | 1000 | px, longest side |
| INTERFACE COLOR | #005756 | Tool buttons |

## 5. Check your folder before delivering

1. Open the tool with **`#designer`** at the end of its address and enter the password.
2. Click **Choose my assets folder** and select your folder. It stays on your computer.
3. Read the report and fix everything in red. Orange items are advice.
4. Click **Fill with sample content** and tick **Show zones** to check the result with a fake logo, a box and a very long game name.
5. When everything is green, deliver the folder.
