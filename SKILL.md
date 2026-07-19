---
name: usability-test
description: "Run a real user-research pass on a live flow, screen, or module in the browser — acting as an end user, not a developer. Use when the user wants to usability-test a feature, do user research, validate a flow end-to-end, understand what value a screen provides, or asks 'test this as a user', 'run a usability test', 'is this flow good', 'what's the UX like', 'do user testing on X'. Produces task-based test cases (10–15), drives them live in Chrome, and returns a severity-rated UX report with a prioritized fix list AND a strategic value assessment (reason-to-visit, stickiness, missing entry points) — not just a holistic critique."
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

---

## The mindset that makes this skill work

The trap in UX evaluation is grading the screen you're looking at ("nice
layout, good contrast") instead of the *user's day*. Fight that. Two lenses run
the whole way through:

- **Use-case-first.** Frame one is the "wow" — the thing loads and looks
  impressive. Frame two is the real test: **"okay, what do I actually do here?"**
  If a user can't answer that in a few seconds, the screen has failed regardless
  of how good it looks. Every test case must probe frame two, not frame one.

- **Reason-to-visit.** For each screen ask: *what does this give me that I can't
  already get somewhere I already go?* If the honest answer is "a prettier view
  of data I can see elsewhere," that's the single most important finding in the
  report — because it predicts the module gets built, demoed, and then never
  opened again. Look actively for the unique value, and for the **entry points**
  that would pull users in from the tools they already live in (e.g. a "see all
  connections" action on a document detail page that lands them here in context).

Behave like the persona, not like someone who built the thing. Don't use inside
knowledge to shortcut a task — if a real user would fumble, fumble, and record
it. The fumble *is* the finding.

---

## Workflow

### Phase 0 — Scope, ground, and get the go-ahead

Do not open the browser yet. First:

1. **Pin the target.** Confirm the exact flow/module, its URL, the login/tenant
   to use, and — critically — **the user's value hypothesis**: what do *they*
   think this is for and who is it for? Their answer becomes the yardstick you
   test against. If they haven't said, ask.

2. **Pick personas.** 1–3 realistic roles who would (or should) use this, each
   with a concrete goal ("AP analyst chasing why an invoice is on hold",
   "procurement lead vetting a new vendor"). Real jobs, not "a user".

3. **Ground yourself in the intended value.** Read the relevant code / config /
   docs so the tests are grounded, not guessed — what the screen is *supposed*
   to do, what data it shows, what actions exist, what it links to. This is the
   one place you use developer knowledge: to design fair tests. You drop it the
   moment testing starts.

4. **Confirm the stack is up and get explicit browser permission.** State which
   dev stack must be running and ask the user to confirm it's live. Then **ask
   for explicit go-ahead before launching Chrome** — never open the browser
   without a clear yes in this session. (If Chrome tools are deferred, load them
   with a single `ToolSearch` batch: `tabs_context_mcp, navigate, computer,
   read_page, tabs_create_mcp, gif_creator`, plus `read_console_messages` if you
   expect to debug.)

### Phase 1 — Design the test cases (10–15, task-based)

Write **10–15** task-based cases — a real user goal, not a click instruction.
"Verify the vendor spend total is legible" is a checkpoint; **"You're an AP
analyst who just got asked why Acme's spend jumped — find out"** is a task. Tasks
surface the flow; checkpoints only confirm a pixel.

Cover these categories deliberately so breadth is designed, not accidental.
Aim for coverage across all of them; weight toward whichever matters most for
this flow:

| # | Category | The question it probes |
|---|----------|------------------------|
| 1 | **Orientation / frame-two** | Land cold — in seconds, do I know what this is and what to do? |
| 2 | **Core jobs-to-be-done** | Can the persona complete their primary task, start to finish? |
| 3 | **Discovery & navigation** | Can I find things? Any dead ends? Can I always get back? |
| 4 | **Reason-to-visit & value** | Does this give me something unique? Would I return? Where would I *enter* from? |
| 5 | **Data scale & honesty** | With realistic data volume, does it still work — or does it cap/hide what I asked to see whole? |
| 6 | **Empty / edge / error states** | No data, one record, broken record, huge record — graceful? |
| 7 | **Readability & hierarchy** | Can I scan it? Is the most important thing the most prominent? |
| 8 | **Interaction & motion** | Do clicks/hovers/animations aid understanding or just decorate / distract / lag? |

Each test case is written as:

```
TC-<n> · <category> · <persona>
Goal:      <what the persona is trying to achieve, in their words>
Steps:     <the path a real user would take — high level, not scripted clicks>
Success:   <the observable outcome that means they succeeded>
Probes:    <the specific usability/value question this case answers>
```

**Show the full test-case list to the user before running.** This is a natural
checkpoint — they'll often add a scenario you'd never guess. Wait for their nod.

### Phase 2 — Run each case as the user

Drive the flow live. For every case:

- Perform the task the way the persona would. Narrate the lived experience as you
  go: where you looked first, what you expected, where you hesitated, what
  confused you, what delighted you.
- **Capture evidence** — screenshots at key moments, and a GIF for any multi-step
  flow worth showing back. Name files by what they show.
- Record the outcome against **Success**, and note anything off-script (a lag, a
  mislabel, a moment of "wait, where am I?").
- Watch for the two lenses continuously: did frame-two land? did you find a
  reason to come back / an entry point that's missing?

If the browser genuinely blocks (2–3 failed attempts, no response, a dialog),
stop and report what you tried — don't loop.

### Phase 3 — Grade & analyse

For each finding assign a **severity**, so the fix list is triageable rather than
a flat wall of notes:

- **Blocker** — user cannot complete the task, or would leave.
- **Major** — completes but with real friction, confusion, or wrong mental model.
- **Minor** — noticeable rough edge, low cost to the user.
- **Polish** — refinement; nice-to-have.

Then step back and answer the **strategic value questions** for the flow as a
whole (this is the part product owners care about most):

- What is the genuine, unique value here vs. what users can already get elsewhere?
- What's the *reason to visit* — and is it strong enough that people will come
  unprompted, or does it need entry points pushed from other modules?
- Where should those entry points live (which existing screens/documents should
  offer an action that lands the user here, in context)?
- Would the persona come back next week? Why / why not?
- Consult `references/ux-rubric.md` for the detailed dimension checklist
  (usability, readability, flow, interaction, animation) to make sure nothing's
  missed.

### Phase 4 — Report

Write the report to a markdown file (default: the scratchpad or, if the user
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
(sorted Blocker → Polish)

## 5. What's working (keep these)
<the genuinely good things — so they don't get refactored away>

## 6. Prioritized fix list
Numbered, most-impactful first. Each: the change, the finding(s) it resolves,
rough effort. Separate quick wins from bigger bets.

## 7. Open product questions
<decisions for the product owner — scope calls, value bets, things testing
surfaced that need a human call>
```

Offer to also render the report as a shareable Artifact if the user wants a
visual version, but the markdown file is the source of truth.

---

## Guardrails

- **Never open the browser without an explicit yes this session.** The stack must
  be running; ask, don't assume.
- **Test as the user, not the builder.** Drop developer knowledge once Phase 2
  starts — a shortcut only you know about hides a real user's dead end.
- **Don't grade the screen — grade the user's day.** A pretty screen nobody has
  a reason to open is a finding, not a pass.
- **Never cap what the user asked to see whole.** If a task is "see all of X" and
  the UI silently shows 30 of 500, that's a Major finding, not a detail.
- **Be honest about weak value.** The most useful thing this skill can say is
  "this is lovely and I'm not sure anyone will come here — here's how to fix
  that." Say it plainly.
