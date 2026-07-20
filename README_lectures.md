# Mini lectures — how they work

## Folder structure

```
Ped All\
    paediatrics-dashboard_3.html
    README_lectures.md
    assets\
        tb_mantoux.jpg
        measles_koplik.jpg
        ... etc
```

All image paths inside the HTML are **relative** (`assets/...`), so this folder can go
on a USB stick, be zipped and emailed, or dropped on a hospital desktop and it still works.
No drive letters anywhere.

## Presenting

- Every one of the 180 diseases has a mini lecture. Open a disease, and its deck loads in the
  right-hand rail automatically. There is nothing to build per disease.
- **P** — present full screen. **F** — toggle true browser full screen (F11 also works).
- Arrows, spacebar or click to advance. Click the left quarter of the screen to go back.
- **Home** / **End** jump to first and last slide. **Esc** exits.
- Click any slide in the rail to start presenting from that slide.
- On a narrow screen the rail hides; the **Lecture** button in the toolbar opens it.

## Where the slides come from

Decks are generated from each disease's own `sections`, `tables`, `mnemonics` and `pearls`.
Edit the disease content and the lecture updates with it — there is no second copy to keep in sync.
Long sections are split into 4-point slides automatically.

## Adding images

Images are optional. A disease with no images still has a full deck. To add one:

1. Put the file in `assets\`.
2. Add an entry to `FIGURES` near the top of the `<script>` block:

```js
"dengue": [
  {after:"Warning Signs & Classification", file:"dengue_tourniquet.gif",
   alt:"Forearm showing petechiae after cuff inflation",
   caption:"Positive tourniquet test — >10–20 petechiae per square inch.",
   credit:"CDC, Public domain, via Wikimedia Commons (https://...)"},
],
```

`after` must match a section heading of that disease **exactly**. If it does not match, the
figure is appended at the end of the deck and a warning is logged to the browser console —
it is never silently dropped. Omit `after` to place the figure straight after the title slide.

If a file is missing or misnamed, the slot shows the expected filename in orange. Fix the
name, refresh, the orange disappears.

## Attribution — do not skip this

Every `credit` string was taken from the Wikimedia Commons API at download time, not written
by hand. CC BY and CC BY-SA both **require** visible credit. Credits appear in two places:
under each image, and on an automatic image-credits slide near the end of each deck.

Currently covered: the 12 Infectious Disease entries plus Measles — 18 figures, all from
Wikimedia Commons (CDC/PHIL public domain, or CC BY / CC BY-SA with named authors).
The other 167 diseases have decks but no images yet.

## Going to a single file

Only at the very end, once images are final. Replace each `assets/NAME` path with a
base64 `data:` URI. The file gets large (tens of MB) and slow to edit, so keep the folder
version as the working copy.
