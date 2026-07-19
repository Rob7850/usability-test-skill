# Writing Usability Test Cases (bundled)

How to author the 10–15 task-based cases in the Design phase. Bundled so the
skill can write strong scenarios on its own.

## A test case is a goal, not a click script

The single most common mistake is writing instructions ("click the vendor row,
then click invoices"). That only proves the buttons work. A usability test case
is a **real user with a real goal**, told in their words, with the path left to
them — because *how they try to reach the goal* is the data.

Weak:  "Verify the spend total is visible on the vendor page."
Strong: "You're an AP analyst. Finance just asked why Acme's spend jumped this
quarter. Find out." ← this surfaces navigation, findability, whether the number
means anything, and whether the user can act on it.

## The template

```
TC-<n> · <category> · <persona>
Goal:      <what the persona is trying to achieve, in their own words>
Steps:     <the rough path a real user would take — high level, not scripted>
Success:   <the observable outcome that means they succeeded>
Probes:    <the specific usability/value question this case answers>
```

## Cover these 8 categories deliberately

Design breadth, don't stumble into it. Aim for coverage across all eight; weight
toward whichever matter most for this flow.

1. **Orientation / frame-two** — land cold: in seconds, do I know what this is
   and what to do? (The most important category — never skip it.)
2. **Core jobs-to-be-done** — can the persona finish their primary task, start to
   finish?
3. **Discovery & navigation** — can I find things? Dead ends? Can I always get
   back to where I was?
4. **Reason-to-visit & value** — does this give me something unique? Would I
   return? Where would I naturally *enter* this from?
5. **Data scale & honesty** — with realistic data volume, does it still work, or
   does it silently cap/hide what I asked to see whole?
6. **Empty / edge / error states** — no data, one record, a broken record, a huge
   record — graceful?
7. **Readability & hierarchy** — can I scan it? Is the most important thing the
   most prominent?
8. **Interaction & motion** — do clicks/hovers/animations aid understanding, or
   decorate / distract / lag?

## Personas

Pick 1–3 realistic roles who would (or *should*) use this, each with a concrete
job — "AP analyst chasing an invoice on hold", "procurement lead vetting a new
vendor", "controller closing the month". Real jobs, never "a user". Assign each
test case to the persona it fits.

## Ground them in reality first

Before writing cases, read the relevant code / config / docs so tasks reflect
what the screen actually does and shows — otherwise you invent tasks the product
can't serve, or miss the ones it's built for. This is the one place developer
knowledge is used: to design fair tests. Drop it entirely once execution starts.

## Quality bar for the set

- Every case has an **observable** success criterion — someone else could watch
  the run and agree whether it passed.
- At least 2–3 cases probe **reason-to-visit / value**, not just usability — this
  is what turns a UX report into a product decision.
- Include the unglamorous ones: empty state, the huge record, the permission the
  persona lacks. Edges are where products break.
- **Show the full list to the user and get their sign-off before running.** They
  know scenarios you can't guess — this checkpoint routinely adds the best case
  in the set.
