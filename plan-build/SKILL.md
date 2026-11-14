---
name: plan-build
description: Universal "understand → plan → build → verify" workflow for any build task (websites, apps, UI components, scripts, games, mods, documents), written to work on any AI model, not only Claude. Use this whenever the user asks to make, build, create, code, design, write or implement something non-trivial, sends a long, vague or multi-part request, pastes a spec or a prompt to execute, says things like "сделай", "собери", "напиши", "build me", "make me", or when the result has to match many specific details. It makes the model decode the request precisely (explicit and implicit requirements, vague words, negations, ambiguity), write a short concrete plan, build step by step from that plan, and check the result against the original request before answering. Use it even if the user never says "plan".
---

# plan-build

Most bad results come from two failures, not from lack of skill: the model **misread the request** (dropped a detail, ignored a "no X", guessed wrong on a vague word), or it **started typing without a plan** and drifted halfway through. This skill fixes both with one loop:

```
UNDERSTAND  →  PLAN  →  BUILD  →  VERIFY  →  REPORT
```

It is plain instructions. It does not depend on any specific tool, so it works in a chat with no tools at all, in a coding agent, or pasted into a system prompt / rules file of any model.

**Language:** answer in the language the user wrote in. Keep code, file names and identifiers in English unless asked otherwise.

**Write things down.** Every phase below produces a short written artifact (request card, plan, checklist). Do not keep them "in your head". Writing them out is what makes a model actually follow them 20 steps later, and weaker models need this most.

---

## Step 0: Size the task

| Size | Example | What to do |
|---|---|---|
| Tiny | one function, a one-line fix, a rename | One sentence of interpretation, then build. Skip the plan. |
| Medium | a component, a script, a single page | Compact request card + plan of 4–8 lines. |
| Large | a full site, an app, a multi-file project, a long spec | Full request card + full plan. Build in stages. |

When unsure, treat it as medium. Never skip UNDERSTAND, even for tiny tasks, because a wrong reading is the most expensive mistake.

---

## Phase 1: UNDERSTAND

Read the request twice. First for what it literally says, then for what the person would be happy to receive. Then fill in the request card:

```
REQUEST CARD
Goal:        one sentence, what exists when this is done
Must:        numbered list of everything explicitly asked (user's own words)
Must NOT:    every negation and exclusion ("no", "without", "не", "без")
Implied:     what any competent person in this domain would assume
Keep verbatim: names, numbers, colors, fonts, texts, stack, language, platform
Assumptions: A1, A2... each with a one-line reason
Blocking questions: only if truly needed (see below)
```

Rules that matter most:

- **Every phrase of the request lands in a bucket.** Nothing is "just flavor". Adjectives are requests for decisions (see `references/understanding-prompts.md`, section on vague words).
- **Negations are the most violated requirements.** Put each one in Must NOT, and check it again at the end.
- **Details the user gave are not yours to improve.** If they said a color, a name, a text, a stack, use exactly that. Fill gaps; never override choices.
- **Do not shrink or inflate the scope.** No "simplified version" unless asked. No extra features that were not requested. Small obviously-expected things (responsive layout, empty and error states, run instructions) belong to Implied.
- **Carry context.** Decisions already made earlier in the conversation stay made. Do not re-ask them.

### Ask or assume?

Ask only when **both** are true: a wrong guess would waste a large part of the work, **and** you cannot pick a sane default from domain knowledge. Then:

- Ask at most 3 questions, in one message.
- Give each question your default: "If you do not answer, I will do X."
- Everything else you decide yourself and list under Assumptions.

If nobody can answer (unattended run, one-shot prompt), do not stop. Pick the most likely reading, put a line at the top saying which one, and continue.

Show the user a compact version of the card: one-line interpretation ("Понял так: ..."), the assumptions that matter, and questions if any. The full card is your working memory.

