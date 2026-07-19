# Visual Craft — "intentional vs. templated" (bundled)

A flow can pass every usability check and still look cheap, busy, or
AI-generated. This reference is the lens for **craft** — whether the UI reads as
deliberate and confident (the Linear / Ramp / Vercel / Stripe / Notion lineage)
or as decorated and templated. Bundled so the skill judges craft without needing
any design skill installed.

Use it in the Evaluate phase for the "readability & visual quality" findings.
These are *heuristics for judging an existing UI*, not build rules — but each one
that's violated is usually a real Minor/Major finding because it erodes trust.

## What "intentional" looks like
- **Restraint.** Every element earns its place. Nothing decorative — no element
  present just to fill space or look lively.
- **Hairlines over shadows.** Structure comes from 1px neutral borders, not drop
  shadows on resting elements. Resting drop-shadows read as dated/toy-like.
- **Flat, low-saturation surfaces.** No gradients, glow, or glassmorphism as
  ornament. Neutrals stay truly neutral (not tinted blue/warm).
- **One accent, used sparingly.** At most one accent color, and only on primary
  actions / focus / progress — never as fill on cards, headers, or chrome. Black
  is a perfectly good "accent."
- **Clear type hierarchy in two weights.** 400 for prose, 500–600 for emphasis.
  Headings clearly outrank body. Weight 700 in chrome and italic UI labels both
  read as amateur.
- **Numerics aligned and tabular.** IDs, counts, money, timestamps in a
  monospaced / tabular-figure treatment so columns line up.
- **Consistent spacing rhythm.** A visible base unit (4px) and a repeating
  rhythm — not arbitrary margins that differ per section.
- **Density matched to the surface.** Compact for tables/dashboards, comfortable
  for forms/detail, spacious for marketing/onboarding — and not mixed on one
  screen.
- **Sentence case copy.** Labels are sentence case, one concept per button
  ("Save changes"), eyebrows are category nouns, titles are the specific
  instance. No Title Case Sandwiches, no emoji/exclamation in product chrome.

## Tells of "templated / AI-generated / cheap" (flag these)
- Rounded-everything: pill buttons, rounded cards, rounded inputs, circular
  avatars where the system is otherwise square. Inconsistent corner radii.
- Drop shadows on every resting card; heavy elevation used as decoration.
- Saturated full-bleed gradient heroes (especially purple/pink), glow, glass.
- Decorative illustrations, clip art, or an emoji next to every label/menu item.
- An icon beside every field label or list item (icons should carry meaning the
  label can't — close, status, expand, drag — not garnish).
- Multiple accent colors competing on one screen.
- **Empty rectangles / dead space.** Two side-by-side panes at unequal height
  leaving a blank box beneath the shorter one; an empty-state floating as a small
  centered card in a large white void instead of filling its footprint. This is
  the single most common "looks broken" tell.
- **Orphaned half-width fields** — a lone field sitting in half a row with dead
  space beside it, instead of spanning full width.
- Disabled inputs used as a "read-only view" (values should render as
  label-over-value pairs, empty = em-dash, never a greyed box).
- Truncating data with an ellipsis where it could simply wrap and be readable.
- Animated number counters, animated tab indicators, parallax, staggered list
  reveals — motion as spectacle rather than explanation.
- Bold + italic + color stacked on the same element.
- Tooltips explaining what a clearly-labelled control already says.

## How to score craft
For each screen, ask: *does this look like a team obsessed over it, or like a
template filled in?* Name the specific tells you see, tie each to a finding, and
weight them by how much they undercut the user's trust in the product. Craft
issues are rarely Blockers on their own, but a pile of them is what makes a
product feel unfinished — say that plainly in the report if it's the case.
