# 01 — Delta Cafés (Portuguese coffee brand)

Source: 5 screenshots + HTML of the main CTA button, from the user. URL not given.
Capture widths: hero screenshot 2534 px wide (1350 tall); history section 2000 px wide (1051 tall); "objects" scene 1242 px wide; two button close-ups (zoomed about 1.25×).
Proportions below are given in vw of the capture width, because the layout scales fluidly: the colored tiles are 12.2vw wide in both the 2534 and the 2000 px captures. DPR is unknown.

Confidence tags: `[code]` from provided HTML · `[user]` stated by the user · `[est]` estimated by eye from a screenshot · `[?]` unknown or inferred

---

## 1. Essence
- **Mood:** warm, proud, archival.
- **Concept:** a coffee brand told as a family story of Portugal. Real faces, real archive material and a chocolate-brown world, with color appearing only where it means something: the product packs.
- **Signature moments:**
  1. Full-bleed documentary video/photo hero with all UI pushed to the perimeter and the face left clear.
  2. Split floating pill nav with the red triangular logo hanging between the halves like a physical object.
  3. The history scene: giant condensed caps in the middle, archival photos and cut-out objects scattered around, connected by hairline orbit curves.
  4. The CTA pill that grows around its icon on hover (section 6).
- **Why it is not slop:** no gradients, no glow, no centered 3-card row; one warm palette; real photography with a point of view; huge scale contrast (giant caps vs 15 px UI text); hairlines instead of boxes; content bleeds off the viewport edges.

## 2. Palette (all `[est]` unless noted)
| Role | Value | Tag | Used for |
|---|---|---|---|
| Deep chocolate (section bg) | ≈ #2B1B14 | est | history section, band under the hero |
| Brand ink | #35221A | code | arrow icon fill, label text on the peach button |
| Peach / cream | ≈ #EDD2BE | est | big headline, button fill, borders of the polaroid frames (slightly lighter ≈ #F3DFD3) |
| Muted peach | ≈ #C9A48E | est | body paragraph |
| Icon chip brown | ≈ #5B3C2E | est | the circular/pill icon button next to the CTA |
| Hairline | peach at 12–20% opacity | est | orbit curves, progress lines, dividers |
| Glass surface | dark brown ≈ rgba(35,24,19,0.6) + backdrop blur | est | nav pills, hero cards |
| Hero overlay | warm dark ≈ rgba(25,15,10,0.4–0.5) | est | over the hero video |
| Logo red / yellow | ≈ #E2231A / ≈ #FFD200 | est | triangle logo and lettering |
| Tooltip | ≈ #3B2A22 with peach text | est | label on hover over the cut-out objects |

Product tile strip, left to right (all `[est]`): pale peach-pink ≈ #D9B8A8, deep green ≈ #0A5A45, royal blue ≈ #0A2FB5, purple ≈ #4B0E6B, azure ≈ #0E73C0, magenta ≈ #B0136B, green ≈ #2E9A2A, orange ≈ #D9601A, yellow ≈ #F2B300. Each tile is a saturated flat color with a product pack and a fruit/flower image peeking in.

**Palette logic:** everything is chocolate + peach (two near-neutral warm tones). Saturated color is reserved for product identity, so when color appears it means "a different blend". Do not add a separate accent color.

## 3. Typography
Three voices, all `[est]`:

| Role | Style | Weight | Size | Line-height | Tracking | Case |
|---|---|---|---|---|---|---|
| Hero headline ("There is a lot of Portugal in Delta.") | light neo-grotesque / humanist sans | ≈ 300 | ≈ 3.9vw (98 px @2534) | ≈ 0.94 | tight, ≈ −0.03em | sentence case; warm white at ≈ 75% |
| Section headline ("SINCE 1961, COFFEE THAT AWAKENS STORIES") | very condensed heavy grotesque, Tusker-like | bold / heavy | ≈ 5.3vw (107 px @2000) | ≈ 0.9 | ≈ 0 | UPPERCASE, peach |
| Nav | neo-grotesque | medium | ≈ 0.6vw (15 px @2534) | 1 | ≈ +0.02em | UPPERCASE |
| Body paragraph | neo-grotesque | regular | ≈ 0.9vw (18 px @2000) | ≈ 1.2 | ≈ 0 | sentence case, centered, muted peach, width ≈ 25vw |
| Button label | neo-grotesque; class `-sans-text-3-medium` `[code]` | medium | ≈ 0.75vw (15 px @2000) | 1 | 0 | sentence case |
| Card titles / chapter titles | neo-grotesque | regular | ≈ 0.55–0.63vw (14–16 px @2534) | ≈ 1.15 | 0 | sentence case |