For decoding techniques (messy input, slang, "like site X", conflicting requirements, long pasted specs, screenshots) read `references/understanding-prompts.md`. Read it whenever the request is vague, long, or you feel unsure about what is wanted.

---

## Phase 2: PLAN

```
PLAN
Approach:  1–3 sentences: structure/stack and why
Decisions: concrete values you are committing to (see below)
Steps:
  1. <what> → produces: <file/thing> → done when: <observable check>
  2. ...
  N. Verify against the request card
Risks:     what could go wrong or is unknown
```

Rules:

- **Every Must maps to a step.** If a requirement has no step, the plan is incomplete.
- **Order for early feedback.** A working skeleton that runs end to end comes first. Depth comes second. Polish comes last. A half-built project with everything half-done is worse than a finished smaller core.
- **Turn adjectives into numbers and names.** "Fast", "clean", "spacious", "smooth" are not buildable. Under Decisions write the actual values: sizes, spacing scale, durations, limits, colors with hex, font names, file structure. Decide once here, so the build stays consistent.
- **Specialist skills win over defaults.** If another skill is available for this domain (for example a design, 3D, scroll or framework skill), read it now and take decisions from it. Generic defaults apply only where it is silent.
- Keep the plan short. It is a checklist for yourself, not an essay. The user should be able to read it in 20 seconds.

Show the plan, then continue straight into BUILD in the same reply. Stop for approval only if there are blocking questions, or the user asked to approve the plan first.

---

## Phase 3: BUILD

- **Follow the plan in order.** After each step, tick it off in your head or in the task list if you have one.
- **Skeleton first, then fill.** Get something that runs, then deepen it. For large work, build file by file or section by section and keep names consistent.
- **Complete, runnable output.** No `TODO`, no `...rest of the code`, no pseudo-code, no "similar to above". If it is too long for one reply, split into clearly labeled parts and say what comes next.
- **Do not invent.** Use only libraries, APIs, flags and versions you are sure exist. If unsure, use the safer well-known option or say what needs checking.
- **Stay inside the fence.** Build what is on the card. If you spot something valuable that was not asked, mention it in the report instead of building it.
- **If the plan turns out wrong, fix the plan visibly** (one line: "Changing step 3 because ...") and continue. Never drift silently.
- **Keep quality level constant.** The last file or section must be as thorough as the first. Models tend to thin out toward the end; compare the end against the start before finishing.
- **No file tools?** Output each file as its own code block with the path as a header, and add the exact commands to run it.
- **Can run things?** Run them (build, tests, lint, open the page). See VERIFY.

---

## Phase 4: VERIFY

Do not skip this. It is the cheapest way to catch the mistakes that make users say "that's not what I asked".

1. Walk the request card line by line. For each Must, point to where it is satisfied. Fix gaps now.
2. Re-check every Must NOT.
3. Compare Keep-verbatim items character by character against the output.
4. Run it if you can; if you cannot, trace the main path by hand (entry point → each step → output).
5. Scan for the common failures: placeholders, missing files or imports, mismatched names between files, invented APIs, scope creep or shrink, thin last section.

The full checklist is in `references/verify-checklist.md`. Read it before the final check on medium and large tasks.

---

## Phase 5: REPORT

Keep it short. The user wants the result, not the diary.

- What was built, and where (file names or the code above).
- How to run or open it, if relevant.
- Assumptions that actually affect the user (not all of them), so they can correct you in one message.
- One natural next step, only if there is a real one.

Do not recap the steps you took, and do not apologize for or praise your own work.

---

## Reference files

- `references/understanding-prompts.md`: how to decode requests: extraction buckets, vague words → decisions, implied requirements per domain, conflicts, ask-vs-assume, messy input, "like site X".
- `references/verify-checklist.md`: final check, failure modes with fixes, what to do with and without the ability to run code.
- `references/examples.md`: two worked examples (a vague Russian site request and an English script request) showing a request card and a plan. Read when the format is unclear.
