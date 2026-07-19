---
name: usability-test
description: "Run a complete user-research pass on a live flow, screen, or module in the browser — acting as an end user, not a developer. Use when the user wants to usability-test a feature, do user research, validate a flow end-to-end, understand what value a screen provides, or asks 'test this as a user', 'run a usability test', 'is this flow good', 'what's the UX like', 'do user testing on X'. This is a SELF-CONTAINED package: it carries its own UX evaluation guidelines, visual-craft lens, test-case method, and browser-driving guide — it needs no other skill installed. Produces 10–15 task-based test cases, drives them live in Chrome, and returns a severity-rated UX report with a prioritized fix list AND a strategic value assessment (reason-to-visit, stickiness, missing entry points)."
user-invocable: true
---

# Usability Test

Run a genuine user-research pass on a live product flow. You are not reviewing
code and you are not admiring the design — you are **an end user trying to get a
job done**, narrating every hesitation, dead end, and moment of delight, then
turning that into a report the product owner can act on.

The output is two things at once:
1. **A usability report** — does the flow work, read well, feel good?
2. **A value assessment** — *why would a user come here at all, and come back?*
   A screen can be beautiful and usable and still be a place nobody visits. This
   second layer is the one product owners actually lose sleep over, so it is a
   first-class part of every run, never an afterthought.

## This is a self-contained package

Everything needed to run a full usability test is **bundled in `references/`** —
you do not need `ui-ux-pro-max`, `saas-design`, an SDLC skill, or any other skill
installed. Read the bundled file at the phase noted below:

| File | What it carries | Read it in |
|---|---|---|
| `references/writing-test-cases.md` | How to author task-based cases + the 8 categories | Design phase |
| `references/browser-driving.md` | How to drive the flow in Chrome as the user | Execute phase |
| `references/ux-evaluation-guidelines.md` | **The grading authority** — 18 UX categories, ~99 checks with severities | Evaluate phase |
| `references/visual-craft.md` | The "intentional vs. templated" lens for visual quality | Evaluate phase |

The only thing a skill file can't ship is the **Claude-in-Chrome browser
extension** (it exposes the `mcp__claude-in-chrome__*` tools). If it isn't
connected, `references/browser-driving.md` explains the fallback.

## The mindset that makes this work

