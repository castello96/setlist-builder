# Setlist Builder

A single-file, offline setlist builder for any band or event. Open `Setlist Builder.html` in Chrome; no install or server needed.

## Features

- **Song catalog**: title, key, lead vox (picked from your band members), length, tempo, notes and tags. Filter by tag, singer, or missing info.
- **Mashups**: one setlist slot made of parts of 2+ songs. The parts can be catalog songs or free text.
- **Setlists**: create, duplicate, and delete them. Drag songs in from the catalog (or multi-select and add), drag to reorder, add breaks, and mark segues.
- **Per-gig overrides**: key, vox, tempo, and notes can change for one setlist without touching the catalog. Length is global.
- **Set times**: per-set and whole-show totals, with a configurable gap between songs (no gap counted after a segue) and optional targets.
- **Print / PDF**: band logo, selectable and reorderable columns, multi-page flow or shrink-to-fit-one-page, Letter or A4.

## Band files

Each band lives in its own `.json` file:

1. Open the app, then click **Open band file…** (or **Start a new band**).
2. Work as normal. The header shows **● Unsaved changes** when there is anything to save.
3. Click **Save band file** to download `<band-name>.json`, and keep that file somewhere safe.

The browser also keeps your latest work between visits, but treat the band file as the real copy.

`some-guys.json` is an example band file.

Songs can be imported from a CSV under **Band settings**. Recognized columns: `title`, `lead vocals`/`vox`/`singer`, `key`, `length`/`duration`, `tempo`/`bpm`, `notes`, `tags`.
