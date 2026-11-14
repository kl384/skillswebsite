# Verify checklist

Run this before the final answer on medium and large tasks. Most "that's not what I asked" moments are caught here.

Contents
1. Trace against the request card
2. Failure modes and fixes
3. If you can run things
4. If you cannot run things
5. Final report shape

---

## 1. Trace against the request card

Go through the card top to bottom and write a short result for each line:

```
Must 1  ✔ in file/section ...
Must 2  ✔ ...
Must 3  ✘ missing → fixing now
Must NOT 1  ✔ nothing of that kind present
Keep verbatim  ✔ hex values, texts, names match exactly
Implied  ✔ responsive / error states / run instructions
```

Fix every ✘ before answering. Do not report a gap as "could be added later" when it was part of the request.

## 2. Failure modes and fixes

| Failure | How to spot it | Fix |
|---|---|---|
| **Dropped detail** | a color, text, number or name differs from what the user wrote | re-read the original request, copy exact values |
| **Broken negation** | something the user excluded is present | remove it; check again |
| **Placeholders** | `TODO`, `...`, "rest unchanged", "similar to above", lorem ipsum where real text was possible | write the real thing |
| **Invented API / package** | a function, flag, import or version you are not certain exists | use a known option, or state clearly what must be checked |
| **Half-wired** | file imported but not created; component created but never used; function defined but never called; CSS class in styles but not in markup (or the reverse) | search for every name once and confirm both ends exist |
| **Name drift** | the same thing is called differently in two files (ids, props, keys, routes) | pick one name, make all places match |
| **Scope shrink** | "simplified version", missing sections or states that were requested | build the missing part |
| **Scope creep** | features nobody asked for, rewritten parts that were fine | remove, or move to "next step" in the report |
| **Thinning** | the last section or file is much shallower than the first | bring it up to the same level |
| **Not runnable** | missing dependencies, missing entry point, no run command, wrong paths | list deps, add the entry point, give exact commands |
| **Edge cases** | empty data, very long text, tiny screen, first run, bad input | test them mentally or for real; add handling |
| **Silent assumption** | you decided something important and did not say so | add it to the assumptions in the report |

## 3. If you can run things

Do the real check instead of trusting yourself:

- install and build; read the whole error output, not just the first line;
- run the tests if they exist; run the main path by hand if not;
- for web: open the page, look at the console, check a narrow and a wide viewport;
- for scripts: run on a small sample, including one bad input;
- fix what breaks, then run again. Report only what you actually ran ("built successfully", "opened at 390 px and 1440 px") and never claim a check you did not do.

## 4. If you cannot run things

Say so plainly in the report and do a manual trace instead:

1. Start at the entry point.
2. Follow the main path step by step, writing the value of the important variables.
3. Follow one error path and one empty-input path.
4. Check imports, file paths, and that every referenced name exists.

Then tell the user how to run it and what to look for.

## 5. Final report shape

```
<what was built, where>
<how to run / open it>
<assumptions that affect them, 1–3 lines>
<one next step, only if there is a real one>
```

No recap of the process, no list of everything you considered, no self-praise.