The trap in UX evaluation is grading the screen in front of you ("nice layout,
good contrast") instead of the *user's day*. Fight that. Two lenses run the whole
way through — they outrank any single checklist item:

- **Use-case-first.** Frame one is the "wow" — it loads and looks impressive.
  Frame two is the real test: **"okay, what do I actually do here?"** If a user
  can't answer that in a few seconds, the screen has failed regardless of how
  good it looks.
- **Reason-to-visit.** For each screen ask: *what does this give me that I can't
  already get somewhere I already go?* If the honest answer is "a prettier view
  of data I can see elsewhere," that's the single most important finding — it
  predicts the module gets built, demoed, and then never opened again. Look
  actively for the unique value, and for the **entry points** that would pull
  users in from the tools they already live in (e.g. a "see all connections"
  action on a document detail page that lands them here in context).

Behave like the persona, not like someone who built the thing. Don't use inside
knowledge to shortcut a task — if a real user would fumble, fumble, and record
it. The fumble *is* the finding.

---

## Workflow — the usability-testing lifecycle

Six phases. Don't skip the sign-off checkpoints — they're where the test earns
the operator's trust.

### Phase 1 — Scope & plan

Do not open the browser yet.

1. **Pin the target.** Confirm the exact flow/module, its URL, the login/tenant
   to use, and — critically — **the value hypothesis**: what does the owner think
   this is for and who is it for? Their answer becomes the yardstick. If unstated,
   ask.
2. **Pick personas.** 1–3 realistic roles with concrete goals (see
   `references/writing-test-cases.md` → Personas).
3. **Ground yourself.** Read the relevant code / config / docs so tests reflect
   what the screen actually does — the one place developer knowledge is used, and
   dropped the moment testing starts.
4. **Confirm the stack is up and get explicit browser permission.** State which
   dev stack must be running and ask the operator to confirm it's live. Then
   **ask for an explicit go-ahead before launching Chrome** — never open the
   browser without a clear yes in this session.

### Phase 2 — Design the test cases (10–15)

Read `references/writing-test-cases.md` and write **10–15 task-based cases** — a
real user goal, not a click script — with deliberate coverage across the 8
categories (orientation/frame-two, core jobs, discovery, reason-to-visit,
data-scale, edge states, readability, interaction).

**Show the full list to the operator and wait for sign-off before running.** They
routinely add the best case in the set.

### Phase 3 — Execute (run each case as the user)

Read `references/browser-driving.md`. Drive the flow live. For every case:
perform the task the way the persona would, narrate the lived experience, capture
screenshots + a GIF of anything multi-step, and record the outcome against
**Success** plus anything off-script (a lag, a mislabel, a "wait, where am I?").
Watch the two lenses continuously.

### Phase 4 — Evaluate & grade

Grade every finding against the **bundled authority**:
`references/ux-evaluation-guidelines.md` (the 18 categories / ~99 checks) for
usability, accessibility, readability, interaction, and motion; and
`references/visual-craft.md` for visual quality. **Every severity rating should
trace to a named guideline or an observed user failure — never to unsupported
taste.**

Assign each finding a severity so the fix list is triageable:
- **Blocker** — user cannot complete the task, or would leave.
- **Major** — completes but with real friction, confusion, or wrong mental model.
- **Minor** — noticeable rough edge, low cost to the user.
- **Polish** — refinement; nice-to-have.

Then answer the **strategic value questions** for the flow as a whole:
- What is the genuine, unique value here vs. what users get elsewhere?
- What's the reason-to-visit — strong enough that people come unprompted, or does
  it need entry points pushed from other modules?
- Where should those entry points live (which existing screens/documents should
  offer an action that lands the user here, in context)?
- Would each persona come back next week? Why / why not?

### Phase 5 — Report

Write the report to a markdown file (default: the scratchpad or, if the operator
keeps research docs outside the repo, their docs folder — ask if unsure; never
commit it into a code repo unprompted). Use this structure exactly:

```
# Usability Test — <flow name> — <date>

## 1. Executive summary
<3–6 sentences: does it work, does it read, and — the headline — is there a
real reason to visit? Lead with the single most important takeaway.>

## 2. What we tested
- Personas, goals, and the value hypothesis being validated
- The 10–15 test cases in a compact table (id · persona · goal · result)

## 3. Value assessment  ← the strategic layer
- Unique value vs. what users get elsewhere
- Reason-to-visit verdict (strong / needs entry points / weak) + why
- Recommended entry points from other modules (where + what action)
- Return-visit likelihood per persona

## 4. Findings
Table: id · severity · category · what happened · why it matters · evidence
(sorted Blocker → Polish; each severity traceable to a guideline or a failure)

## 5. What's working (keep these)
<the genuinely good things — so they don't get refactored away>

## 6. Prioritized fix list
Numbered, most-impactful first. Each: the change, the finding(s) it resolves,
rough effort. Separate quick wins from bigger bets.

## 7. Open product questions
<decisions for the product owner — scope calls, value bets, things testing
surfaced that need a human call>
```

### Phase 6 — Close

Offer to render the report as a shareable Artifact if the operator wants a visual
version (the markdown file stays the source of truth), and confirm any
follow-ups. Note anything that couldn't be tested (a blocked path, missing data,
the extension being unavailable) so the coverage is honest.

---

## Guardrails

- **Self-contained by design.** Grade against the bundled `references/`, not
  against skills that may not be installed. Don't tell the operator to install
  anything except (if needed) the Claude-in-Chrome extension.
- **Never open the browser without an explicit yes this session.** The stack must
  be running; ask, don't assume.
- **Test as the user, not the builder.** Drop developer knowledge once Phase 3
  starts — a shortcut only you know about hides a real user's dead end.
- **Don't grade the screen — grade the user's day.** A pretty screen nobody has a
  reason to open is a finding, not a pass.
- **Never cap what the user asked to see whole.** If a task is "see all of X" and
  the UI silently shows 30 of 500, that's a Major finding, not a detail.
- **Every verdict is grounded.** "UX is strong" is only earned once it's checked
  against the bundled guidelines — never from taste alone.
- **Be honest about weak value.** The most useful thing this skill can say is
  "this is lovely and I'm not sure anyone will come here — here's how to fix
  that." Say it plainly.
