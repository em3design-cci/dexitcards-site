This document defines how DexIt communicates.

Tone and content should make the product feel:

approachable
clear
helpful
trustworthy

DexIt should feel like a smart, friendly guide — not a financial tool and not a hype-driven app.

## 1. Core Tone

DexIt speaks like a collector, not a corporation.

The tone is:

friendly, not formal
direct, not wordy
helpful, not pushy
confident, not arrogant

DexIt should always feel:

easy to understand and easy to trust

## 2. Voice

Calm. Confident. Grounded. Not optimized.

### Voice rules

- **Second person, not first.** Speak to the user ("Your collection") not from a system perspective ("We've found").
- **Short sentences. One idea per line.** Density is the enemy of clarity.
- **Active, concrete verbs.** "Dex this card" not "This card can be added."
- **No hedging.** State what is known directly, without qualifiers like "we think" or "approximately."
- **No hedging punctuation either.** (v1.3.) A tilde on a value — `~2012` — is "approximately" written as punctuation, and it is forbidden for the same reason the word is. Where a value can be changed, the affordance says so: an inline trigger's underline carries "this can be changed" as an action rather than as a hedge. See `design-principles.md` → Inline Triggers.
- **No exclamation points. Ever.** The product is grounded, not enthusiastic. Confidence comes from clarity, not punctuation.
- **Emoji used sparingly,** and only in auth or empty-state moments. The main app surface does not use emoji.

### Casing rules

- **ALL CAPS + letter-spacing** for section labels and category headers
- **ALL CAPS for Bebas button labels.** (v1.3 — corrected.) Bebas Neue Pro has lowercase glyphs, so a label passed as a literal string renders exactly as typed. Enforce it in the shared button style with `textTransform: 'uppercase'` rather than per call site, so casing cannot drift.
- **Title Case for screen titles.**
- **Sentence case** for body copy, descriptions, inline text, and placeholders

> **v1.3 correction.** Through v1.2 this section read *"Title Case for button labels and primary actions."*
> That was wrong, and it shipped a defect: a Title Case action rendered among all-caps siblings on the scan
> result screen, the only mixed-case action on the screen. `README.md` in `dexit-mobile` carried the same
> line — it was mirroring this document correctly, so both had to change. **This document is canonical for
> casing; the README is a mirror and must not diverge from it.**

### Placeholders

