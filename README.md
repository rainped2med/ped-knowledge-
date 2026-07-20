# Paediatrics Teaching Dashboard

A single-file clerkship reference and lecture tool covering **180 paediatric diseases**.
Open `paediatrics-dashboard_3.html` in any browser — no server, no build step, no install.

## What it does

- **Reference view** — every disease runs from pathophysiology through clinical features,
  investigations and management, with comparison tables and exam pearls.
- **Mini lectures** — each of the 180 diseases has a slide deck in the right-hand rail,
  generated from that disease's own content. Press **P** to present full screen.
- **Search** — by symptom, sign or drug across every entry.

## Presenting

| Key | Action |
|---|---|
| `P` | Present full screen |
| `F` | Toggle true browser full screen |
| `→` `space` / `←` | Next / previous slide |
| `Home` / `End` | First / last slide |
| `Esc` | Exit presenter |
| `/` | Focus search |

Click any slide in the rail to present from that slide. Click the left quarter of the
screen to go back. On a narrow screen the rail hides behind the **Lecture** button.

## Layout

```
paediatrics-dashboard_3.html   the whole application
assets/                        62 figures, referenced by relative path
README_lectures.md             how to add images and edit decks
IMAGE_CREDITS.md               full attribution for every image
```

Image paths are relative, so the folder works from a USB stick, a zip, or a hospital
desktop with no network.

## Images

54 of the 180 diseases carry figures; the rest are text-only and read fine without them.
Every image is from Wikimedia Commons — public domain, CC0, CC BY or CC BY-SA — with
attribution taken from the Commons API at download time and shown both under each figure
and on an automatic credits slide in each deck.

**49 figures are published here. A further 13 are deliberately not.** Those 13 are clinical
photographs in which a patient — in most cases a child — is identifiable. They are freely
licensed on Commons, so withholding them is an editorial choice rather than a licensing
one: a public repository is a much wider audience than a lecture theatre. Their slots
render as an orange placeholder naming the expected file, so the decks still work; supply
your own copy in `assets/` if you want them.

**CC BY and CC BY-SA require attribution to travel with the work.** If you redistribute
this repository or the images in it, keep `IMAGE_CREDITS.md` with them.

See [IMAGE_CREDITS.md](IMAGE_CREDITS.md) for the full list.

## Adding an image

Drop the file in `assets/`, then add an entry to `FIGURES` near the top of the `<script>`
block. `after` must exactly match a section heading of that disease; if it does not match,
the figure is appended at the end of the deck and a warning is logged to the browser
console rather than being silently dropped.

```js
"dengue": [
  {after:"Warning Signs & Classification", file:"dengue_tourniquet.gif",
   alt:"Forearm showing petechiae after cuff inflation",
   caption:"Positive tourniquet test.",
   credit:"CDC, Public domain, via Wikimedia Commons (https://...)"},
],
```

A missing or misnamed file shows an orange slot naming the file it expected.
Full details in [README_lectures.md](README_lectures.md).

## Licence

The written clinical content is the author's own. Images remain under their individual
licences as listed in `IMAGE_CREDITS.md`.