Notes:
- **Mixed size inside one headline:** the word "THAT" is ≈ 55% the size of its neighbors, baseline-aligned. It makes the heading read like a spoken line and gives it voice. A rule to transfer: connector words smaller, nouns huge.
- **Scale contrast:** biggest text ≈ 107 px vs smallest UI text ≈ 13–15 px, about 7×.
- **Type tokens** `[code]`: the class `-sans-text-3-medium` suggests a naming scheme `<family>-<role>-<step>-<weight>`: a small set of named text styles instead of ad-hoc sizes.
- Free substitutes (not the real fonts): display caps → Anton, Bebas Neue or Antonio; hero light sans → Hanken Grotesk 300 or Inter Tight 300 with negative tracking; UI/body → Instrument Sans, Hanken Grotesk or Inter Tight.

## 4. Layout, spacing, shape (`[est]`)
- **Outer gutter:** ≈ 0.9–1.2vw (22–30 px @2534). Hero UI sits this close to the viewport edges. Very tight, which is why the hero feels full-bleed.
- **No max-width container.** The hero is edge to edge; the history section is centered text with scattered media.
- **Fluid sizing:** components scale with viewport width (tiles 12.2vw, nav ≈ 47vw wide, chapter thumbnails ≈ 4.3vw). Use vw/clamp, not breakpoint-fixed px.
- **Radius system:** pill (999px) for nav and buttons; ≈ 0.6vw (≈ 14–16 px @2534) for hero cards; ≈ 0.4vw for tile tops; ≈ 0.4–0.5vw for photo frames; tooltip ≈ 10 px.
- **Borders and shadows:** no shadows seen. Structure comes from hairlines (≈ 1 px, peach at ≈ 15%).
- **Gaps:** hero cards ≈ 10 px apart; chapter columns ≈ 12 px apart; product tiles ≈ 12–14 px apart.
- **Vertical position in the history screen (@2000×1051):** headline top ≈ 19% of viewport height; CTA ≈ 50%; paragraph ≈ 58–63%.

## 5. Screen-by-screen composition

### Screen A: hero (2534×1350)
- Full-bleed video/photo of a smiling elderly man with closed eyes holding a Delta cup, warm low-key grade, dark overlay. His face is the focal point and sits in the center-top; nothing covers it.
- **All UI hugs the perimeter:**
  - top center: the split pill nav with the logo;
  - top-left: a small dark pill with a waveform icon (probably an audio toggle `[?]`);
  - top-right: a dark pill "globe + EN ⌄";
  - bottom-left: headline (2 lines, left aligned at ≈ 1vw from the edge) and under it a row of three numbered chapters;
  - bottom-right: a cluster of 4 cards (bento);
  - bottom-left corner, fixed: a small round dark button with a link-like icon `[?]`.
- **Chapter row:** three columns ≈ 10.6vw wide, ≈ 0.5vw apart, each with a hairline on top (looks like progress bars of a slideshow `[?]`), then a 4.3vw × 2.7vw thumbnail on the left, "01 / 02 / 03" small above a two-line title on the right. A faint hairline continues along the same y toward the right side.
- **Bento cluster:** ≈ 16.6vw wide, bottom-right, ≈ 1.2vw from the right edge. Four cards: a "Products →" pill-card; a product card ("The Azores coffee" with a pack image); an image card ("Delta Sustainability", photo of beans in a sack with the label overlaid at the bottom-left, image inset ≈ 6 px inside its card with its own radius); a wide card "The History of delta" with a roaster illustration, a title, two lines of muted text and an arrow. Cards are translucent dark glass, restrained: tint + blur + small radius, no glow, no gradient.
- The photo ends at ≈ 95% of the viewport height, leaving ≈ 5% for the strip below.

### Screen B: product strip (bridge between hero and history)
- A dark chocolate band below the hero with a row of tall saturated color tiles peeking up from the bottom edge (≈ 12.2vw wide, ≈ 0.5vw gap, tops rounded). It invites scrolling.
- In the next screenshot the same strip is visible at the very top (bottom parts of the tiles), so it scrolls away with the page rather than being fixed. The first tile is partly cut by the left edge.

