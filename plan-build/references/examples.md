# Worked examples

Two examples that show the shape of the request card and the plan: one vague request in Russian, one precise request in English. The values inside are illustrations of the format, not defaults to copy.

---

## Example 1: vague visual request (Russian)

**User:** сделай лендинг для кофейни, чтоб красиво было, тёмный, без банальщины, секция меню и контакты

**Visible start of the answer:**
Понял так: тёмный одностраничный сайт для кофейни, с секциями меню и контактов, без шаблонных стоковых блоков вроде «Наши преимущества».

**Request card (working memory)**
```
Goal:      single-page dark landing for a coffee shop, publishable as is
Must:      1. dark theme  2. menu section  3. contacts section  4. looks good
Must NOT:  generic template blocks ("our advantages", stock-photo grids, lorem ipsum)
Implied:   responsive (phone + desktop), real-looking content, working anchor nav,
           readable contrast, opens by double-clicking index.html or with one command
Keep verbatim: "тёмный", sections named Меню and Контакты (site language = Russian)
Assumptions:
  A1. Name and address are not given → invented placeholder shop "Зерно", clearly
      marked in the report so the user can swap them
  A2. Plain HTML/CSS/JS in one folder, no build step (nothing in the request needs more)
  A3. Menu content: 8–10 items in 3 groups with prices, written by me
Blocking questions: none
```

**Plan**
```
Approach:  one index.html + styles.css + script.js; no dependencies
Decisions: background #0e0c0a, text #f1e9df, accent #c8803a; one serif for headings
           + one sans for body; spacing scale 8 / 16 / 24 / 48 / 96 px; section
           padding 96 px desktop, 64 px phone; one easing curve for all motion,
           250 ms; one signature element: oversized heading with a slow fade-up
Steps:
  1. Skeleton: header, hero, menu, contacts, footer → page opens, anchors work
  2. Styles: palette, type, spacing scale applied everywhere
  3. Menu: 3 groups, 8–10 items, prices aligned
  4. Contacts: address, hours, phone, map placeholder block
  5. Responsive pass at 390 px and 1440 px
  6. Verify against card
Risks:     contrast of accent on dark: check ≥ 4.5:1 for body-size text
```

Notice: "красиво" became concrete decisions, "без банальщины" became a Must NOT, and the unknowns (name, address) became logged assumptions, not questions.

---

## Example 2: precise technical request (English)

**User:** write a python script that renames my photos by the date they were taken, format YYYY-MM-DD_HHMMSS.jpg. don't touch the originals.

**Visible start of the answer:**
Understood: a Python script that copies photos into a new folder named by the capture date as `YYYY-MM-DD_HHMMSS.jpg`, leaving the originals untouched.

**Request card**
```
Goal:      script producing date-named copies of photos
Must:      1. python  2. name format YYYY-MM-DD_HHMMSS.jpg  3. date = date taken
Must NOT:  modify, rename, move or delete originals
Implied:   handles photos without EXIF date; handles name collisions (two photos in
           the same second); clear usage; prints what it did; works on a folder
Keep verbatim: format YYYY-MM-DD_HHMMSS.jpg
Assumptions:
  A1. "Don't touch originals" → output goes to a new folder "renamed/" next to the input
  A2. No EXIF date → fall back to file modified time, and say so in the output
  A3. Collision → append _1, _2 before the extension
  A4. Library: Pillow for EXIF (the only dependency)
Blocking questions: none
```

**Plan**
```
Approach:  one file, rename_photos.py, argparse CLI, Pillow for EXIF
Steps:
  1. CLI: input folder argument, optional --out, --dry-run
  2. Read DateTimeOriginal from EXIF; fall back to mtime
  3. Build the target name; resolve collisions
  4. Copy (never move) into the output folder; print one line per file + summary
  5. Verify: dry run on a sample, one file without EXIF, two files with the same time,
     confirm originals unchanged
Risks:     other extensions (.jpeg, .JPG): match case-insensitively
```

Notice: the one negation ("don't touch the originals") shaped the whole design (copy, not rename), and it is checked again in the last step.
