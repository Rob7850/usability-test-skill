# UX Evaluation Guidelines (bundled — the grading authority)

This is the standard the usability test grades against. It is **bundled into the
package** so the skill is fully self-contained — it needs no other skill
installed to judge UX quality. Grounded in established UX practice (Nielsen
heuristics, WCAG, Apple HIG, Material) and organised as 18 evaluation categories
with concrete thresholds and a severity for each check.

**How to use it:** in the Evaluate phase, walk every category against what you
observed while running the tasks. When something violates a check, record it as a
finding and inherit the severity below (adjust up/down if the real user impact
differs). A verdict like "readability is good" is only earned once you've checked
it against the Typography, Accessibility, and Content categories here — never
from taste alone.

Severities: **High** = blocks or badly misleads a user · **Medium** = real
friction · **Low** = polish.

---

## 1. Navigation
- **Active location** — the current page/section is visually indicated (color, underline). Ambiguous "where am I" = **Medium**.
- **Back behaviour** — browser/app back works predictably; history preserved, not replaced. Broken back = **High**.
- **Deep linking** — the URL reflects the current view/state so it can be shared/reloaded. Static URL for dynamic content = **Medium**.
- **Breadcrumbs** — present on hierarchies 3+ levels deep; absent there = **Low–Medium**.
- **Sticky nav** — a fixed header never obscures content beneath it. Overlap = **Medium**.
- **Smooth in-page scroll** — anchor jumps transition rather than snapping. Jarring jump = **Low**.

## 2. Animation & motion
- **Restraint** — 1–2 key elements animate per view, not everything. Motion everywhere = **High**.
- **Duration** — micro-interactions 150–300ms; anything >500ms for UI feels sluggish = **Medium**.
- **Reduced motion** — honours `prefers-reduced-motion`. Ignoring it = **High** (accessibility).
- **Loading feedback** — async work shows a skeleton/spinner, never a frozen or blank UI = **High**.
- **Hover ≠ tap** — primary actions work on touch, not hover-only = **High**.
- **Continuous motion** — infinite animation only for loaders, never decoration = **Medium**.
- **Easing** — ease-out entering / ease-in leaving; linear UI motion feels robotic = **Low**.

## 3. Layout
- **No layout shift** — space is reserved for async content/images (aspect-ratio, fixed height). Content jumping = **High**.
- **Z-index sanity** — nothing important is hidden behind a stacking-context conflict; no `z-[9999]` arms race = **Medium–High**.
- **Overflow** — content isn't clipped by a blind `overflow:hidden`; it scrolls or wraps = **Medium**.
- **Readable measure** — text blocks capped ~65–75ch, not full-viewport-width paragraphs = **Medium**.
- **Fixed elements** — multiple fixed/sticky elements don't overlap or trap content = **Medium**.
- **Mobile viewport height** — uses `dvh`/safe areas, not raw `100vh` that breaks under mobile browser chrome = **Medium**.

## 4. Touch (mobile/tablet)
- **Target size** — interactive targets ≥ 44×44px. Tiny tap targets = **High**.
- **Target spacing** — ≥ 8px gap between adjacent targets = **Medium**.
- **Tap latency** — `touch-action: manipulation` (no 300ms delay); default lag = **Medium**.
- **Gesture conflicts** — custom gestures don't fight system swipes/back = **Medium**.
- **Accidental refresh** — pull-to-refresh disabled where it isn't wanted = **Low**.
- **Haptics** — used for confirmations, not every tap = **Low**.

## 5. Interaction
- **Focus states** — visible focus ring on every interactive element; never `outline:none` with no replacement = **High**.
- **Loading buttons** — disabled + spinner during async to prevent double-submit = **High**.
- **Error feedback** — failures show a clear message near the problem; no silent failure = **High**.
- **Destructive confirm** — delete/irreversible actions confirm first (inline preferred over modal) = **High**.
- **Hover states** — clickable things change on hover + show pointer cursor = **Medium**.
- **Active/pressed states** — immediate visual feedback on press = **Medium**.
- **Disabled clarity** — disabled ≠ enabled visually (reduced opacity + not-allowed cursor) = **Medium**.
- **Success feedback** — completed actions confirm (toast/checkmark/visual change) = **Medium**.

## 6. Accessibility
- **Color contrast** — body text ≥ 4.5:1 against its background. Low contrast = **High**.
- **Not color-alone** — status/meaning carried by icon/text too, not just red/green = **High**.
- **Alt text** — meaningful images have descriptive alt; missing on content images = **High**.
- **ARIA names** — icon-only buttons have `aria-label`; unlabeled icon buttons = **High**.
- **Keyboard reachable** — all functionality works by keyboard; tab order matches visual order; no traps = **High**.
- **Form labels** — every input has an associated `<label>`, not placeholder-as-label = **High**.
- **Announced errors** — errors use `role=alert`/`aria-live`, not visual-only = **High**.
- **Heading hierarchy** — sequential h1→h2→h3, not skipped for styling = **Medium**.
- **Semantic structure** — real landmarks (`nav`/`main`/`article`), not div soup = **Medium**.
- **Skip link** — nav-heavy pages offer "skip to content" = **Medium**.
- **Motion sensitivity** — no forced parallax/scroll-jacking; respects reduced-motion = **High**.

