# usability-test

A Claude Code skill that runs a **real user-research pass** on a live product
flow — acting as an end user, not a developer — and hands back a severity-rated
UX report **plus a strategic value assessment**: not just "is this usable?" but
*"why would anyone come here, and come back?"*

Most UX reviews grade the screen in front of them. This one grades the user's
day. It drives your flow live in the browser, fumbles where a real user would
fumble, and tells you the thing product owners actually lose sleep over — whether
a beautiful screen has any reason to be visited at all.

## What it does

- Designs **10–15 task-based test cases** across 8 deliberate categories
  (orientation, core jobs-to-be-done, discovery, reason-to-visit, data-scale,
  edge states, readability, interaction) — and shows you the list before running.
- **Runs each one live in Chrome** as a named persona, capturing screenshots and
  GIFs of the real experience.
- Grades findings by **severity** (Blocker / Major / Minor / Polish).
- Returns a structured report: executive summary, **value assessment**
  (unique value, reason-to-visit verdict, where to add entry points, return-visit
  likelihood), findings table, what's-working, and a **prioritized fix list**.

Two lenses run the whole way through:

- **Use-case-first** — frame one is the "wow"; frame two is the real test:
  *"okay, what do I actually do here?"*
- **Reason-to-visit** — what does this give me that I can't already get where I
  already go? If the honest answer is "a prettier view of the same data," that's
  the headline finding.

## Install

Requires [Claude Code](https://claude.com/claude-code).

```bash
git clone https://github.com/Rob7850/usability-test-skill ~/.claude/skills/usability-test
```

Or download the ZIP and unzip it into `~/.claude/skills/` (the folder must be
named `usability-test`). That's it — Claude Code picks it up automatically.

## Use

Just ask, in plain language:

```
run a usability test on the checkout flow at http://localhost:3000/checkout
```

or invoke it directly with `/usability-test`. It will confirm the target,
personas, and your value hypothesis, ask before opening the browser, propose the
test cases for your sign-off, then run them and write the report.

> **Note:** the skill drives a real browser and always asks permission before
> opening one. It never opens a browser without an explicit yes.

## What you get back

```
# Usability Test — <flow> — <date>
1. Executive summary        ← does it work, read, and is there a reason to visit
2. What we tested           ← personas, value hypothesis, the test-case table
3. Value assessment         ← the strategic layer
4. Findings                 ← severity-sorted table with evidence
5. What's working           ← the good things, so a refactor doesn't strip them
6. Prioritized fix list     ← most-impactful first, quick wins vs. bigger bets
7. Open product questions   ← the calls only a product owner can make
```

## Self-contained — no other skills required

This is one complete package. It carries its own UX evaluation authority, visual
craft lens, test-case method, and browser-driving guide, so it works on a fresh
machine with nothing else installed. The only external requirement is the
Claude-in-Chrome browser extension (a skill file can't ship a browser
extension) — and the skill explains a fallback if it isn't connected.

## Files

- `SKILL.md` — the six-phase methodology Claude follows.
- `references/ux-evaluation-guidelines.md` — the grading authority: 18 UX
  categories, ~99 checks with severities.
- `references/visual-craft.md` — the "intentional vs. templated" visual-quality lens.
- `references/writing-test-cases.md` — how the task-based cases are authored.
- `references/browser-driving.md` — how the flow is driven live in Chrome.

## License

MIT — see [LICENSE](LICENSE).
