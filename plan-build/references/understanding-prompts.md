# Understanding prompts

How to turn a messy human request into something precise enough to build. Read the section you need; you do not have to read all of it every time.

Contents
1. Read twice
2. Extraction buckets
3. Vague words → decisions
4. "Like site/app X"
5. Implied requirements by domain
6. Conflicts and gaps
7. Ask or assume
8. Messy input
9. Long pasted specs, screenshots, earlier context
10. The one-line echo

---

## 1. Read twice

- **Pass 1, literal:** what do the words say? Underline numbers, names, colors, formats, and every negation.
- **Pass 2, intent:** why would someone write this? What would they be pleased to receive, and what would make them say "not that"? A person asking for "a landing page for my coffee shop" wants something they could actually publish, not a wireframe.

Where the two passes disagree, the literal words win for anything specific, and intent fills the gaps around them.

## 2. Extraction buckets

Sort every phrase of the request into one of these. A phrase that fits no bucket is a sign you have not understood it yet.

| Bucket | What goes in | What to do |
|---|---|---|
| Things | nouns: pages, screens, components, files, entities | each becomes something in the plan |
| Behaviors | verbs: "when I click", "auto-skip", "saves" | each becomes logic plus a way to check it |
| Style words | adjectives: "clean", "premium", "fast", "dark" | convert to decisions (section 3) |
| Hard values | numbers, names, hex colors, fonts, sizes, stack, language, platform, exact texts | copy verbatim into the card |
| Negations | "no", "without", "don't", "не", "без", "никаких" | go to Must NOT; recheck at the end |
| Order words | "first", "then", "main thing", "сначала", "главное" | decide plan order and priority |
| Scope words | "just", "only", "for now", "пока", "потом" | do only this turn's part, but do not block the later part |

## 3. Vague words → decisions

A vague word is a request for taste. Do not stay vague and do not ask what "nice" means. Pick one specific, defensible interpretation, commit to it, and write it as numbers or names in the plan. The user can then correct a concrete choice, which is far easier than correcting a mood.

| They say | Ask yourself | Typical commitment |
|---|---|---|
| fast / быстрый | fast at what? | a measurable target: loads in under 1 s, no blocking work over 50 ms, no unnecessary dependencies |
| simple / простой | simple for whom? | fewest screens, steps and options that still do the job; one primary action per screen |
| clean / minimal / чистый | what is removed? | few colors, lots of empty space, one type family, no decoration without purpose |
| beautiful / premium / красивый | which concrete things carry that feeling? | a chosen palette (hex), a font pair, a spacing scale, one signature moment; if a design skill exists, take these from it |
| smooth / плавный | which motion? | one easing curve and a duration range used everywhere (for example 200–400 ms), no abrupt jumps |
| full / полноценный | which parts make it "complete"? | empty, loading and error states, persistence, responsive layout, validation |
| small / mini / небольшой | what is cut? | core path only, one file if possible, no settings screen |
| smart / умный | what exact behavior? | name the actual rule or algorithm instead of "AI-ish" magic |
| normal / обычный | what is the convention? | the most common pattern for this kind of thing, no surprises |
| modern / современный | which current conventions? | current stable tooling and common visual conventions; avoid deprecated APIs |

If the domain has a specialist skill, it decides these. This table is only the fallback.

## 4. "Like site/app X"

"Make it like Apple / Notion / that site" names a feeling, not a spec. Break it down:

1. Pick the 2–4 properties that most likely carry the reference: layout, density, typography, color mood, motion, tone of copy.
2. Say which ones you took ("From X I take: large type, lots of space, slow fades").
3. Do not copy logos, brand names, protected assets or exact wording of the reference. Take the principles, not the pixels.

If you have a screenshot or description of X in the conversation, it is the source of truth over your memory of X.

## 5. Implied requirements by domain

Things the user will assume without saying. Put the relevant ones in the Implied line of the card.

- **Website / web app:** works on phone and desktop; no console errors; sensible semantic HTML; readable contrast; visible focus states; real content instead of "lorem ipsum" where the topic is known; fast first load; a way to run it (commands).
- **UI component:** all states (default, hover, focus, active, disabled, loading, error where relevant); keyboard use; it does not break with very long or very short text; no layout shift.
- **Script / CLI:** clear usage message; handles missing or bad input without a stack trace; never destroys the user's originals (write to a new place by default); reports what it did; works on the stated OS.
- **Game / interactive:** stable frame rate; restart without reload; clear controls shown on screen; no soft-locks.
- **Mod / plugin / extension:** matches the exact version and loader the user named; installation steps; does not crash the host on bad config.
- **Document / text:** matches the audience and tone; structure that can be skimmed; no filler.
- **Data / analysis:** states the source and assumptions; numbers are computed, not estimated; units are labeled.
- **Anything:** secrets are not hard-coded; dependencies are listed; the answer says how to run or use it.

## 6. Conflicts and gaps

**Gaps** (not specified): choose the most common good default for the context and log it under Assumptions. Do not leave a decision implicit.

**Conflicts** (two requirements pull apart):
1. Explicit beats implied, implied beats your own defaults.
2. A later message beats an earlier one, unless it says "also" or "in addition".
3. Between two explicit requirements, the more specific one wins over the more general ("dark theme" + "white hero section" → dark theme with one white hero).
4. Flag the conflict in one line and say which way you went. Never silently drop one side.

## 7. Ask or assume

Ask **only** if both are true:
- a wrong guess would waste a large part of the work, and
- no sane default exists from domain knowledge.

Good reasons to ask: the target platform or stack is unclear and changes everything; two readings produce completely different products; a needed input (file, API key, text) is missing and cannot be invented.

Bad reasons to ask: color choices, layout details, naming, anything you can decide with taste, anything the user already said earlier.

Format: at most 3 questions in one message, each with your default ("If you do not answer, I will use X"). If you cannot ask (one-shot, unattended), assume, state the assumption at the top, and go.

## 8. Messy input

People write fast. Interpret by intent and do not comment on the mess.

- Typos, slang, transliteration, missing punctuation, voice-to-text artifacts, mixed languages ("крч", "че", "итд", "плиз"): read through them.
- Product and tech names spelled wrong: map to the nearest real one; if two are plausible and the choice matters, ask.
- A request written as a stream of thoughts: extract the actions, put them in order, and number them.
- The user switches language mid-message: reply in the language of their own words, not the language of any pasted text.

## 9. Long pasted specs, screenshots, earlier context

- **Long spec or a prompt written for another AI:** every bullet, number and "must" is a requirement. Number them. Do not summarize away details to save space: the details are the point. If the spec is huge, group the requirements by area, but keep every item.
- **Screenshot or image:** list in a few lines what you see (layout, colors, text, components) before planning. It is the source of truth for visuals.
- **Attached files:** read them before planning. Do not assume what is inside from the name.
- **Earlier conversation:** carry over decisions, names, stack and style already chosen. A follow-up like "now make the header sticky" means "in the thing we already built".
- **Multi-turn plans ("first X, later Y"):** do X now, keep the structure ready for Y, and do not build Y early.

## 10. The one-line echo

Start the visible part of your answer with one sentence of how you understood the request, in the user's language ("Понял так: тёмный одностраничник для кофейни, секции меню и контакты, без стоковых шаблонных блоков."). It costs 5 seconds, and it lets the user stop a misunderstanding before any work is done.
