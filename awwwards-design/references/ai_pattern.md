# AI patterns (AI slop): what to avoid and what to do instead

**Why this exists.** A model predicts the most probable design for a prompt. The most probable design is the average of thousands of templates, so the default is the average, and the average is slop. Every item below is a "probable default". One default alone is harmless; slop is the *combination*: purple gradient + centered hero + three equal glass cards + fade-up on everything.

**How to use it.** Before designing, scan sections 1–9 and write down which defaults you were about to use. Replace each one on purpose (section 12). After building, run the detector tests (section 11).

Contents
1. Page structure and composition
2. Color
3. Typography
4. Components
5. Shape, spacing and detail
6. Imagery and media
7. Motion and interaction
8. Copy and content
9. Code and implementation tells
10. Process-level slop (model behavior)
11. Detector tests
12. Replacement moves

---

## 1. Page structure and composition
- The template skeleton, regardless of brand: navbar → hero → logo strip → three feature cards → "how it works" 1-2-3 → testimonials → pricing (3 tiers) → FAQ → CTA banner → footer.
- Everything centered and symmetric: centered headline, centered paragraph, then a row of equal cards.
- Every section has the same vertical padding (py-20 / py-24) inside the same container (max-w-7xl mx-auto px-4). The rhythm is monotone: no section is tighter, bigger or different.
- Alternating "image left, text right / text left, image right" blocks.
- Bento grid of equal rounded boxes, each with icon + title + gray text.
- Cards for everything: all content sits in bordered boxes. Nothing bleeds off the viewport, overlaps, is cropped, or touches an edge.
- Hero formula: headline + subtitle + two buttons + product screenshot in a browser frame (often tilted) below.
- Sticky blurred navbar: logo left, 4 text links, a filled CTA button right, spanning the full width as a rectangle.
- Footer: 4 link columns, socials, copyright.
- No concept or narrative: the sections are interchangeable and could be reordered without anyone noticing.

