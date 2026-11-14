---
name: awwwards-design
description: Design knowledge base and workflow for making websites, landing pages, UI components and visual designs that look distinctive, premium and Awwwards-level instead of generic AI output. Works on any AI model. Use whenever the user asks to build or design a site, page, section, hero, component, portfolio, landing, app screen or any visual interface, or says things like "красиво", "современный дизайн", "премиально", "как на awwwards", "не как нейронка", "unique", "award-winning", or complains that a result looks generic or AI-made. Contains the catalogue of AI-slop patterns to avoid and a growing library of analyzed real sites (colors, type, spacing, components, motion) to learn design principles from. Use it even when the user gives only a short prompt and expects strong design decisions to be made for them.
---

# awwwards-design

AI-made sites look the same because every model reaches for the same probable defaults: purple gradient, centered hero, three equal cards, fade-up on everything. Award-level work is the opposite: a **concept**, a **deliberate system with numbers**, one or two **memorable moments**, and **craft in the details**.

This skill gives you three things: a map of the defaults to avoid (`references/ai_pattern.md`), real analyzed sites to learn from (`references/NN_*.md`), and a process that turns a short prompt into a specific design.

**Language:** answer in the language the user writes in. Code and identifiers stay in English.

If a `plan-build` skill is available, run the steps below inside its UNDERSTAND and PLAN phases. If not, follow them directly.

---

## Process

### 1. Decode the design intent
The user rarely says what they want visually; a short prompt hides a lot. Work out, and write down in 5–6 lines:
- **What it is and who it is for:** brand, product, audience, the one action the visitor should take.
- **The feeling:** 3 words (for example: warm, archival, proud). Not "modern, clean, professional": those are the default and mean nothing.
- **What the user gave you:** colors, fonts, texts, references, screenshots. These are fixed. Do not "improve" them.
- **What they said they hate:** negations are requirements.
- **Vague words:** "красиво", "премиум", "современно", "как у Apple" are requests for decisions. Turn each into concrete choices (palette, type, scale, motion) and say which you chose.

Ask a question only if a wrong guess would waste the whole design. Otherwise decide and list the assumption.

### 2. Pick a concept
Write one sentence: "This site feels like ___ because ___." Then choose **one signature moment** (a type treatment, an interaction, a composition, a transition) that a visitor would remember a day later. Then name 3 things you are deliberately **not** doing (for example: no gradient, no glass cards, no centered 3-card row).

### 3. Anti-slop pass
Read `references/ai_pattern.md`. For a full page read all of it; for a single component read the sections that apply. Write down which defaults you were about to use and what replaces each. This is the single biggest quality gain.

### 4. Learn from references
Open the index at the bottom. Pick 2–3 references closest to the mood. Read them and extract **principles and numbers**, not appearance: how big is the contrast between largest and smallest type, how is the gutter set, what moves and how, where is the tension.
- Transfer the logic, not the look. Never reuse another brand's name, logo, photos, copy or exact layout.
- Blending two references is fine. If swapping the brand name still leaves it recognizably the reference, you copied too much.
- Values tagged `[est]` or `[?]` are approximate: use them as direction, not as law.

### 5. Write the design spec (numbers before code)
Decide once, then build from it. Every visual value must trace to a token.
- **Color roles:** background, surface, text, muted text, line, accent. Hex for each. Color should mean something (brand, product, material), not decorate.
- **Type:** the families (usually one display voice and one text voice), a real scale with sizes, line-height, tracking and case per role. Prefer fluid sizing (`clamp()`, `vw`) over fixed px. Aim for large scale contrast between the biggest and the smallest text.
- **Spacing:** one base unit, 6–8 steps, gutters, section padding, component padding and gaps all taken from it. No arbitrary 13px or 17px.
- **Shape:** one or two radii plus pill, line weights (hairlines are a structure tool), shadows (often none).
- **Motion:** 1–2 easing curves, 2–3 durations, what moves and why, the signature interaction, a `prefers-reduced-motion` fallback.
- **Composition per screen:** where is the focal point, where is the scale contrast, where is the deliberate tension (overlap, bleed, crop, asymmetry), where is the empty space.

### 6. Build
Skeleton first, then depth, then polish. Hover, focus and active states are part of the design, not an afterthought. Real content, no lorem ipsum when the topic is known.

### 7. Slop audit
Run the detector tests at the end of `references/ai_pattern.md` (swap test, squint test, default count, one-memorable-thing, tension, numbers). Fix what fails before answering. In the report, describe what you decided and why in one or two sentences. Do not call your own work "stunning" or "award-winning".

---

## Adding a new reference site

This library grows. When the user sends screenshots, colors, fonts, spacing or component code for a site:

1. Find the highest number in `references/` and use the next one. File name: `NN_Site_Name.md` (underscores, no spaces).
2. Follow the structure of `references/_TEMPLATE.md`.
3. **Text only.** No images, base64 or hotlinks. Describe precisely what is seen: layout, proportions, colors, type, behavior.
4. Tag every value: `[code]` came from provided HTML/CSS, `[user]` the user said it, `[est]` estimated by eye from a screenshot, `[?]` unknown or inferred. Never present an estimate as measured.
5. Prefer proportions (vw, ratios, multiples of a base unit) over raw pixels, and state the capture width. Sites that scale fluidly look broken when copied as fixed px.
6. Record behavior (hover, scroll, transitions) from what the user describes. If you add a reconstruction of CSS, label it as a reconstruction.
7. Do not copy the site's text, logo or assets. Record roles and structure instead.
8. Add the file to the index below. Tell the user what data is still missing (exact hex, font names, computed CSS, transition values) so they can send it next.

---

## Reference index

| File | What it is |
|---|---|
| `references/ai_pattern.md` | Catalogue of AI-slop patterns (layout, color, type, components, motion, copy, code, process), detector tests, and replacement moves. Read first. |
| `references/_TEMPLATE.md` | Structure for every site file. |
| `references/01_Delta_Cafes.md` | Delta Cafés (Portuguese coffee brand): warm chocolate + peach, condensed caps vs light sans, split pill nav with hanging logo, archival "orbit" collage, CTA pill that merges with its icon on hover. |
