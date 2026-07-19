# UX Rubric — dimension checklist

Read this in Phase 3 to grade each dimension so nothing slips through. These are
prompts for judgement, not a scorecard to fill mechanically. For each, note what
you observed with concrete evidence, then map issues to a severity.

## 1. Usability (can they do the job?)
- Does the primary task complete without the user needing to be taught?
- Are the next steps obvious at each point, or does the user have to guess?
- Are actions where the user expects them (near the thing they act on)?
- Is feedback immediate and clear after every action (loading, success, error)?
- Can the user recover from a wrong turn without starting over?
- Frame-two test: on landing cold, is "what do I do here?" answerable in seconds?

## 2. Readability (can they scan it?)
- Does the eye land on the most important thing first? Is hierarchy real?
- Is text legible — size, weight, contrast — in both light and dark themes?
- Are labels human? (No raw field names, codes, UUIDs, internal identifiers.)
- Is dense data chunked and scannable, or a wall the user must decode?
- Do numbers/statuses/totals read at a glance, correctly formatted?

## 3. Flow (does the journey hang together?)
- Does one step lead naturally to the next, or are there jumps and dead ends?
- Can the user always tell where they are and get back where they came from?
- Are there detours that add clicks without adding value?
- Does the flow match the persona's real mental model of the task?
- Return-to-origin: after cancel/close/back, do they land where they'd expect?

## 4. Interaction (does it respond well?)
- Do clicks, hovers, drags, selections do what the user expects?
- Are targets big enough to hit; is nothing frustratingly fiddly?
- Do controls communicate state (hover, active, selected, disabled, focus)?
- Is anything laggy, janky, or unresponsive under realistic data?
- Do clicks *focus* the user's attention rather than pile on clutter?

## 5. Animation & motion (does it aid or distract?)
- Does motion explain a change (where did this come from, what just happened)?
- Is it fast enough to feel responsive, slow enough to follow?
- Does anything block the user or make them wait on decoration?
- Is it calm at rest, or busy/noisy when nothing is happening?
- Does it degrade gracefully at scale and under reduced-motion?

## 6. Hindrances (what gets in the way?)
- Moments of confusion, hesitation, or "wait, what?"
- Dead ends, missing back-paths, unexplained empty states.
- Data capped/hidden when the user asked to see it whole.
- Anything that made the persona want to give up or leave.

## 7. Good things (what to protect)
- Genuine moments of delight or clarity.
- Places the design made a hard thing feel easy.
- Anything uniquely valuable — the reason-to-visit, if it exists.
List these explicitly so a later refactor doesn't strip them out.