## 2. Color
- Purple / indigo / violet → blue / cyan gradients (#6366f1, #8b5cf6, #3b82f6, #06b6d4), or a pink-orange sunset gradient.
- Background is either near-black navy (slate-900, zinc-950) with neon accents, or pure white with gray-50 sections.
- Radial glows and blurred gradient blobs behind the hero; "aurora" backgrounds; dot or grid patterns with a radial mask; decorative noise overlay for no reason.
- Gradient text on the headline (`bg-clip-text text-transparent`).
- Untouched default Tailwind palette; gray-400/500/600 for all secondary text (often low contrast).
- Pure #000 and #fff; or 5–7 unrelated hues; an accent used everywhere, so nothing stands out.
- Color carries no meaning: it is not tied to the brand, product, material or story.
- On dark: `bg-white/5` surfaces with `border-white/10`.

## 3. Typography
- Inter, system-ui, Roboto, Poppins, Space Grotesk, DM Sans or Plus Jakarta as the only family, in 2 weights.
- Headline: 48–72px, bold, tracking-tight, line-height 1.1, centered, two lines, often with one gradient word.
- An "eyebrow" label above the headline: small uppercase, wide tracking, in a pill with a dot, sparkle or emoji.
- Subtitle: 18–20px gray, centered, max two lines.
- A flat scale (text-sm/base/lg/xl/2xl/4xl) with small steps: nothing huge, nothing tiny; hierarchy is made only with weight.
- Display type set with body line-height and default tracking; sizes never tuned per role.
- Bold keywords inside paragraphs; one italic serif accent word as a "designer touch" (heavily overused).
- Headings never break lines on purpose and never mix sizes inside a line.
- Centered multi-line paragraphs with an ugly rag; widows untouched.

## 4. Components
- Glassmorphism by default: `bg-white/5 backdrop-blur border border-white/10 rounded-2xl`.
- Cards: `rounded-2xl shadow-lg p-6/p-8`, `hover:-translate-y-1 hover:shadow-2xl`.
- An icon in a tinted rounded square at the top of each card (Lucide / Heroicons / emoji).
- Badges: "✨ New", "🚀 Launching soon", "Now in beta".
- Buttons: gradient fill with a glow shadow, `hover:scale-105`, an arrow icon that nudges 4px right on hover, and always a primary + outlined secondary pair ("Get started" / "Learn more").
- Inputs: `rounded-lg focus:ring-2 ring-indigo-500`.
- Stat row: "10K+ users · 99.9% uptime · 24/7 support · 4.9★".
- Avatar stack plus "Join 2,000+ teams"; a row of greyed fake logos.
- Testimonial cards: quote, round avatar, name and title, five stars, names like Sarah Chen / John Doe / Alex Johnson.
- Pricing: three tiers, the middle one "Most Popular", ✓ lists, monthly/yearly toggle "Save 20%".
- FAQ accordion with a chevron; tabs with a pill-shaped active indicator.
- Component-library defaults shipped unchanged (shadcn, MUI, Bootstrap look).

## 5. Shape, spacing and detail
- One radius for everything (rounded-xl / 2xl) with no system behind it.
- Spacing is either arbitrary (13px, 17px, 22px) or uniform (`p-6 gap-6` everywhere): no rhythm of tight clusters and big voids.
- 1px gray borders on everything, soft shadows, subtle gradients on cards. Hairlines are never used deliberately as structure.
- Equal-width, equal-height columns. No asymmetry, no overlap, no bleed, no oversized element, no cropped image.
- Everything contained in a 1280px box with 16px side padding. Full-bleed is rare.
- Fixed breakpoints (sm/md/lg) instead of fluid sizing; `100vh` hero hacks.
- Decoration without purpose: floating shapes, sparkles, glowing orbs, grid lines, a divider between every section.
- A bouncing "scroll down" chevron or mouse icon.

## 6. Imagery and media
- Stock / Unsplash / placeholder-service photos; gray boxes or gradient rectangles instead of images.
- Fake dashboard screenshots built from divs; laptop or browser mockups; floating UI cards with invented data.
- Glossy 3D blobs and spheres, generic abstract AI art, "Undraw"-style flat people, isometric illustrations.
- Emoji as icons; one line-icon set, same weight everywhere.
- No art direction: no deliberate crop, grade, scale or perspective. Every image is a rectangle with `rounded-xl` at the same ratio (16:9 or 4:3) and the same size.
- Background video under a flat 50% dark overlay, for no reason.

## 7. Motion and interaction
- Everything fades up on scroll (opacity 0→1, y 20→0, ~0.6s, ease-out) with a 0.1s stagger, on every element.
- `transition-all duration-300 ease-in-out` on every element; `hover:scale-105`; hover lift; hover that only changes color.
- Infinite float / pulse / bounce / spin / marquee as decoration.
- Cursor glow, card spotlight, 3D tilt on cards, shimmer buttons, animated "border beam".
- Number count-up on stats; typewriter or rotating-word headline.
- Smooth-scroll library added with no choreography; mild parallax on one background image.
- No page-load sequence or page transition, or the cliché percentage-counter preloader.
- One easing (ease / ease-in-out / linear) and random durations; no custom cubic-bezier.
- No `prefers-reduced-motion`, no focus states, animations fire once and are never revisited.
- Motion carries no meaning: it is not tied to the concept and tells no story.

## 8. Copy and content
- Headline formulas: "[Verb] your [noun] with AI", "The future of X", "Build faster. Ship smarter.", "X, reimagined", "Everything you need to...", "The all-in-one platform for...", "Built for teams who...".
- Stock vocabulary: elevate, unlock, empower, supercharge, seamless, effortless, streamline, revolutionize, next-generation, cutting-edge, robust, leverage, harness, delve, tapestry, journey, landscape, game-changer.
- Triplets ("Fast. Secure. Scalable.", "simple, powerful, and beautiful"); "not just X, but Y"; em-dash-heavy sentences; "Ready to get started?"; "No credit card required"; "Get started in minutes".
- Title Case On Every Heading; exclamation marks; emoji in headings and bullets.
- Invented specifics: made-up metrics, customers, awards, quotes; lorem ipsum; "Acme Inc"; "John Doe"; "user@example.com".
- The same voice for every brand: no point of view, no humor, no concrete nouns (a place, a year, a person, an object).
- Microcopy: "Learn more" six times, "Submit", "Get started". Nav: Features, Pricing, About, Contact.

## 9. Code and implementation tells
- Tailwind class soup of default scale values: `bg-gradient-to-r from-purple-600 to-blue-600`, `text-gray-600`, `container mx-auto px-4`, `max-w-7xl`.
- shadcn defaults: `rounded-lg border bg-card text-card-foreground shadow-sm`.
- Framer Motion boilerplate on everything: `initial={{opacity:0,y:20}} whileInView={{opacity:1,y:0}} viewport={{once:true}} transition={{duration:0.6}}`, `staggerChildren: 0.1`.
- Components named Hero, Features, Testimonials, Pricing, CTA, Footer in that order; an array of `{icon, title, description}` mapped into identical cards.
- No design tokens or CSS variables: hardcoded, inconsistent colors and sizes; magic numbers; `!important`.
- `transition: all 0.3s ease`; `box-shadow: 0 10px 30px rgba(0,0,0,.1)`; `border-radius: 12px` everywhere; a `.glass` class.
- Fixed px font sizes; only md/lg breakpoints; `100vh` instead of `svh`/`dvh`; overflow and long text not handled.
- Div soup, no semantic tags, no alt text, no `:focus-visible`, `<a>` without `href`, `onClick` on a `div`.
- A heavy library for nothing (three.js for a spinning cube, particles.js backgrounds).
- Leftovers: `TODO`, `console.log`, `href="#"`, hotlinked images, an entire icon library imported.
- One 800-line component, or the opposite: abstraction for its own sake.

## 10. Process-level slop (model behavior)
- Starting from the list of standard sections instead of a concept.
- Adding features nobody asked for, or "improving" the exact details the user gave (their color, font, text).
- Delivering something that looks finished but is half-wired: placeholders, missing states.
- Writing "stunning / modern / premium / award-winning" in the summary instead of making it so.
- Hedging with three safe options instead of making one decision.
- Polishing the wrong thing (shadows, gradients, blur) while hierarchy, scale and composition stay weak.
- Quality drift: following the user's reference at the start and sliding back to defaults by the last section.
- Copying a reference 1:1 (brand name, text, assets) instead of transferring its principles.

## 11. Detector tests
Run these on your own design before delivering.

1. **Swap test.** Replace the brand name and copy with a competitor's. If nothing else has to change, the design is generic.
2. **Ten-prompts test.** Could ten different prompts have produced this same page? If yes, no decision here was specific.
3. **Squint test.** Zoom out or blur. Is there a clear 1-2-3 hierarchy and one focal point per screen? Is the largest text at least 5× the smallest?
4. **Grayscale test.** Does the structure still work without color? Does color carry meaning rather than decoration?
5. **Default count.** Count untouched defaults: stock gradients, glass cards, fade-ups, rounded-2xl everywhere, Inter. More than about 3 means rework.
6. **One-memorable-thing test.** Name what a visitor will remember tomorrow. If you cannot, choose or create one signature moment.
7. **Tension test.** Is there at least one deliberate break of the grid (overlap, bleed, crop, oversize, asymmetry)?
8. **Motion audit.** List every animation. Does each have custom timing and a reason? Anything animated "just because" goes.
9. **Copy test.** Could this sentence appear on any company's site? Rewrite it with a specific noun, place, date or voice.
10. **Numbers test.** Can you point to the token (hex, type size, spacing step, radius) behind every visual value? Arbitrary values mean there is no system.

## 12. Replacement moves
| Default | Do this instead |
|---|---|
| Centered hero + two buttons | Anchor the type to an edge or corner at huge scale with one CTA; or a full-bleed photo/video with the UI on the perimeter and the subject left clear (see `01_Delta_Cafes.md`) |
| Three equal cards | Cards of different sizes with real content, an asymmetric bento, a horizontal story, or a scattered collage |
| Purple/blue gradient | A palette of 2–3 related colors taken from the brand's world (materials, products, places) and one strictly-used accent |
| Inter everywhere | A face with character: condensed display caps, a light grotesque with tight tracking, a high-contrast serif; plus a neutral text sans |
| Fade-up on everything | Choreograph: one primary motion per screen, the rest still; one custom easing; motion tied to the concept |
| Glass cards with glow | Flat or tinted surfaces with hairlines, or a real photograph as the card |
| Icon in a rounded square | Typographic markers (01 / 02 / 03), real objects, photos |
| Stock photos, 3D blobs | Specific archival, product or human photography with art direction (crop, grade, scale); or typography only |
| Generic copy | Concrete nouns, places, dates and a voice that only this brand would use |
| Uniform padding everywhere | Rhythm: tight clusters and big voids; larger gaps where the story changes |
| Full-width navbar rectangle | A floating pill, a split nav, the logo as a physical object (see `01_Delta_Cafes.md`) |
| `hover:scale-105` on buttons | A shape change tied to the component's anatomy, for example a pill that grows around its icon (see `01_Delta_Cafes.md`, CTA) |
| Boxes with 1px borders | Hairlines at low contrast used as structure (progress lines, orbit curves), content bleeding past edges |