### Screen C: history teaser (2000×1051)
- Background deep chocolate. Centered: giant condensed caps headline (3 lines, ≈ 32vw wide) → pill CTA with icon → paragraph (3 lines, ≈ 25vw wide, muted peach).
- **Scattered archive media around the text, never over it:** a framed B&W Expo '98 photo top-left (≈ 13.5vw × 10vw), a tall framed B&W factory photo on the right bleeding off the right edge (≈ 13.6vw × 19vw), an unframed "Deltanic" movie-parody poster bottom-left-center (≈ 9.5vw × 13.4vw), a small framed photo (≈ 7.5vw × 5vw, rotated ≈ 3°), a color illustration bleeding off the bottom-right corner, a group photo bleeding off the bottom-left corner. Sizes range from 5vw to 19vw; several are cropped by the viewport.
- **Frames:** cream/peach "polaroid" border ≈ 8–10 px, radius ≈ 10 px, slight rotation (≈ −2° to +3°) `[est]`.
- **Orbit curves:** 1 px low-contrast lines: one huge circle arc passing around the text block (radius ≈ 31vw) plus wavy S-curves linking photos to each other. They suggest a timeline path or orbit that the media travels along while scrolling `[?]`.

### Screen D: objects scene (1242 wide)
- Same chocolate background and curves, now with **cut-out objects** (no frame, transparent background): a large vintage Delta tin with a striped label (≈ 24vw, cropped by the left edge) and a modern red-orange "rise" appliance (≈ 17vw).
- **Tooltip on hover:** a dark rounded label "Delta Foundation" with a small pointer, peach text ≈ 1.4vw, ≈ 16vw × 4.5vw box, anchored to the object. The objects look like hotspots that lead to subpages `[?]`.
- A pale-lime rectangle (≈ #F0FFDC `[est]`) is cut by the top edge: purpose unknown.

## 6. Components

### Nav (split pill with hanging logo)
- Two dark glass pills (left and right halves) ≈ 47vw wide in total, ≈ 1.9vw tall, ≈ 0.9vw from the top, symmetric around the center. The inner ends follow the silhouette of the logo `[est]`.
- Logo: red triangle with yellow lettering, ≈ 3.6vw × 3.2vw, flush with the top of the viewport, taller than the bar so it pierces it above and below. It reads as an object hanging in the bar, not an image inside a bar.
- Left group: DELTA CAFÉS ⌄ · COFFEE CULTURE ⌄ · PRODUCTS. Right group: BUSINESS SOLUTIONS · SUSTAINABILITY · JOURNAL. Uppercase medium ≈ 0.6vw, gaps between items ≈ 1.4vw. Dropdown chevrons on two items.
- Language pill (globe + "EN ⌄") and the waveform pill are separate small pills at the far left and far right.

### Hero chapter row, bento cards, product tiles, polaroid frames, orbit curves
See section 5. These are components of the composition; copy the logic (perimeter UI, glass with restraint, hairlines, peeking strip) and not the content.

### CTA button: label pill + icon pill that merge on hover
This is the signature micro-interaction. Facts first, then a reconstruction.

**Facts**
- DOM `[code]`:
  ```html
  <div class="label-container">
    <span class="label-wrap"><span class="-sans-text-3-medium">History of Delta</span></span>
  </div>
  <span class="icon-container arrow-right"> …icon… </span>
  <span class="icon-container ghost arrow-right"> …identical icon… </span>
  ```
  The icon is `data-component="icon"`, size class `xsmall`, `viewBox="0 0 20 20"`, one path with `fill="#35221A"`:
  `m11.09 3.3 5.333 6.133-5.307 6.16 1.04 1.04 7.306-7.2-7.333-7.2zm6.293 5.226H1.595v1.867h15.787z`
  This is a long thin arrow (shaft ≈ 1.9 units thick, spanning ≈ 84% of the box, with a solid chevron head). There are two identical icon containers, one normal and one with the class `ghost`.
- The `data-v-xxxx` attributes mean Vue scoped styles (probably Nuxt) `[code]`. The CSS was not extractable.
- **Rest state `[est]`** (measured on the 2000 px capture): label pill ≈ 126 × 44 px (6.3vw × 2.2vw), peach fill, ink text, left/right padding ≈ 22 px. Next to it an icon pill ≈ 53 × 38 px (≈ 1.4:1, a rounded pill, not a perfect circle), chip-brown fill, light arrow, vertically centered so it is ≈ 3 px shorter than the label pill at top and bottom. The two shapes touch or overlap by up to ≈ 11 px. Total width ≈ 177 px (≈ 8.8vw).
- **Hover state** `[user]` + `[est]`: when the pointer is over the **label** (not the icon), the label pill and the icon pill become one shape. Measured: the peach shape grows to the right until it wraps the icon pill, which stays in place and ends up inset ≈ 3 px from the pill's top, bottom and right edge. Total width stays ≈ the same (≈ 175 px). So the icon does not travel; the peach shape expands underneath it.
- Whether hovering the icon alone triggers the same effect: `[?]`. Duration and easing: `[?]`.
- The arrow color in the screenshots is light on the brown chip, while the SVG fill is #35221A: the fill is overridden by CSS (likely `currentColor`) `[?]`.
- Purpose of the `ghost` duplicate icon: `[?]`. The usual technique is an arrow-swap where the first arrow slides out to the right while the ghost slides in from the left on hover.

**Reconstruction (not the original CSS; verify when real CSS is available)**
```css
.cta{
  --h:44px; --rim:3px; --icon-w:53px; --pad:22px; --overlap:11px;
  --peach:#EDD2BE; --ink:#35221A; --chip:#5B3C2E;
  position:relative; display:inline-flex; align-items:center; height:var(--h);
  padding:0 calc(var(--icon-w) + var(--overlap)) 0 var(--pad);
  font:500 15px/1 var(--sans); color:var(--ink); text-decoration:none;
}
.cta::before{                      /* the peach shape: label-sized at rest */
  content:""; position:absolute; inset:0 auto 0 0;
  width:calc(100% - var(--icon-w) + var(--overlap));
  border-radius:999px; background:var(--peach);
  transition:width .6s cubic-bezier(.65,0,.35,1);   /* easing is a guess */
}
.cta:hover::before{ width:calc(100% + var(--rim)); }  /* grows to wrap the icon */
.cta__label{ position:relative; }
.cta__icon{                        /* sits above the peach shape and never moves */
  position:absolute; right:0; top:var(--rim);
  width:var(--icon-w); height:calc(100% - 2*var(--rim));
  display:grid; place-items:center; border-radius:999px;
  background:var(--chip); color:var(--peach);
}
```
Rendered and checked in Chromium: at rest the peach pill and the chip overlap by ≈ 11 px; on hover the peach shape grows to wrap the chip, which stays in place with a ≈ 3 px rim on top, bottom and right. This matches the screenshots. Timing and easing are still guesses. In a fluid build, express `--h`, `--pad`, `--icon-w`, `--rim` in `em` or `vw` so the button scales with the page.

**Transferable rule:** on hover, change the *shape relationship* between two parts of one component (a pill swallowing its icon) instead of scaling or lifting the whole button.

## 7. Motion and interaction
Known: the CTA merge (above); a hover tooltip on the cut-out objects; the strip scrolls away with the page; the hero chapter row looks like slideshow progress.
Unknown `[?]`: chapter transitions, parallax of the orbit scene, how media moves along the curves, the preloader, the cursor, hover states of hero cards and of the nav dropdowns, mobile behavior.

## 8. Principles to transfer
1. **Perimeter UI:** in a full-bleed hero, put all UI on the edges and keep the subject's area clear.
2. **Two near-neutral tones for the whole site; saturated color only where it carries identity.**
3. **Extreme scale contrast:** giant condensed caps beside ≈ 15 px UI text.
4. **Mixed sizes inside a headline:** shrink connector words to ≈ 55% for voice and rhythm.
5. **Real, specific imagery:** documentary portraits and archive material with a point of view; cutouts as objects.
6. **Hairlines as structure:** low-contrast 1 px lines (progress, orbit curves, dividers) instead of boxes and shadows.
7. **Controlled bleed:** let images run off the viewport edges and keep text clear of them.
8. **Restrained glass:** tint + blur + small radius, no glow, no gradient, no border-white/10 cliché.
9. **A logo or key element behaves like a physical object** (hangs between nav halves, pierces the bar).
10. **Micro-interactions change shape relationships** (the CTA swallowing its icon) rather than scale or lift.
11. **Fluid proportions:** size everything in vw/clamp so the composition keeps its proportions at any width.
12. **Peek to invite scrolling:** a strip of the next content visible under the hero.

## 9. What not to copy
The Delta name, logo, triangle shape and slogans; the photographs and archive material; the "Deltanic" parody poster; the exact copy lines; the product pack imagery. Reuse the logic (section 8), not the content.

## 10. Missing data (ask the user)
- Eyedropper hex for the chocolate, peach, muted peach, chip brown and the nine tile colors.
- Real font names and computed values (family, size, weight, line-height, letter-spacing) for the hero headline, the caps headline, nav and body.
- Computed CSS for the CTA (padding, height, radius, transition property, duration, easing), including the `ghost` icon behavior and what happens when the icon alone is hovered.
- Nav bar CSS (background, blur amount, radius, the shape around the logo) and dropdown behavior.
- Hero: how chapters switch, whether the hairlines animate as progress, the video overlay value.
- History scene: how the media and curves move on scroll.
- Hover state screenshots of the cards; mobile layout; preloader and cursor.