(v1.3, Build 19 Design handoff §6. The paragraph below is Design's, written for this document.)

> **Placeholders.** Sentence case. When a field benefits from an example, the placeholder is
> `Field name (e.g. value)` — one real example, lowercase `e.g.`, no trailing period, no dash and no colon.
> When it does not, the placeholder is the field name alone. Instructions and constraints are never
> placeholders; they go in helper text beneath the field, which is `textHintOnPaper` (#A0928F) while the
> placeholder itself is `textHint` (#B8AEAD) inside the white field.

**Every placeholder that needs an example uses one form:** `Field name (e.g. value)`

**Do:** `Parallel (e.g. Gold)` · `Set (e.g. Topps)` · `Grade (e.g. PSA 9)` · `Collection name (e.g. Vintage Baseball)`

**Don't:**

- `Parallel — e.g. Gold` — the dash does a label's job
- `Parallel: Gold` — reads like a filled value
- `Enter parallel` — instructions belong in helper text
- `e.g. Gold` — no field name

Details, so it stays one form: field name in sentence case; `e.g.` lowercase with both periods; exactly one
example, never a list of three; no trailing period; no colon and no dash; the example is a real value from
the catalog.

**Two exceptions:** a field inside a welded control where the name is the whole instruction and there is no
room, and a field where one example would imply a wrong format. Those use a helper line beneath instead.

#### Affixes are not placeholders

A permanent `#` or `/` sitting inside a field is an **affix**, not part of the placeholder and never part of
the value — a pasted `#360` strips to `360`. The affix is what says "card number" or "print run" without
spending a label on it. Where a field carries an affix, the placeholder is the affix plus the word that
names the box: `#Number`, `/Run`. That word is capitalised because it names the field, not because it opens
a sentence.

#### Two clarifications the handoff left implicit

(v1.3. Recorded here so they are not re-litigated from the general rule.)

- **`#NUMBER` in the value tile is deliberate, not a violation.** The welded display field inside the Dexit
  Value tile is Bebas, where all-caps is the casing rule; the edit sheet's card-number field is Inter and
  takes the sentence-case form `#Number`. Same field, two contexts, two correct answers. This is the first
  of the two exceptions above.
- **`Builds as you type.` keeps its period.** It is empty-state copy inside a preview card, not a field
  placeholder, so the no-trailing-period rule does not reach it.

### Collector language pairs

Always use collector-native language. Replace investor or generic-app language with collector terms:

| Instead of | Use |
|---|---|
| Add to wishlist | Chase this card |
| Your portfolio | Your collection |
| Market price | Your value |
| Holdings | What you've got |
| Asset | Card |
| Position | Card |

Note: the canonical engineering vocabulary may use finance-style terms (`portfolio`, `cost_basis`, `market_value`) inside code, but those terms must never reach user-facing strings.

## 3. The Personality

DexIt is:

the knowledgeable friend at a card show
the person who explains things simply
someone who helps you make better decisions

DexIt is NOT:

a finance app
a trading platform
a hype machine
overly technical
## 4. Language Principles
4.1 Keep It Simple

Avoid complex or financial-heavy language.

Instead of:

"Optimize your portfolio allocation"

Say:

"See what you have too much of"
4.2 Be Direct

Say things clearly in as few words as possible.

Instead of:

"You may want to consider adding this card"

Say:

"This could be a good fit for your collection"
4.3 Be Helpful, Not Salesy

Avoid urgency and pressure.

Instead of:

"Don't miss this opportunity!"

Say:

"This might be worth a look"
4.4 Use Familiar Collector Language

Lean into how collectors already speak:

pull
trade
slab
rookie
comp

This makes DexIt feel native to the hobby.

4.5 Introduce New Concepts Gently

The word "portfolio" may feel too formal.

Use softer language when needed:

"your collection" (default)
"your setup"
"your mix"
"what you've got"

Use "portfolio" when context matters, but don't force it.

## 5. The "Dex" Language System

DexIt introduces a new behavior.

This should feel natural and repeatable.

Examples:

"Dex your card"
"Did you Dex it?"
"Share your Dex"
"Check your Dex"

Rules:

keep it short
keep it casual
make it feel like something collectors would actually say
## 6. UX Writing Guidelines
Buttons
"Dex Card"
"Share Dex"
"Add Card"

Avoid:

"Submit"
"Continue" (unless necessary)
Empty States

Instead of:

"No data available"

Say:

"No cards yet. Dex your first one."
Feedback Messages

Instead of:

"Card successfully added"

Say:

"Card Dex'd"
Errors

Be calm and helpful.

Instead of:

"Error: Failed to process image"

Say:

"That didn't work. Try again or add it manually."

### Verdicts and evidence

(v1.3, Build 19 Design handoff §4.1. DEX-446.)

When the product cannot price a card because of what it found — rather than because it is still working —
it says so in **two sentences: a verdict naming what we found, and one line of evidence saying how we know.**

**The difference in certainty lives entirely in the evidence line.** No new badge state, no mark on the
number. The verdict shape and the controls are identical across states; only the evidence changes.

| State | Verdict | Evidence |
|---|---|---|
| Resolved, no comps | `No sales yet for #360` | unchanged from today |
| **Unresolved** — checklist complete, number not on it | `No card #999999 in this set` | `Not on the 2026 Bowman checklist.` |
| **Unknown** — no checklist for the set | `Can't confirm #999999` | `No checklist for 2026 Bowman yet.` |

Why each rule holds:

- **Never reuse "No sales yet" for a number that did not resolve.** It asserts the card exists — the one
  claim this screen cannot afford to get wrong, and the one the user acts on. A quiet market means wait;
  no such card means fix it. Those are opposite instructions.
- **"Not priced yet" is also wrong here.** It is a waiting state and implies time will fix it. This is a
  dead end until something changes, so the verdict names the finding instead.
- **Unresolved and unknown stay distinct.** Only 18 of 46 sets carry a complete checklist, so collapsing
  them would make the product routinely claim a certainty it does not have. The user's next action is the
  same either way, which is why only the evidence line differs.
- **Read from the back rather than typed:** same verdict, same layout. The evidence line says the number
  was read from the back, and the secondary action is **RETAKE** rather than SCAN THE BACK. A back scan is
  stronger evidence than typing, so the likelier fault is our catalog — **the screen must not imply a typo
  the user never made.**

> ⚠ **Drafted, not ruled by Design.** The handoff specifies the read-from-the-back behaviour in prose but
> gives no exact evidence string. Proposed, following the two-short-sentences voice rule:
> `Read from the back. Not on the 2026 Bowman checklist.` and
> `Read from the back. No checklist for 2026 Bowman yet.`
> The leading clause is what keeps the blame off the user. Replace if Design writes its own.

"Resolved", "unresolved" and "unknown" are defined in `confidence-architecture.md` §3.2 — they are the
product's three verdicts about whether a supplied value names a real card, not a new user-facing vocabulary.
Never render those words to the user.

### Copy fits by measurement

(v1.3.) Where copy sits in a row that also carries an action, the text column is what is left after the
action — not the row width. A line that has been cut to fit was cut for a reason; do not restore a longer
sentence later because it reads better in isolation.

When a sentence has to go, check what else is already carrying the meaning. An empty dashed thumbnail and a
scan control together say "the back is missing and you can fix it" without a sentence explaining it.

### Resolve collisions by anatomy, not by rewording

(v1.3, handoff §3.7.) When two labels collide on one control, the fix is usually to remove one of them
rather than to find shorter words for both. The confidence badge's edit segment carries **no text at all** —
its name lives in `accessibilityLabel` — so there is no surface on which a second label can collide with the
tier. Reach for structure before a thesaurus.

### Confidence Labels

When the system communicates confidence in a card identification, use plain-English tier labels. These are neutral descriptors, not warnings or disclaimers.

| Engine output | UI label |
|---|---|
| `'high'` | High Confidence |
| `'medium'` | Medium Confidence |
| `'low'` | Low Confidence |

The confidence badge is a **split capsule**: a label segment showing the confidence tier, a divider, and an edit segment containing a Material edit icon. The edit segment is always present and tappable; it opens the corrections flow. Do not render the badge as plain inline text.

**The label segment always reads the tier, and the edit segment carries no text.** (v1.3.) There is no state in which the label segment says something other than High / Medium / Low Confidence.

**"User Edited" is not a valid badge state.** When the user corrects a card, confidence improves — the badge reflects the updated confidence tier, not an editorial override label. (DEX-362)

Always state what is known. Avoid hedging language like "we think" or "approximately."

_Note: Earlier versions of this doc used "Strong signal / Limited data / Estimate only." Those labels are retired. The canonical labels are "High Confidence", "Medium Confidence", and "Low Confidence" — without a "Match" suffix — as of 2026-08-07 (DEX-373/374). DEX-302 introduced the High/Medium/Low system; this update removes the "Match" suffix and codifies the split-capsule badge anatomy._

### Currency formatting

**v1.4 — DEX-472, ruled by Eric 2026-08-19. Supersedes the rule below in full, including its own example
(`$4,889.50`), which the new ladder makes wrong** — `$4,889` is over the $10 threshold and must never carry
cents.

Display USD with a `$` prefix and comma thousands separators (e.g., `$4,889` not `$4889`) — unchanged.

**Never arbitrary cents, at any magnitude.** A displayed dollar value is never a number that merely happens
to have two decimal digits — it lands on exactly one of two precisions, by magnitude:

| Magnitude | Precision | Example |
|---|---|---|
| Under $10 | Quarter-dollar increments, rounded to the nearest quarter | `$2.50`, `$7.25` |
| $10 and over | Whole dollars, no decimals, comma thousands separators | `$10`, `$4,889` |

**Focused and unfocused states of any editable money field render at the same precision.** A value slider or
a typed value field must not show more or fewer decimal places while the user is actively editing it than it
shows at rest — a precision change on focus reads as the product silently rounding what the user typed,
which is not honest at either end of the interaction.

In code, use the `formatCurrency` utility — never format currency inline with template literals or one-off `toLocaleString` calls. This rule applies to every surface where money is shown to a user: scan results, collections, eBay listings, value sliders, success banners, push notifications, emails.

## 7. Content Strategy

DexIt content should do three things:

Teach the behavior ("Dex it")
Show value (insight, clarity)
Build trust
7.1 Content Themes
A. The Behavior
"Did you Dex it yet?"
"Dex your collection in seconds"
B. Insight
"You might have too many prospects"
"Here's what your collection looks like"
C. Real Moments
card shows
trades
pulls
shop visits

Content should reflect how collectors actually interact.

D. Light Education
what's a comp
how value works
how to think about your collection

Keep it simple and visual.

7.2 Avoid
overly financial language
hype or speculation
complicated explanations
long paragraphs
## 8. Trust Through Tone

Trust is built through:

clarity
transparency
consistency

Always:

explain where data comes from
avoid exaggeration
keep language grounded

DexIt should feel reliable, not flashy.

## 9. Visual + Tone Alignment

The product uses:

a vintage-modern aesthetic
clean layouts
minimal design

The tone should match:

simple
focused
grounded

Avoid loud or chaotic messaging.

## 10. Guiding Question

When writing anything, ask:

Does this sound like something a collector would actually say at a card show?

If not, simplify it.

## 11. The Goal

DexIt should feel:

easy the first time
useful the second time
essential over time

And eventually, collectors should naturally say:

"Just Dex it."

---

## Changelog

| Version | Date | Change |
|---|---|---|
| v1.4 | 2026-08-19 | **Currency formatting replaced with the magnitude ladder.** (DEX-472, ruled by Eric.) The prior rule — "show cents only when meaningful" — was undefined and its own example (`$4,889.50`) contradicts the new rule outright. Merged from scratch: this specific ladder had never shipped to this repo's copy (the v1.3 draft lived only in the Claude project). **Never arbitrary cents, at any magnitude**: under $10, quarter-dollar increments rounded to the nearest quarter (`$2.50`, `$7.25`); $10 and over, whole dollars, no decimals, comma thousands separators held (`$4,889`). New rule: **focused and unfocused states of any editable money field render at the same precision** — a value must not gain or lose decimal places on focus. |
| v1.3 | 2026-08-15 | **Build 19 Design handoff, content rules.** **Casing corrected** — through v1.2 this document said "Title Case for button labels and primary actions", which is what shipped a Title Case action among all-caps siblings on the scan result screen. It now reads ALL CAPS for Bebas button labels and Title Case for screen titles, enforced with `textTransform: 'uppercase'` on the shared style rather than per call site. The handoff attributed the bad guideline to `dexit-mobile`'s README; the README was mirroring **this** document, so the canonical line was the source. This document is canonical for casing and the README is a non-diverging mirror. New **Placeholders** section carrying Design's verbatim paragraph plus the full form (`Field name (e.g. value)`), the do/don't list, the two exceptions, and an **Affixes are not placeholders** rule. Two clarifications the handoff left implicit are recorded so they are not re-litigated: `#NUMBER` in the Bebas value tile versus `#Number` in the Inter edit sheet is the welded-control exception, not a violation; and `Builds as you type.` keeps its period because it is empty-state copy, not a placeholder. New **Verdicts and evidence** section (DEX-446): two sentences — a verdict naming what we found and one line of evidence saying how we know — with the exact strings for the resolved, unresolved and unknown states, and the reasoning for why "No sales yet" must never be reused for a number that did not resolve, why "Not priced yet" is also wrong, and why unresolved and unknown stay distinct. The read-from-the-back evidence line is **drafted rather than ruled** — the handoff specifies the behaviour but no string, and the draft is flagged in place. New **Copy fits by measurement** and **Resolve collisions by anatomy** rules. Voice rules gain **no hedging punctuation** — a tilde is "approximately" as punctuation, and where a value can be changed the inline trigger's underline carries that as an action instead. Confidence Labels records that the label segment always reads the tier and the edit segment carries no text. |
| v1.2 | 2026-08-07 | Removed "Match" suffix from confidence labels (High/Medium/Low Confidence are canonical, not "High/Medium/Low Confidence Match"). Replaced inline-text badge description with split-capsule anatomy rule. Added "User Edited is not a valid badge state" rule (DEX-362). DEX-373/374. |
| v1.1 | 2026-08-04 | Introduced High/Medium/Low Confidence Match labels (DEX-302). Retired "Strong signal / Limited data / Estimate only." |
| v1.0 | Prior | Initial release. |