## 7. Performance (observed, not just measured)
- **Image weight** — right-sized, modern format (WebP/AVIF); no 4000px image in a 400px slot = **High**.
- **Lazy loading** — below-fold media/content loads on demand = **Medium**.
- **Font loading** — `font-display: swap` with a matched fallback; no invisible-text flash or shift = **Medium**.
- **Bundle/render blocking** — critical CSS inlined, non-critical JS async/defer; interaction not stalled = **Medium**.
- **Caching** — repeat visits are fast = **Medium**.
- **Perceived speed** — anything >300ms shows progress; the UI never *feels* frozen = **High**.

## 8. Forms
- **Visible labels** — a persistent label above/beside each input; placeholder is never the only label = **High**.
- **Submit feedback** — submit → loading → clear success/error; never a click with no response = **High**.
- **Error placement** — errors appear under the offending field, not only a lump at the top = **Medium**.
- **Inline validation** — validate on blur, not only on submit = **Medium**.
- **Correct input types / keyboards** — `type=email/tel/number`, `inputmode` for mobile keyboards = **Medium**.
- **Required indicators** — required fields are marked = **Medium**.
- **Input affordance** — inputs look interactive (border/background), not like plain text = **Medium**.
- **Password visibility** — a show/hide toggle exists = **Medium**.
- **Autofill** — sensible `autocomplete`; not blanket `autocomplete=off` = **Medium**.

## 9. Responsive
- **No horizontal scroll** — content fits the viewport width on mobile = **High**.
- **Readable mobile text** — body ≥ 16px on mobile = **High**.
- **Touch-friendly at mobile widths** — targets grow, don't stay desktop-tiny = **High**.
- **Viewport meta** — `width=device-width, initial-scale=1` present = **High**.
- **Images scale** — `max-width:100%`, no fixed-width overflow = **Medium**.
- **Tables** — wide tables scroll in a wrapper or become cards, never break layout = **Medium**.
- **Breakpoints** — holds at 320/375/414/768/1024/1440 = **Medium**.

## 10. Typography
- **Body contrast** — dark-enough body text; no gray-on-gray = **High**.
- **Line height** — body 1.5–1.75; not cramped, not airy = **Medium**.
- **Line length** — ~65–75 characters per line = **Medium**.
- **Type scale** — a consistent modular scale, not arbitrary sizes = **Medium**.
- **Heading clarity** — headings clearly outrank body by size/weight = **Medium**.
- **No load shift** — fallback font reserves space so text doesn't reflow = **Medium**.

## 11. Feedback
- **Loading indicators** — spinner/skeleton for any wait >300ms = **High**.
- **Empty states** — "no content" screens explain and offer an action, never blank white space = **Medium**.
- **Error recovery** — errors give a next step (retry/help), not just a message = **Medium**.
- **Progress** — multi-step flows show "step 2 of 4" or a bar = **Medium**.
- **Confirmation** — successful actions get a brief confirmation = **Medium**.
- **Toasts** — auto-dismiss (3–5s); a toast reports an outcome, it never enforces a rule the UI could have prevented = **Medium**.

## 12. Content
- **Graceful truncation** — long text clamps with an expand affordance; layout never breaks = **Medium**.
- **Number formatting** — thousands separators / abbreviations (1,234 / 1.2K), not raw digit runs = **Low**.
- **Date formatting** — relative or locale-aware ("2 hours ago"), not ambiguous 01/02/03 = **Low**.
- **Realistic content** — no lorem ipsum standing in for real data at review time = **Low**.

## 13. Search
- **Autocomplete** — predictions as the user types = **Medium**.
- **No-results** — a helpful "no results, try X", never a blank screen or bare "0 results" = **Medium**.

## 14. Feedback loops & AI interaction
- **AI disclosure** — AI-generated content is labelled; never presented as human = **High**.
- **Streaming** — long AI responses stream rather than a 10s spinner = **Medium**.
- **Feedback affordance** — AI output offers thumbs/regenerate, not read-only = **Low**.

## 15. Onboarding
- **User freedom** — tutorials are skippable with Skip/Back; no forced unskippable tour = **Medium**.

## 16. Data entry
- **Bulk actions** — repetitive edits allow multi-select + bulk, not one row at a time = **Low–Medium**.

## 17. Spatial UI (VisionOS / AR — only if relevant)
- **Gaze/hover response** — elements react to look before selection = **High** (on platform).
- **Depth layering** — real z-depth/glass separates UI from environment = **Medium**.

## 18. Sustainability
- **No autoplay video loops** — click-to-play or pause off-screen = **Medium**.
- **Asset weight** — heavy 3D/textures compressed and lazy-loaded = **Medium**.

---

## The two lenses that outrank the checklist

The checklist above catches craft defects. But two questions decide whether the
screen is *worth using at all*, and they outrank any single check:

1. **Frame-two ("what do I do here?")** — on landing cold, can the persona tell
   what this is and what to do within a few seconds? A screen that fails this is
   a **High** finding no matter how clean it scores on the checklist.
2. **Reason-to-visit** — does this give the user something they can't already get
   where they already go? "A prettier view of the same data" is the single most
   important finding a report can carry, because it predicts the feature gets
   demoed once and never reopened. This belongs in the report's Value Assessment,
   not the findings table.
