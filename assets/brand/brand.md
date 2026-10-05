# Replay: Brand & Product Design Operating Document

**Version 1.1 · 1 October 2026 · Prepared by PIXELUP for Replay (Sunset HQ Corp.)**

**Companion files (this kit).** `DESIGN.md` is the short, machine-readable contract that coding and design agents load: tokens in YAML front matter plus rules, in the open DESIGN.md format from Google Labs, and it lints clean with `npx @google/design.md lint`. This document is the long form: the evidence, the reasoning, the debt and the roadmap. When the two disagree, fix DESIGN.md first and this document second. Logo masters, textures and patterns ship alongside in `logo/`, `textures/` and `patterns/`; exported tokens in `tokens/`.

**What changed in 1.1.** Audited the review file (`UstspKowhUbYUC0zzT5DRc`: Final Pages and Brand Guidelines WIP) and the repo's assets. New findings: four text colours fail WCAG AA as shipped; the STK Bureau files are trial cuts; the final footer IA in Figma differs from the code; the WIP guideline names a different serif accent from the one the site loads; 14 texture files are 6 textures; two logo files in the repo are dead and one of them is not the Replay mark. Corrections to 1.0: the footer does not use a standalone mark; eyebrows are Geist Mono 400, not 500; Blue Bright is not usable as text.

This is the source of truth for how Replay looks, feels, behaves, moves and speaks. It is written for four readers at once: the client making brand calls, designers adding screens, engineers implementing them, and AI agents asked to do any of the above without a human in the loop.

It is an audit first and a rulebook second. Every important rule is traced to evidence in the Figma file (`AYzBKhVneW9mct6tUchEo7`) or the repository (`PIXELUPLABS/sunsethq`, commit `b89c394`, 1 Oct 2026). Where the evidence is thin or contradictory, the document says so instead of inventing a rule.

---

## 0. How to read this document

Every substantive claim carries one of four tags.

| Tag | Meaning |
|---|---|
| **[O] Observed** | Found directly in Figma or code. A fact, with a location. |
| **[P] Pattern** | Repeated enough across pages or files to count as an existing system, even if nobody wrote it down. |
| **[I] Inferred** | A likely design intention reconstructed from several examples. Treat as the current best reading, not law. |
| **[R] Recommendation** | Something that should be introduced or changed. Not yet true of the product. |

Three conventions follow from this. An **[O]** or **[P]** rule can be enforced in review today. An **[I]** rule should be confirmed with the design lead before it is encoded in tooling. An **[R]** is a decision still to be made, listed in the action plan (§23) with a priority.

Nothing in this document turns an accident into a rule. Where the code does something once, in one module, it is reported as a one-off. Where a value appears 70 times across every module, it is reported as the system.

**Contents.** 0 How to read · 1 What makes Replay feel like Replay · 2 Design principles · 3 Personality → behaviour · 4 Logo · 5 Colour · 6 Typography · 7 Layout and spacing · 8 Shape · 9 Iconography · 10 Imagery · 11 Product design language · 12 Motion · 13 Invisible details · 14 Brand ↔ product bridge · 15 Marketing vs product · 16 Content and voice · 17 Responsive · 18 Tokens · 19 Decision framework · 20 Established / emerging / missing · 21 Inconsistencies · 22 Evolution · 23 Action plan · 24 Source map

---

## 1. What makes Replay feel like Replay

Replay licenses operating data from companies that are still operating. The brand problem it was built to solve is a misread: the parent company, Sunset, winds companies down, and leads who saw the Sunset site assumed Replay was there to shut them down too. **[O]** Brief, Part 1.

So the identity is defined as much by what it refuses as by what it uses. Sunset is warm tan paper, rounded cards, a horse, ukiyo-e landscapes and the language of closure. **[O]** `currentsite.png`. Replay is cool paper, hard corners, cobalt, engraved serif, dashed registration lines and the language of yield. The two share a legal footer line and nothing else. **[O]** `footer.tsx`: "© 2026 Replay. All rights reserved · Sunset HQ Corp."

Looked at as a whole, the Replay system has a small number of recurring characteristics. **[P]**

- **The page is a sheet of paper.** Near-white ground (`#fcfcfc`) with a grain texture multiplied over it, on every page, in the nav, in cards. Not a screen, a document.
- **Everything on it is printed, stamped or issued.** Serif display type at tight tracking; mono eyebrows set inside hairline boxes; record-style metadata (`RL-2026-001 // Version 1.0`, `CLASSIFICATION PROPRIETARY DATA / LICENSING`); dashed guide lines where a ledger would have rules.
- **Zero radius.** Across ~250 component files, `rounded-*` appears seven times: on 5 px status dots, on the decorative holes of the form rail, and on one 1.5 px illustration edge. Corners are square. Where a corner needs emphasis it gets a fold (a clipped black triangle) or a registration tick, never a radius.
- **One blue, used as a reveal.** The cobalt gradient (Deep `#133264` → Bright `#147dba`) is scarce. It appears on the primary button's *hover* state, on the growth card's *hover* state, and on the panels where the worth of the data is shown. Paper and Ink carry the page; blue marks the moment.
- **A colour bar.** A horizontal strip of Sky, Olive, Bar gray and Sun segments, with noise multiplied over it, runs under the nav, under heroes, inside the button hover and on the brand-guideline cards. It is the one piece of chromatic noise the brand allows, and it is always a thin horizontal band.
- **Texture does the work shadows would do.** Grain, guilloché weave, hatch, canvas. The whole codebase contains one `shadow-xl`. Depth comes from surface changes (Paper → White → Mist → Night) and lines, not from elevation.
- **Illustrations show the mechanism.** Real operating material (Slack threads, emails, tickets, commits) going through a visible process (a scan line, redaction bars, stacked isometric slabs with pinned callouts). The brief's own words: "Show it works", not "Just works".
- **Two tempos of motion.** Interface feedback is fast ease-out (150 to 200 ms). Ceremonial moments (the worth reveal, the de-identification pass, the footer wordmark sweep, the counting stats) are slow, play once on scroll, and are tied to the content they explain.

The brief asked for a brand that reads as "Amex, not Spirit": established, trustworthy, the most prestigious bank for a new asset class. **[O]** Workshop 4.1. The system above is how that ambition is executed: restraint in colour, craft in texture and type, and process shown rather than claimed.

---

## 2. Design principles

Six principles. Each is specific enough to judge a new feature against. They are ordered by how often they will be the deciding factor.

### 2.1 Paper first, ink second

**Meaning.** The surface is a document, not a screen. Everything placed on it should feel printed onto it rather than floating above it.

**Visual expression.** Paper ground `#fcfcfc` with grain multiplied at low opacity **[O]** `navbar.tsx`, `grain-card.tsx`, Figma annotation "Base texture Blend Mode: Multiply, Brightness 125%, Contrast 200%, Saturation 0%". Ink `#141518` for type and buttons. Dashed hairlines as rules. **[P]** 186 `border-dashed` declarations vs 1 explicit `border-solid`.

**Product expression.** Surfaces step, they do not lift: Paper for the page, White for cards that must read as sheets, Mist `#eaebf1` for feature bands, Night `#080808` for dark sections. **[O]** Figma 3.2 Neutrals & Surfaces. A card is a region of the page with a line around it, not an object casting a shadow. The whole site uses one drop shadow in UI (the Value-my-data form card, `0 8px 28px -10px rgba(20,21,24,.10)`) and one on the cookie banner. **[O]**

**Interaction expression.** State changes are changes of ink: a border darkens (`#d4d4d4` → black on input focus **[O]** `value-my-data-form.tsx`), text darkens (`#777` → `#141518` on nav hover **[O]**), a surface floods with cobalt (primary button hover **[O]**). Nothing lifts, glows or bounces.

**Avoid.** Drop shadows as a default elevation model. Glassmorphism. Glow effects on UI. Gradient text. Anything that reads as a floating card on a dashboard.

### 2.2 Square, registered, hairline

**Meaning.** The geometry is that of ledgers, certificates and assay documents: right angles, 1 px lines, corner marks, dash patterns. The shape language signals that things here are measured and recorded.

**Visual expression.** Zero border radius everywhere. **[P]** Hairline borders at 1 px (Tailwind `border`), dashed in `#d4d4d4` ("Line", Figma) for guides and dividers, solid in `#a8a8a8` ("Strong line") for frames and field borders. **[O]** Figma 3.2; code counts 64 dashed vs 4 solid uses of `#d4d4d4`, 26 vs 4 for `#a8a8a8`. Corner fold: a 16 px black triangle clipped into the top-right of grain cards. **[O]** `grain-card.tsx`. Registration ticks at frame corners. **[O]** Data & Trust illustrations, stored memory.

**Product expression.** Inputs are 48 px tall rectangles with a 1 px `#d4d4d4` border and no radius. **[O]** Buttons are rectangles. Tags are mono text inside a bordered box with the icon in an adjacent, border-sharing box (`-mr-px` to collapse the double line). **[O]** `section-tag.tsx`. Tabs are bordered cells in a row. Progress is a thin filled bar.

**Interaction expression.** Hover and focus are expressed by the line, not the shape: border colour, underline width (footer links grow a 1 px underline from 0 to 100 % **[O]** `footer.tsx`), or a filled cell. Shapes never morph their corners.

**Avoid.** Any `rounded-*` on containers, buttons, inputs or badges. Pills. Soft blobs. Strokes above 1.5 px in UI. Two-tone outlines.

### 2.3 One blue, and it is the reveal

**Meaning.** Replay Blue exists to mark the moment of value. It is the colour of the answer, not the colour of the page.

**Visual expression.** A single vertical gradient, Deep `#133264` at ~27 % to Bright `#147dba` at ~144 %, under a soft-light guilloché weave. **[O]** `.bg-brand-gradient` in `globals.css`, `primary-button-hover.tsx`, Figma hover variant. The gradient always runs top to bottom (deep on top). Never a flat blue fill on a large surface; always the gradient plus weave.

**Product expression.** Blue appears on: the primary button's hover state; the hoverable growth card; the "What companies your size get paid" panel; the de-identification panel on Data & Trust; the About page's purpose diagram. **[O]** That is a short list, and it should stay short. Blue is never used for body text, links, icons at rest, or secondary buttons. **[I]** No instance found in code of blue text on paper.

**Interaction expression.** Blue arrives on interaction (hover, scroll-into-view) and is the strongest state in the system. Where blue appears, nothing else on the surface competes: text goes white, textures go soft-light, the colour strips slide in. **[O]** `primary-button-hover.tsx`.

**Avoid.** A second blue. Blue as a link colour. Blue buttons at rest. Blue on more than one surface per viewport. Purple or violet anywhere in UI (the brief: "Hate purple").

### 2.4 Show the working

**Meaning.** Replay's product is a process (identified → structured → verified → licensed) applied to real material. The imagery should always show real operating records and the mechanism acting on them.

**Visual expression.** Three families. (1) Specimens: cut-outs of emails, Slack threads, Jira tickets, commits, dashboards, with torn edges and no box shadow. **[O]** `deid-pass.css`: "the records are cut from real exports with torn edges, so no box shadow". (2) The mechanism: a scan line, guilloché redaction bars, a de-identification sheet, placeholder tokens like `[user_01]`, `[id_256]`. **[O]** AI Buyers "De-identified, without losing the signal". (3) Structure: isometric slabs with extruded sides, hatch fills and pinned callouts with leader dots. **[O]** "How it works", Data & Trust, memory notes on the Griffin reference.

**Product expression.** Every explanatory section pairs copy with a working diagram, not a hero image. Data categories are shown as an index of named record types, not icons on a grid. Stats count up from zero when they enter view. **[O]** `use-digit-count-up.ts`.

**Interaction expression.** Explanatory motion is allowed to be long and literal because it is doing a teaching job: the de-identification pass runs ~5 s per step; the "How it works" accordion auto-advances. **[O]** But it plays only when ≥ 30 % visible, pauses when fully out of view, and restarts on re-entry. **[O]** `SCROLL_PLAY_THRESHOLD = 0.3`.

**Avoid.** Abstract gradient blobs. Generic "AI" orbs or neural networks. Stock photography of offices. Personal or sensitive records as specimens (payroll stubs, medical bills; rejected by the client as "super scary"). Illustrations whose labels do not match what the block actually depicts.

### 2.5 Engraved, not campaigned

**Meaning.** The brand sounds like something issued by an institution: plain, declarative, specific. It does not sell; it states.

**Visual expression.** STK Bureau Serif at tight negative tracking for everything that is said; Geist for everything that is explained; Geist Mono, uppercase, wide-tracked, for everything that is filed. **[P]** 83 `font-serif`, 76 `font-mono`. Headlines are sentence case with a full stop. **[P]** "Fund growth by licensing the data you already have." "Your data stays yours." "Every note, on the record."

**Product expression.** Section eyebrows are mono labels in bordered boxes ("WHO BUYS IT", "THE PROCESS"). Footer columns are numbered `01 Product … 04 Legal`. Lists are indexed `[001]`, `[002]`. Metadata is formatted like file headers. Numbers are big serif (`$100K+`, `26 days`), labels beneath them small and grey.

**Interaction expression.** Microcopy stays in the same register during interaction: "Sending…", "Send for review", "Value my data". **[O]** `value-my-data-form.tsx`. No exclamation marks, no "Awesome!", no emoji, no toasts that cheer.

**Avoid.** Uppercase headlines. Jargon ("leverage", "unlock", "seamless", "cutting-edge"). Em dashes (house rule). Exclamation marks. Campaign taglines. Any copy that could be pasted onto a competitor's site unchanged.

### 2.6 Fast ink, slow ceremony

**Meaning.** There are exactly two tempos. Feedback to the user is immediate. Explanation to the user is deliberate. Nothing lives in between.

**Visual expression.** Fast: a border or colour change, a 2 % press scale, an opacity swap. Slow: a stat counting up, a sheet scanning a record, light sweeping across the wordmark, stripes stepping in with scroll.

**Product expression.** Press: `scale(0.98)`, 150 ms, `--ease-snap`. **[O]** Form submit, cookie buttons, role rows. Hover colour: `transition-colors`, 150 to 200 ms. **[P]** Disclosure: `grid-template-rows 0fr → 1fr`, 200 ms, ease-out. **[O]** `faq-item.tsx`. Reveal on scroll: fade (with optional 8 to 12 px slide or 10 px blur), 300 to 500 ms, once. **[O]** `reveal-fade*` keyframes. Ceremony: 500 to 900 ms, custom curve, one-shot. **[O]** wordmark shimmer 900 ms, count-up 500 ms + 120 ms per digit.

**Interaction expression.** Fast interactions use CSS transitions so they can be interrupted and reversed. Ceremonies use `requestAnimationFrame` or keyframes and are designed to be seen once; they rewind when the element leaves the viewport so a second viewing starts clean. **[O]** `use-digit-count-up.ts` rewinds on exit.

**Avoid.** Hover transitions over 200 ms. Springs or overshoot anywhere in UI. Animating `height`, `width`, `padding` for interactive elements. Scroll-hijacking (the brief names it). Any animation that plays on a keyboard-initiated action.

---

## 3. Brand personality → design behaviour

Five attributes, each supported by the brief, the workshop and the shipped work. The workshop pinned the brand as Serious + Safe, strongly Timeless, Muted, Authoritative and Light-first; the primary adjectives were Premium, Precise, Trustworthy, Editorial, Confident. **[O]** Workshop 5.2 to 5.4, stored project memory.

| Brand quality | Visual expression | UI expression | Interaction expression |
|---|---|---|---|
| **Precise** | Hairline rules, tight serif tracking (−4 %), mono metadata, dashed registration | 1 px borders, 48 px fields, numeric indexes on lists, right-aligned metadata, consistent 24 px gaps | Press feedback ≤ 150 ms, disclosures ≤ 200 ms, nothing overshoots; transitions name their properties |
| **Trustworthy (institutional)** | Paper and ink dominate; blue scarce; textures from banknotes and certificates (guilloché, grain, hatch) | Named buyers, named steps, numbered footers; legal line always present; no dark patterns in consent UI (Reject and Accept styled identically **[O]**) | Nothing surprises: hover reveals, never hides; auto-cycles pause when off-screen; forms keep answers on failure ("Your answers are saved in this tab") |
| **Premium, by restraint** | One typeface for voice, one for explanation, one for filing; one blue; one colour bar; square geometry | Generous section rhythm (72 px side padding, 64 to 176 px vertical gaps); small type is small (10 px eyebrows); no decoration without a job | Hover states are rich but rare (cobalt flood, weave, strips); everything else is quiet. Motion is deliberately slow only where it explains |
| **Technical, but human** | Code fragments and record headers as texture; real Slack and email specimens; isometric machinery | Plain-language labels next to technical ones ("De-identify your data", "Get paid"); eyebrows in mono, headings in serif | Explanatory animations show cause and effect (record enters, scan passes, placeholders appear); stats count rather than appear |
| **Confident, calm** | Large serif statements with full stops; big numbers; wide whitespace; no hero carousel | One primary action per page ("Value my data") in Ink, everywhere else is a link | No urgency devices. Enter is longer than exit. Nothing pulses, blinks or badges |

What the evidence does **not** support: Playful, Energetic, Experimental, Rebellious. The brief lists them as options; the work never chose them. Do not add them.

---

## 4. Logo

The signature is a square mark plus a serif wordmark. **[O]** Figma 2.0 to 2.6; `public/images/sunset-logo.svg` (111 × 36, the legacy filename is still in use), `footer-logo.svg` (43 × 43 mark), `favicon-light.svg` / `favicon-dark.svg` (32 × 32).

**Primary mark.** A square frame through which a series of parallel forms pass, with a solid wedge between them. The WIP guideline gives the intended reading: information moving from what already exists into something structured, usable and valuable; repetition suggesting continuity and return; the frame giving it the permanence of an institutional seal. **[O]** Figma review file, 2.2 (`7547:3985`). It is also explicit that the meaning should stay one level abstract and not be explained as "data becoming money". **[O]** That instruction is currently written *inside* the 2.2 body copy as a reviewer's note ("This is important: I would avoid over-explaining it…"). **[R]** Move it to a Figma comment before the guideline is shared.

**Wordmark.** "Replay" in a classical serif drawn to sit with the mark; the WIP copy describes it as "intentionally restrained, drawing on the visual language of established financial and information institutions". **[O]** 2.1. The signature (mark + wordmark) is the primary form and should be used together wherever space allows; the mark alone is for constrained spaces or where Replay is already established. **[O]** 2.1, 2.2.

**Measured construction.** From the shipped master (`sunset-logo.svg`, 111 × 36 units), with X = the mark's side (20.46 units): **[O]**
- The mark is a true square, X × X.
- The wordmark's cap height equals X; the cap R and the mark share top and baseline.
- The gap between mark and wordmark is 0.26X, which is the X/4 clear-space rule; the clear space and the internal gap are the same unit.
- Ascender (l) rises 0.10X above the mark; descenders (p, y) drop 0.27X below the baseline.
- The full signature is 5.41X wide.

**Construction and clear space.** Minimum exclusion zone X/4 on all sides, where X is the width of the mark. Applies when the mark is used alone. **[O]** Figma 2.4.

**Scalability.** Documented sizes 104, 88, 72, 56, 40 px; minimum 24 px. **[O]** Figma 2.5. The nav renders the signature at 36 px high. **[O]** `navbar.tsx`.

**Colour.** Ink on Paper is primary. Reversed (white) on Night is the dark version. **[O]** Favicon ships light and dark variants keyed to `prefers-color-scheme`. **[O]** `layout.tsx`. Blue wordmark, blue mark on black wordmark, and gradient-filled wordmark are all shown as incorrect. **[O]** Figma 2.6.

**Incorrect usage (from the file).** Do not recolour individual elements; do not change the mark/wordmark relationship; do not add text to the signature ("We are Replay" is shown crossed out); do not reposition or reorder; do not distort; do not apply effects; do not reset in another typeface or weight. **[O]** Figma 2.6.

**Product usage.** Nav: full signature, left, 36 px. Footer: a large grain-filled wordmark lockup with a pointer-following shimmer and a dashed white stroke, drawn from `lib/replay-wordmark-paths.ts`. **[O]** `replay-wordmark.tsx`. The footer does **not** use a standalone mark. Two logo-looking files in `public/` are unreferenced: `images/footer-logo.svg` (a white knot shape that is not the Replay mark at all) and `public/Vector.svg` (an earlier white export of the footer lockup). **[O]** grep across `modules/`, `components/`, `app/`. **[R]** Delete both so nobody picks them up as masters.

**Masters.** Use only the files in `logo/` in this kit: signature, mark and wordmark in black and white, each with an X/4 clear-space variant, plus square avatars on Paper and Night and the two favicons. They were cut from the shipped signature by geometry, so they match production exactly. The masters are pure black (`#000`) as in Figma; on Paper the difference from Ink is invisible, and the guideline forbids recolouring individual elements.

**Favicon and avatar.** 32 px simplified mark, light and dark. **[O]** OG image and X/Twitter header exist in Figma (`OG-1`, `OG Banner`, `Twitter header - 3`) using the hero headline on paper with the colour bar. **[O]** Figma Brand Guideline page.

**[R]** Rename `sunset-logo.svg` to `replay-signature.svg`. The filename is the last place the old brand survives in the product, and it will confuse the next engineer.

**[R]** ~~Add the mark alone as a documented asset.~~ Done in this kit (`logo/svg/replay-mark-*.svg`, PNG at 64 to 1024 px). Ship the same files into `public/` and the Figma library so the three stay identical.

---

## 5. Colour system

The Figma Brand Guidelines (3.1 to 3.4) name a complete palette. **[O]** The code exposes only three of those colours as tokens and hard-codes the rest in ~60 distinct hex values. **[O]** `globals.css` defines `--color-ink`, `--color-blue-deep`, `--color-blue-bright`; a grep of `modules/` returns `#d4d4d4` 74 times, `#727272` 52, `#a8a8a8` 47, `#898989` 37, `#fcfcfc` 33, `#141518` 28. The system exists; it has not been tokenised.

The usage principles from the file, verbatim in spirit: **accents stay small; keep text readable; one blue; pastels live in artwork.** **[O]** Figma 3.4.

### 5.1 Brand

| Token | Value | Purpose | Usage | Source | Status |
|---|---|---|---|---|---|
| `color/brand/blue-deep` | `#133264` | Replay Blue, deep end | Top of the brand gradient; never flat on large areas | Figma 3.1; `globals.css` | [O] |
| `color/brand/blue-bright` | `#147dba` | Replay Blue, bright end | Bottom of the brand gradient | Figma 3.1; `globals.css` | [O] |
| `gradient/brand` | `linear-gradient(180deg, #133264 27%, #147dba 144%)` | The one blue surface | Primary button hover, growth card hover, value panels | `.bg-brand-gradient`, `primary-button-hover.tsx` | [O] |

The gradient is always paired with a soft-light weave texture at 185 px or 296 px tile. **[O]** Figma specifies the weave; code applies `button-hover-weave.webp` and `texture-soft-light.webp`.

### 5.2 Surface

| Token | Value | Purpose | Usage | Source | Status |
|---|---|---|---|---|---|
| `color/surface/paper` | `#fcfcfc` | The page | Body ground on every page; nav backdrop at 97 % | Figma "Paper"; 33 uses | [O] |
| `color/surface/white` | `#ffffff` | Cards that must read as sheets | Form card, shelf tiles | Figma "White · Cards" | [O] |
| `color/surface/mist` | `#eaebf1` | Feature bands | Grey panels, hover ground under cobalt, catalog tiles | Figma "Mist"; 23 uses | [O] |
| `color/surface/night` | `#080808` | Dark sections | Footer, pricing panel | Figma "Night"; footer | [O] |
| `color/surface/ink` | `#141518` | Ink as a surface | Primary button, mobile CTA, bottom stripes (should be) | Figma "Ink"; 11 `bg-` uses | [O] |
| `color/surface/overlay` | `#fcfcfc @ 0.97` + 16 px blur | Nav backdrop | Fixed header only | `navbar.tsx` | [O] |

**[R]** `--background` in `globals.css` is `#ffffff` and `--foreground` is `#171717`; both are Next.js boilerplate and neither matches the system (`#fcfcfc` / `#141518`). Set them to Paper and Ink. Today every page overrides them, which is why nobody noticed.

### 5.3 Content

| Token | Value | Purpose | Usage | Source | Status |
|---|---|---|---|---|---|
| `color/content/primary` | `#141518` | Headings, button labels | Serif display, Ink UI | Figma "Ink · Type and buttons" | [O] |
| `color/content/body` | `#727272` | Body copy on Paper and White **only** | Hero sublines, descriptions | Figma "Body gray"; 52 uses | [O] 4.69:1 on Paper; **fails on Mist (4.04:1)** |
| `color/content/reading` | `#565656` | Long copy; text on Mist | Legal pages, cookie copy, long paragraphs | Figma "Reading gray"; 12 uses | [O] |
| `color/content/label` | `#898989` | Small labels **on Night** | Mono captions, role-row meta, chevrons | Figma "Label gray"; 37 uses | [O] **3.41:1 on Paper, fails AA**; 5.73:1 on Night |
| `color/content/inverse` | `#ffffff` | Text on Ink, Night, Blue | Button labels, dark sections | Everywhere dark | [O] |
| `color/content/inverse-muted` | `#ffffff @ 0.6` (≈ `#9c9c9c` on Night) | Secondary text on dark | Footer links at rest | `footer.tsx` | [O] |

**Contrast, measured.** **[O]** Every text grey checked against every surface (WCAG 2.1, 4.5:1 for body text):

| Text | Paper | White | Mist | Night | Blue Deep |
|---|---|---|---|---|---|
| Ink `#141518` | 17.80 | 18.26 | 15.35 | — | — |
| Body `#727272` | **4.69** | 4.81 | *4.04* | *4.16* | — |
| Reading `#565656` | 7.15 | 7.34 | **6.17** | — | — |
| Label `#898989` | *3.41* | *3.50* | *2.94* | **5.73** | — |
| Nav as shipped `#777` | *4.36* | *4.48* | — | — | — |
| Eyebrow as shipped `#7b7b7b` | *4.13* | *4.23* | *3.56* | 4.73 | — |
| Tag on blue `#a9b8c8` | — | — | — | 9.90 | **6.22** |
| Blue Bright `#147dba` | *4.38* | *4.49* | — | — | — |
| Error `#bf000f` | 6.35 | 6.52 | 5.48 | — | — |

Italic values fail. The Figma rule "Reading gray for text on Mist" is therefore not a preference but the only passing option, and Label gray belongs on Night. Google's DESIGN.md linter reproduces the nav, eyebrow, Mist and Label failures automatically when the as-shipped values are encoded (see `tokens/lint-report.json` and §23).

### 5.4 Border

| Token | Value | Purpose | Usage | Source | Status |
|---|---|---|---|---|---|
| `color/border/line` | `#d4d4d4` | Dashed guides, dividers, rules | Section dividers, FAQ rules, grid lines | Figma "Line · Dashed lines"; 74 uses | [O] |
| `color/border/strong` | `#a8a8a8` | Frames, field borders, tag boxes | Nav side frames, input rest, tethers | Figma "Strong line · Frames, field borders"; 47 uses | [O] |
| `color/border/focus` | `#141518` (Ink) | Focused field | Input `focus:border-black` | `value-my-data-form.tsx` | [O] |
| `color/border/inverse` | `#ffffff @ 0.16` | Dashed rules on Night | Footer | `footer.tsx` | [O] |

Dash pattern in Figma is 4 on / 4 off at 1 px. **[O]** Figma annotation in `deid-pass-engine.js`: "the site's dashed stroke - #D4D4D4, weight 1, dash 4, gap 4". CSS `border-dashed` is browser-defined and does not reproduce 4/4 exactly. **[O]** This is an accepted approximation for UI; illustrations that need the exact pattern draw it in SVG.

### 5.5 Semantic

| Token | Value | Purpose | Source | Status |
|---|---|---|---|---|
| `color/semantic/error` | `#bf000f` | Errors only | Figma 3.1 "Error red · Errors only" | [O] in Figma |
| `color/semantic/error` (as shipped) | Tailwind `text-red-700` (`#b91c1c`) | Form error message | `value-my-data-form.tsx` | [O] mismatch |
| `color/semantic/success` | — | Not defined | — | Missing |
| `color/semantic/warning` | — | Not defined | — | Missing |
| `color/semantic/info` | — | Not defined | — | Missing; if needed, Blue Deep `#133264` (Blue Bright fails as text) |

**[R]** Ship `#bf000f` as the error token and remove the Tailwind default. Define success as Olive `#54702f` (already a brand accent, already reads as "done" on the process bar) and info as Blue Bright `#147dba` at small sizes only. Do not add a warning yellow; Sun `#eae058` fails contrast on Paper and the brand does not warn, it states.

### 5.6 Accents (the colour bar and charts)

| Token | Value | Name | Purpose | Source | Status |
|---|---|---|---|---|---|
| `color/accent/sky` | `#499df8` | Sky | Colour bar; corner fold on hover; chart bars | Figma 3.1; `PROCESS_BAR_COLORS` | [O] |
| `color/accent/olive` | `#54702f` | Olive | Colour bar; chart bars | Figma 3.1; 17 uses | [O] |
| `color/accent/sun` | `#eae058` | Sun | Colour bar only (4 to 6 % of its width) | Figma 3.1; 6 uses | [O] |
| `color/accent/bar-gray` | `#7e7e7e` | Bar gray | Colour bar only | Figma 3.1; 13 uses | [O] |
| `color/accent/teal` | `#0e9692` | Teal | Chart bars (pricing tiers "cyan" tone) | Figma 3.1; `PRICING_TIERS` | [O] |
| `color/accent/slate` | `#3a5979` | Slate | Chart bars, artwork | Figma 3.1 | [O] |

The colour bar's segment order and proportions are a fixed asset: Sky 27 %, Olive 21 %, Bar gray 30 %, Sun 4 %, Sky 6 %, Olive 23 %, with hero noise multiplied over it at soft-light. **[O]** `process-bar.tsx`. The nav strip uses the same six colours in a different, pixel-fixed rhythm at 8 px high. **[O]** `nav-color-strip.tsx`. **[I]** The colour bar is read as a spectrum of record classes passing through the pipeline. It runs 8 to 9 px under the nav and up to 20 px under the home hero's pipeline line (`hero-footer-bar.tsx`). It is never a background, never a chart, never taller than that. Note the six widths in `process-bar.tsx` sum to 111 %; flex-shrink rescales them, so rendered proportions are about 24 / 19 / 27 / 4 / 5 / 21 %. **[O]** **[R]** Normalise the numbers so the code says what the screen shows. `patterns/colour-bar.svg` in this kit is already normalised.

### 5.7 Artwork

Butter `#f0edd1`, Sage `#b7d3c1`, Lavender `#c1b4d8`, Cream `#fbf1d0`. **[O]** Figma 3.1 "Artwork colours". These are for the torn-paper specimen collage behind the closing CTA and for illustration fills only. They never touch UI.

**[R]** Lavender sits uncomfortably against the brief's "Hate purple". It appears in Figma but not in shipped code. Either drop it from the palette or keep it strictly under 10 % of any illustration and never on its own.

### 5.8 Interactive states

| State | Treatment | Source | Status |
|---|---|---|---|
| Default | Ink surface, white label (primary); Ink text, no surface (link) | `hero-cta-button.tsx`, `nav-links.tsx` | [O] |
| Hover (primary) | Cobalt gradient + weave fade in 300 ms; colour strips slide in from both edges 300 ms | `primary-button-hover.tsx` | [O] |
| Hover (link) | `#777` → `#141518`, 150 ms colours | `nav-links.tsx` | [O] |
| Hover (row) | `bg-black/[0.03]`, 200 ms, gated to hover-capable devices | `role-row.tsx` | [O] |
| Active / press | `scale(0.98)`, 150 ms, `--ease-snap` | 5 sites; absent on hero and nav CTA | [P] partial |
| Selected (tab) | Sliding Ink fill with white text (landing); text-colour change (Data & Trust) | `deidentification-tabs.tsx`, `standard-tab-button.tsx` | [O] |
| Focus | `focus-visible:outline-2 outline-offset-2/4` (browser default colour) | Legal, cookie only | [O] partial |
| Disabled | `opacity-60`, `cursor-wait` while submitting | `value-my-data-form.tsx` | [O] |

### 5.9 Colours to consolidate

The following hex values appear in code and are visually equivalent to a named token. **[O]** They should be replaced, not added to.

| Found in code | Count | Replace with |
|---|---|---|
| `#0c0c0b`, `#010101`, `#090909`, `#181a1b`, `#171717`, `#1c1c1c` | 16 | Ink `#141518` or Night `#080808` by context |
| `#777`, `#7b7b7b`, `#8a8a8a`, `#8d8d8d`, `#919191`, `#858585`, `#a2a2a2`, `#a6a6a6` | ~20 | Body `#727272` or Label `#898989` |
| `#d9d9d9`, `#ddd`, `#dedede`, `#e0e0e0`, `#cecece`, `#c2c2c2` | ~14 | Line `#d4d4d4` |
| `#b2b2b2`, `#b8b8b8`, `#bcbcbc`, `#aaa`, `#a9b8c8`, `#b8bac2` | ~12 | Strong line `#a8a8a8` (or `inverse-muted` on dark) |
| `#f1f1f1`, `#f2f2f2`, `#fafafa`, `#f4f4f4`, `#ececec` | ~15 | White or Paper; `#f1f1f1` on dark is Inverse at 94 % |
| `#faf9f6`, `#e7e7e2` | 3 | Paper; Mist (cookie banner uses a warm off-white that belongs to Sunset, not Replay) |

---

## 6. Typography

Three families, each with one job. **[O]** `layout.tsx`, Figma 4.1 to 4.5.

| Family | Role | Cuts loaded | Fallback |
|---|---|---|---|
| **STK Bureau Serif** | Voice: headlines, numbers, CTAs, card titles | Book 400 (`--font-serif`, local woff2); Regular 400 (`--font-serif-regular-only`, a 71-glyph trial cut used for H3 and some mobile H1/H2, falling back to Book for missing glyphs) | Newsreader 400 (web, Google) → Georgia → Times New Roman (Figma 4.4) |
| **Geist** | Explanation: body, labels, nav, form fields | Variable, via `next/font` | Helvetica → Inter (Figma 4.5) |
| **Geist Mono** | Filing: eyebrows, metadata, indexes, footer links, record headers | Variable, `preload: false` | ui-monospace, Menlo |

### 6.1 Scale

The Figma type-setting frame (4.3) defines the scale; the code implements it with responsive steps. **[O]** Both sources agree on desktop values. Tracking is expressed in Figma as a percentage and in code as pixels; the pixel values are the percentage of the size (72 × −0.04 = −2.88).

| Role | Family / weight | Desktop | Tablet (`sm`) | Mobile | Leading | Tracking | Colour |
|---|---|---|---|---|---|---|---|
| Headline (H1) | STK Bureau Book | 72 px | 56 px | 42 px | 100 % (mobile 103.5 %) | −4 % | Ink |
| Sub-heading (H2) | STK Bureau Book | 44 px | 44 px | 36 px | 100 % | −4 % | Ink / White |
| Card title (H3) | STK Bureau Regular | 24 px (32 px in dark panels) | 24 | 22 to 24 | 110 % | −1 % | Ink |
| Statement number | STK Bureau Book | 56 to 72 px | | 42 | 100 % | −4 % | Ink / White |
| Body | Geist 400 | 16 px | 16 | 14.5 px | 140 % | −3 % | Body gray |
| Small | Geist 400 | 14 px | | | 140 % | −3 % | Body / Reading gray |
| Label | Geist Mono 400, uppercase | 12 px | | | 133 % | +2.5 % (Figma) / +6 % (footer code) | Label gray |
| Eyebrow | Geist Mono 400, uppercase | 10 px | | | 150 % | +8 % | `#7b7b7b` light (fails AA; use Body `#727272`) / `#a9b8c8` on blue |
| Nav link | Geist 400 | 14 px | | | | tight | `#777` → Ink (fails AA at rest; use Body `#727272`) |
| CTA | STK Bureau, uppercase | 16 px (hero) / 12 px (nav) / 14 px (form) | | | 80 % | +8 % | White on Ink |
| CTA "Value my data" | STK Bureau, sentence case | same | | | | +1 % | White on Ink |

Sources: H1 pattern repeated in 9 hero files; H2 pattern in 20 files; `cta-type` utility in `globals.css`; `SENTENCE_CASE_CTA` in `lib/cta.ts`. **[P]**

### 6.1a Licensing and the secondary serif

**[O]** The Figma font names are `STK Bureau Serif Book-Trial` and `STK Bureau Serif Regular-Trial`, and `layout.tsx` calls the Regular file "its trial file". The production site is serving trial font files. **[R]** P0: confirm a commercial web licence for STK Bureau Serif before launch and swap in the licensed files. The fonts are deliberately **not** included in this kit for the same reason.

**[O]** WIP guideline 4.2 says "Hedvig Letters Serif appears narrowly as an accent." The site loads **Newsreader** as the serif fallback and Hedvig nowhere (an earlier build used it). **[R]** Decide which one exists. The recommendation is neither as a visible accent: Newsreader stays as a silent fallback only, and 4.2 drops the Hedvig line. A third serif dilutes the one-voice rule.

### 6.2 How hierarchy is made

Hierarchy comes from family switches and size, almost never from weight. The serif has one weight on the page; Geist and Geist Mono at 400 only (the WIP guideline is explicit: "keep the weight regular and never use bold"); Geist Mono carries uppercase instead of bold. **[P]** There is no bold serif anywhere in the product and no bold body copy. This is the single most important typographic rule: **do not add weight to make something louder; change its size or its family.**

Secondary hierarchy comes from colour: Ink for the thing said, Body gray for the thing explained, Label gray for the thing filed. **[P]**

**[O]** `cta-type` declares `font-weight: 500` on STK Bureau Serif, but only the 400 cuts are loaded, so browsers render Book. The declaration is inert. **[R]** Remove it so the intent is honest; if a medium cut is ever licensed, decide deliberately.

### 6.3 Density: product versus marketing

The marketing site runs at the generous end of the scale: 72 px headlines, 24 px gaps, one idea per section. **[O]** The forms (Value my data, Referral) are the closest thing to product UI and run tighter: 48 px fields, 14 px labels, 24 px between fields, a 52 px submit. **[O]** `value-my-data-form.tsx`.

**[R]** For any future authenticated product surface, hold the families and colours and compress the scale one step: H1 44, H2 32, H3 20, body 14, labels 11, eyebrows 10, with 16 px as the base gap instead of 24. Keep tracking percentages identical; they are what make the serif read as Replay at any size.

### 6.4 Responsive behaviour

Observed steps: H1 42 → 56 → 72, H2 36 → 44, body 14.5 → 16, side padding 24 → 72. **[P]** Several mobile headings swap to the Regular cut (`font-serif-regular`) at small sizes and back to Book at `sm`. **[O]** About, AI Buyers, Referrals, Data & Trust heroes. Others stay Book throughout. **[O]** Home, Blog, Careers. Both look acceptable; the inconsistency is a drift, not a decision.

**[R]** Formalise one rule: Book everywhere, Regular only for H3. The 71-glyph trial cut is a liability on headlines that may contain punctuation it lacks.

---

## 7. Layout and spacing

Derived from the shipped site, not from a generic grid. **[O]** Tailwind v4 defaults supply the scale; the product uses a narrow subset of it.

### 7.1 Container

- Content max width **1560 px**, centred. 46 uses. **[P]**
- Side padding **24 px** on mobile (`px-6`), **72 px** from `sm` upward (`px-18`). 17 and 16 uses. **[P]** The Figma design width is 1440 with 72 px outer padding, which yields a 1296 px content column; on wider viewports the column grows to 1560 before locking. **[O]**
- Reading measure: hero sublines are capped at **669 px** (desktop) and **420 px** (mobile); long copy columns at 560 px. **[P]** `max-w-[669px]`, `max-w-[560px]`.

### 7.2 Spacing scale (as used)

| Step | px | Tailwind | Observed role |
|---|---|---|---|
| 1 | 4 | `gap-1` | Icon to label inside a tag |
| 2 | 8 | `gap-2` | Label to field; stacked small text |
| 3 | 12 | `gap-3` | Title to body inside a card; hero stack on mobile |
| 4 | 16 | `gap-4` | Related rows |
| 5 | 20 | `gap-5` | Card padding |
| 6 | **24** | `gap-6` | **The base.** Fields, hero stack, column gaps, nav items. 55 uses, the most common value in the codebase |
| 8 | 32 | `gap-8` | Column group gaps |
| 10 | 40 | `gap-10` | Section-internal blocks; mobile section gaps. 33 uses |
| 16 | 64 | `gap-16` | Section rhythm on mobile; footer |
| 20 | 80 | `gap-20` | Section rhythm on tablet; Figma "80 inner" |
| — | 176 | `gap-[176px]` | Footer nav to wordmark on desktop |

**[I]** The system is a 4 px base with 24 px as the working unit. Figma's "section padding 72 outer, 80/40 inner" **[O]** is consistent with this. There is no 8-point religion; 20 and 36 appear where the content needed them.

### 7.3 Breakpoints

Tailwind defaults carry the structure: `sm` 640 (475 uses), `lg` 1024 (592 uses), `xl` 1280 (56). `md` 768 is nearly unused (8). **[O]** Custom breakpoints appear for specific layouts: `min-[800px]` 38, `min-[900px]` 24, `min-[1150px]` 22, `min-[1350px]` 33, `min-[1200px]` 8, `min-[1800px]` 8. **[O]** The nav has a bespoke rule for 1560 to 1800 px that lets the fixed header's side frames align to the content column. **[O]** `navbar.tsx`.

**[R]** Formalise three tiers (mobile < 640, tablet 640 to 1023, desktop ≥ 1024) and treat the custom `min-[...]` values as layout-local exceptions that must be commented. Most of them exist because an illustration needed a specific width; they should not leak into component rules.

### 7.4 Section rhythm

A section is: eyebrow tag → H2 → body (≤ 560 px) → the working (diagram, index, panel) → optional CTA. **[P]** Sections are separated by dashed hairlines or by a surface change (Paper → Mist → Night), not by large empty margins. Vertical gaps between major blocks are 64 / 80 / 176 depending on viewport. **[P]**

---

## 8. Shape language

**Radius: 0.** **[P]** The product is rectilinear by decision, not by omission. The brief's dislikes include "excessive rounded cards"; the shipped site has none. The only circles are 5 px status dots and the tab-progress ring.

**Corners carry meaning instead of radius.**
- **Fold.** A 16 px black triangle clipped into the top-right of grain cards, turning Sky on hover. **[O]** `grain-card.tsx`. Reads as a dog-eared page.
- **Registration ticks.** Short hairlines at the corners of illustration frames. **[O]** Data & Trust illustrations.
- **Jagged bottom edge.** A 22 px tear texture along the bottom of grain cards on tablet and up. **[O]** `hover-card-texture-lines.png`.

**Borders.** 1 px. Dashed for guides and rules (`#d4d4d4`), solid for frames and fields (`#a8a8a8`), solid Ink for selected states and the cookie buttons. **[P]** Dashed white at 16 % on Night. **[O]**

**Buttons.** Rectangles, Ink fill, white label, no border, `overflow-hidden` to contain the hover layers. Hero size 260 × ~62 px (`px-6 py-5`), nav size `px-5 py-3`, form size full-width × 52 px. **[O]**

**Inputs.** 48 px tall, full width, transparent fill on a White card, 1 px `#d4d4d4` border, 20 px horizontal padding, 15 px Geist. Focus: border → Ink. Selects add a 16 px chevron at 16 px from the right. **[O]** `value-my-data-form.tsx`.

**Pills.** None. Tags are bordered rectangles (§11.2).

**Panels.** Mist or Night or Cobalt rectangles, full-bleed inside the container, often with a dashed rule inset from the top and bottom. **[O]** Figma 3.3 "Colour in Use".

**Dividers.** Dashed hairline, full container width, or dashed white on dark. **[P]**

**Why it works.** Square geometry plus hairlines plus paper texture reads as *document*, which is the category Replay wants to own: a register of licensed data, not a SaaS dashboard. Rounding anything would move it toward the Sunset site and toward every other startup. The constraint is the differentiator.

---

## 9. Iconography

Two systems coexist. **[O]**

**UI icons.** 18 inline SVG components in `components/ui/icons.tsx` (briefcase, shield, bar chart, check circle, heart, film, file, user box, gavel, zap, box, landmark, align left, arrow up-right, arrow right, search, chevron right, chevron down). Stroke-based, `currentColor`, rendered at 12 to 16 px (`size-3`, `size-4`), round caps and joins. **[O]** The de-identification engine borrows Remix Icon path data under Apache-2.0. **[O]** `deid-pass-engine.js`.

**Illustrative marks.** Sector and record-type pictograms used in the industries diagram and data index, plus a "diamond mark" used as a journal bullet. **[O]** `industries-diagram.tsx`, `diamond-mark-icon.tsx`.

**Rules a new icon must follow.** **[I]** from the existing set:
1. Stroke, not fill. 1.5 px at 16 px; scale stroke with size.
2. Square-ish construction with round caps. Corners of the glyph may be sharp; line ends are round.
3. Sized to the cap height of the text it sits beside (12 px icon next to 12 px mono label; 16 px next to 14 px Geist).
4. Icon-to-text gap is 6 px (`gap-1.5`) inside tags, 16 px (`gap-4`) in rows. **[O]**
5. Colour follows the text it labels: Body gray at rest on light surfaces (Label gray on Night), Ink on hover, never Blue. **[P]** `role-row.tsx` chevron.
6. Marketing iconography may be drawn as line pictograms with hatch fills to match the isometric illustrations; UI iconography never has fills.

**[R]** Consolidate on one icon source (Remix Icon is already in the repo under a compatible licence, and its outline set matches the stroke rules above) and document the 18 UI icons as the approved set. Today a new icon is drawn ad hoc.

---

## 10. Imagery and graphic language

### 10.1 Core visual assets (ownable, keep)

| Asset | What it is | Where | Status |
|---|---|---|---|
| **Paper grain** | Light grain SVG multiplied over Paper at ~11 % | Every page, nav, cards | [P] |
| **Guilloché weave** | Fine interlaced line pattern, soft-light over cobalt | Button hover, growth card hover, blue panels | [P] |
| **Colour bar** | Six-segment Sky/Olive/Gray/Sun strip with noise | Under nav, under heroes, inside button hover, on OG images | [P] |
| **Redaction bar** | Hatched or guilloché-filled bar over an identifier | De-identification sections, specimens | [P] |
| **Record header texture** | Repeated `CLASSIFICATION PROPRIETARY DATA / LICENSING`, `RL-2026-001 // Version 1.0`, `def load_dataset(source)` in 6 to 8 px mono at low contrast | Hero side patterns, footer backdrop, CTA collage | [P] |
| **Torn specimens** | Cut-outs of real operating records with torn edges and no shadow | De-id pass, CTA collage, Data & Trust hero stream | [P] |
| **Footer wordmark** | Grain-filled "Replay" with dashed white stroke and pointer-following shimmer | Footer | [O] |
| **Bottom stripes** | Nine Ink stripes of increasing height stepping in with scroll | Beneath dark panels: pricing, referral payouts, careers benefits | [O] |
| **Isometric slabs** | Extruded stacked plates with hatch fills and pinned callouts | How it works, Data & Trust, AI Buyers | [P] |

### 10.1a The texture library (shipped in `textures/` and `patterns/`)

WIP guideline section 5.0 Art Direction is an empty title card. **[O]** This is that section's content. The repo holds 14 texture files that are really 6 textures, re-exported per page: **[O]** measured by image difference.

| Kit file | What it is | How it is applied | Duplicates in `public/images/` |
|---|---|---|---|
| `grain-clear.webp` | Transparent grain, ~11 % alpha | Multiply over Paper; nav, cards, mobile menu | `texture-grain-light.webp` = `footer/grain.webp` (byte-identical) |
| `grain-clear-faint.webp` | Same grain, ~5 % alpha | Multiply on tiles where 11 % is too heavy | `ai-buyers/catalog/tile-texture.webp` |
| `grain-light-vector.svg` | Vector grain | Nav backdrop | `grain-light-texture(-optimized).svg`, `header-bg-right.svg` |
| `paper-white.webp` | Near-white paper with grain | Band tops, white panels | `texture-grain-white.webp` |
| `grain-card-ground.svg` | Mid-grey grain | Grain card ground | `medium-grey-texture-bg.svg`, `-btn-bg.svg`, `hover-card-grey-bg*.svg` |
| `weave-canvas.webp` | Grey canvas weave | **Soft-light over the brand gradient**; 185 px tile on buttons, 296 px on cards | `texture-canvas-blue.webp`, `button-hover-weave.webp`, `growth-card-hover/texture-soft-light.webp`, `ai-buyers/soft-light-texture.webp`, `pricing/grain-texture.webp` (five files, one image) |
| `weave-denim.webp` | Blue denim weave | Multiply at ~11 % under the gradient | `growth-card-hover/texture-multiply.webp`, `about/letter-grain-texture.webp` |
| `bar-noise.webp` | Horizontal noise strip | Soft-light over the colour bar | `hero/bar-noise.webp`, `data-trust/assurance-bar-texture.webp` |

Patterns and devices, with their source: `colour-bar.svg` / `colour-bar-noise@2x.png` / `colour-bar-nav.svg` (generated from `PROCESS_BAR_COLORS` and `NAV_STRIP_SEGMENTS`), `colour-strip-left/right.svg` (button hover strips), `colour-bar-vertical.png`, `stepped-stripes.svg` (generated from `bottom-stripes.tsx`), `dashed-rule.svg` and `-inverse.svg` (1 px, 4/4), `corner-fold-ink/sky.svg` (16 px), `guilloche.svg` (the "who it's for" line pattern), `torn-edge.png`, `record-header-strip.png` and `record-header-field.png`, `light-sweep-band.webp`, `button-ground.svg`, `data-strata.webp`, `record-streams.webp`, `specimen-collage-left/right.webp`.

**[R]** Point every component at the canonical eight and delete the duplicates. One texture per job makes the next page cheaper and stops five slightly different weaves drifting further apart.

### 10.2 Decorative experiments (used once; do not propagate without a decision)

- Mesh texture on buyer cards (`buyer-card-hover-mesh.png`). **[O]**
- ~~Canvas blue texture~~. Correction to 1.0: it *is* the weave (see 10.1a), used on the Data & Trust standard section and blog hero.
- Hard-light blend on hero H1 (`mix-blend-hard-light`) so grain shows through type. **[O]** 4 uses. Subtle; keep if it survives a contrast check.
- Luminosity blend on a few images. **[O]** 2 uses.
- Team photo pile with pointer tilt on Careers. **[O]** `use-team-collage-tilt.ts`. The one place the brand is allowed to be playful, and the code comments say so explicitly. Keep it quarantined there.

### 10.3 Potential future brand assets

- **The scan line.** A single horizontal rule with a soft falloff that passes over a record and leaves placeholders behind. **[O]** It exists inside the de-id pass. **[R]** Extract it as a reusable loading or processing device for product UI.
- **The hallmark / assay roundel.** Named in the project vocabulary, not yet drawn. **[R]** A small stamped seal (mark + "Verified" or the record ID) would give case studies and certificates a signature closing device.
- **The record ID format.** `RL-2026-001` already appears as texture. **[R]** Make it real: assign every licensed dataset, case study and standard document a visible ID in this format.

### 10.4 Treatment rules

Photography: none in the product today, apart from team photos on Careers. **[O]** **[R]** If photography is ever introduced, it is documentary (people at desks, real offices), desaturated toward the grain, never stock, never hero-scale.

Cropping and composition: specimens are shown at an angle or in a fanned stack, cut off by the frame edge; nothing is centred and fully contained unless it is the subject of a diagram. **[P]**

Colour treatment: artwork may use the pastel set; UI may not. Blue always arrives with its weave. Noise is multiplied over every flat colour area wider than a hairline. **[P]**

Visual density: one working illustration per section. Where two are needed (Data & Trust rows), they alternate sides. **[O]**

---

## 11. Product design language

What exists is a marketing site with two forms, one consent dialog and a mobile menu. The component vocabulary below documents those, and marks what a future product surface would need.

### 11.1 Buttons

**Purpose.** One primary action per page. The brand CTA is "Value my data" and it appears in the nav, the hero, the closing section and the form. **[P]**

**Anatomy.** Ink rectangle; serif label; hero variant has a subtle pattern image under the label; a hover layer stack (gradient, weave, inset edge) and two 6 px colour-strip edges that start translated off-canvas. **[O]** `hero-cta-button.tsx`, `primary-button-hover.tsx`.

| State | Behaviour | Source |
|---|---|---|
| Default | Ink fill, white label | [O] |
| Hover | Hover stack fades in over 300 ms; strips slide in over 300 ms; gated to `(hover: hover)` | [O] |
| Focus | Browser default outline (likely clipped by `overflow-hidden`) | [O] gap |
| Active | `scale(0.98)` 150 ms on form submit and cookie buttons; **absent on hero and nav CTA** | [O] gap |
| Disabled | 60 % opacity, `cursor-wait` | [O] form only |
| Loading | Label changes to "Sending…"; fieldset disabled; `aria-busy` | [O] |
| Touch | Mobile CTA uses `on="active"` so the hover stack reveals on press | [O] `cta-section-mobile.tsx` |

**Secondary button.** Bordered Ink rectangle, no fill, 12 px label. **[O]** Cookie banner "Reject" / "Accept" only. **[R]** Promote this to the documented secondary button and use it wherever a non-primary action is needed, instead of inventing per-page variants.

**Text link.** Geist 14 px, Body gray → Ink on hover, 150 ms. **[O]** Nav. Footer links are mono uppercase with a growing underline. **[O]**

**When not to use.** Never two primary buttons in one viewport. Never a primary button inside a card.

**[R]** Add `active:scale-[0.98] transition-transform duration-150 ease-snap` to `HeroCtaButton` and the nav CTA, and move the focus outline to the outer element with `outline-offset-2` so `overflow-hidden` does not clip it. These are the two most-pressed controls on the site and they are the only pressables without press feedback.

### 11.2 Section tag (eyebrow)

Mono 10 px uppercase label in a 32 px tall bordered box; optional 32 px square icon cell sharing the border. Light tone: `#b2b2b2` border, `#7b7b7b` text. Dark tone: `#a9b8c8` both. **[O]** `section-tag.tsx`. **[R]** Align to tokens: Strong line border, Body gray text (Label gray fails AA on Paper); dark tone uses Inverse at 60 %.

### 11.3 Inputs and selects

Documented in §8. Labels are 14 px Body gray above the field, 8 px gap. Error copy is 14 px, `role="alert"`, placed after the verification widget. **[O]** No inline field validation exists; errors are form-level. **[R]** When field-level errors are needed, mark the field border Error red and put the message in Error red 12 px Geist beneath it, 4 px gap. Keep the border 1 px; do not add a ring.

### 11.4 Cards

Three card types exist. **[O]**

| Card | Surface | Border | Hover | Where |
|---|---|---|---|---|
| Grain card | Grey grain texture | `black/15`, corner fold, torn bottom | Optional: floods cobalt, text → white, fold → Sky | About, Referrals |
| Mist panel | `#eaebf1` | Dashed inset rules | None | Pricing, How it works |
| Catalog / shelf tile | White | `#a8a8a8` at 60 % | Border → Ink, slight transform | AI Buyers catalog, Revenue stream shelf |

Cards are 240 px tall fixed height in grids, 20 px padding, 12 px title-to-body gap. **[O]** `grain-card.tsx`.

### 11.5 Navigation

Fixed header, 64 px tall, Paper at 97 % with 16 px backdrop blur and grain. **[O]** On desktop, scrolling past the top drops the header 16 px, fades the full-width backdrop out and fades two bordered side frames in, so the nav appears to sit inside the content column as a framed strip. **[O]** `navbar.tsx`, `use-page-scrolled.ts`. Transition 200 ms with a bespoke curve, 500 ms for the opacity swaps.

Mobile nav: full-screen Paper sheet below the header, fades and slides 8 px over 300 ms ease-out on open, 200 ms ease-in on close; Escape closes; body scroll locked. **[O]** `mobile-nav.tsx`, `use-disclosure.ts`.

**[R]** The backdrop blur plus a grain image on a fixed element is the most expensive thing on every page. Consider dropping the blur: the 97 % Paper plus grain already reads as solid. Measure before and after.

### 11.6 Tabs

Three implementations exist. **[O]**

| Tabs | Cell | Label | Selected | Progress | Where |
|---|---|---|---|---|---|
| De-identification (landing) | Bordered `#ccc`, 40 / 72 px tall, equal width | Serif 16 / 18 px | An Ink fill that slides between cells (the duplicated-layer clip technique) | A 5 to 8 px strip filling with `clip-path: inset` from the bottom, linear | `deidentification-tabs.tsx` |
| Standard (Data & Trust) | Bordered `#ccc`, dashed from `sm`, 42 / 74 px | Serif 16 / 22 px | Text colour | Slide 220 ms | `standard-tab-button.tsx` |
| Assurance (Data & Trust) | Underlined row, `#b8b8b8`, 33 px | Sans 14 px uppercase | Text colour, 150 ms | None | `assurance-tab-button.tsx` |

The first is the strongest and the most on-brand: a bordered serif cell, an Ink indicator that moves rather than appears, and a progress strip that uses `clip-path` instead of width. **[R]** Make it the one Tabs component; the other two become variants (dashed border; compact).

**[R]** Tabs should be keyboard-navigable with arrow keys. Verify; the hooks handle viewport pause but there is no arrow-key handling in the components.

### 11.7 Accordion / disclosure

Two implementations. FAQ: `grid-template-rows` 0fr → 1fr, 200 ms ease-out, a `+` that rotates into `−`, dashed rules between items, numbered `01`. **[O]** `faq-item.tsx`. Valuation: same grid technique at 500 ms, with a status dot and a media panel that swaps. **[O]** `valuation-accordion.tsx`. **[R]** One duration (see §12.6).

### 11.8 Menus, dropdowns, popovers, tooltips

None exist beyond native `<select>`. **[R]** When one is needed: Paper surface, 1 px Strong-line border, no radius, no shadow or at most `0 8px 28px -10px rgba(20,21,24,.10)`; enter at `scale(0.97)` + opacity from the trigger's origin over 150 ms `--ease-snap`; exit 100 ms. Tooltips 125 ms, mono 12 px, Ink surface with white text.

### 11.9 Modals and drawers

Cookie preferences is the only dialog. **[O]** `cookie-preferences.tsx`. The consent banner is a bottom sheet on a warm off-white (`#faf9f6`), which is off-palette. **[R]** Banner on Paper or Mist. Dialogs: centred, Paper, 1 px Ink border, no radius, `transform-origin: center`, fade + `scale(0.98)` 200 ms. Drawers: slide from the edge with `cubic-bezier(.32,.72,0,1)` (already used in the de-id pass), 300 ms in, 200 ms out.

### 11.10 Alerts and toasts

Form-level messages only. **[O]** **[R]** Inline alerts are a bordered rectangle (Error red or Olive border, Paper fill, 14 px Geist). No toasts on the marketing site. If a product surface needs them, they enter from the bottom-right with a 200 ms translate, stack with 8 px gaps, and never auto-dismiss errors.

### 11.11 Tables

None exist. **[R]** Tables are the register: hairline dashed rows, mono 12 px headers in Body gray, serif numbers in Ink, right-aligned figures, no zebra striping, no row hover fill above `black/[0.03]`.

### 11.12 Metrics and numbers

Big serif value (56 to 72 px, −4 %) over a 14 px Body-gray label. **[O]** Stats grid, pricing tiers. Values count up on entry; non-numeric values ("Millions", "Billions") fade. **[O]** `animated-stat-value.tsx`, `parse-stat-value.ts`. Bar tiers use stacked 8 px segments in Bar gray / Teal / Sky. **[O]** `PRICING_TIERS`.

### 11.13 Badges and status

A 5 px dot (`rounded-full`) that changes colour for the active accordion step; mono uppercase text beside it. **[O]** `valuation-accordion.tsx`. This is the only status indicator. **[R]** Keep it: a 5 px dot plus a mono label is the status badge. Colours: Label gray (idle), Ink (active), Olive (done), Error red (failed). No pills, no filled chips.

### 11.14 Data visualisation

Bars only, in the accent set, with noise multiplied. **[O]** No line charts, no pies. **[R]** Hold to bars and tables. If a line chart is unavoidable: 1 px Ink line, no area fill, dashed Line grid, mono axis labels.

### 11.15 Empty, loading and error states

Loading: the submit button label changes and the form is disabled; the Cal.com embed shows its own loader. **[O]** Empty: none exist. Error: a sentence in Error red (Tailwind's, see §5.5) with the user's answers preserved. **[O]**

**[R]** Empty states are a Mist panel with a serif H3 and one Body line; no illustration. Loading states use the scan line (§10.3) rather than a spinner where the wait is Replay doing work on data; a 1 px progress bar otherwise.

---

## 12. Motion: the design-engineering lens

The repository ships Emil Kowalski's design-engineering skill under `.agents/skills/emil-design-eng/` and the team has adopted its two easing curves verbatim. **[O]** `--ease-snap: cubic-bezier(0.23, 1, 0.32, 1)` and `--ease-swift: cubic-bezier(0.77, 0, 0.175, 1)` in `globals.css`, with a comment that they are opt-in for new work because 22+ call sites already use Tailwind's `ease-out`. This section applies that philosophy to what is actually there.

There is no animation library. **[O]** `package.json` lists React, Next and the Cal.com embed. Everything is CSS transitions, CSS keyframes, or `requestAnimationFrame` inside custom hooks. That is the right stack for this brand and should stay.

### 12.1 Motion personality

**Measured ease-out. Nothing springs.** **[I]** Of 62 easing declarations, 40 are `ease-out`, 23 are `--ease-snap` (a stronger ease-out), 10 are `ease-in-out` for on-screen movement, 2 are `ease-in` (both on exits). There is no bounce, no overshoot, no spring. Distances are short (8 to 14 px). Opacity does most of the work.

The brand is Serious, Timeless and Calm. The motion should feel like a well-made mechanism: it responds instantly, it settles without wobble, and when it does something slow it is because it is showing you something.

### 12.2 Should this animate? (an audit of what does)

| Animation | Frequency | Purpose class | Verdict |
|---|---|---|---|
| Nav link colour on hover | Tens/day | Feedback | Keep, 150 ms |
| Primary button hover stack | Tens/day | Feedback + brand | Keep; 300 ms is at the limit; do not go longer |
| Press scale on buttons | Tens/day | Feedback | Keep; **extend** to hero and nav CTA |
| Header dropping into frame on scroll | Once per page | Spatial | Keep |
| Mobile nav open/close | Occasional | State transition | Keep |
| FAQ / accordion open | Occasional | State transition + preventing jump | Keep at 200 ms |
| Tab content crossfade | Occasional | State transition | Keep at 200 ms |
| Scroll reveals (fade / blur / slide) | Once per section | Preventing jarring entry | Keep, once only, ≤ 500 ms |
| Stat count-up | Once | Explanation | Keep |
| Revenue shelf tiles staggering in | Once | Explanation | Keep (200 ms per tile) |
| Bottom stripes stepping with scroll | Once | Ambient / brand | Keep; it is tied to scroll position, not time, so it cannot feel slow |
| De-identification pass | Once, long | Explanation | Keep; it is the product demo |
| How-it-works auto-advance | Continuous while visible | Explanation | Keep but stop on user interaction |
| Footer wordmark shimmer (pointer) | Hover | Delight / brand | Keep; it is contained to the footer |
| Footer wordmark one-shot sweep | Once | Delight | Keep |
| Team collage tilt | Hover, Careers only | Delight | Keep, quarantined |
| Catalog marquee | Continuous | Ambient | Acceptable; linear; pauses off-screen? **verify** |
| Smooth anchor scrolling (`motion-safe:scroll-smooth`) | On anchor click | Spatial | Keep; already motion-safe |

Nothing animates on keyboard-initiated actions. **[O]** Nothing is animated that a user triggers hundreds of times a day, because nothing on a marketing site is. When a product surface appears, the rule is explicit: **command-style actions, filters, keyboard navigation and list changes do not animate.**

### 12.3 Every animation needs a job

Classification of what exists, with where it feels off. **[I]**

- **Feedback:** hover colours, press scale, input focus border. Purposeful. The gap is coverage (hero/nav CTA have no press).
- **Spatial continuity:** header into frame; mobile nav sliding from where the menu button is; mobile "How it works" media moving to sit under the open step over 200 ms. **[O]** `VALUATION_MEDIA_SWAP_MS`. Purposeful.
- **State transition:** accordions, tabs, button hover stack. Purposeful. The valuation accordion at 500 ms feels slow next to the FAQ at 200 ms; same component, two personalities.
- **Explanation:** count-ups, de-id pass, isometric sequences, step cycles. Purposeful and allowed to be long.
- **Delight:** wordmark shimmer, collage tilt. Two instances, both at the edges of the experience. Correct amount.
- **Ambient:** record-header texture drift in the Data & Trust hero (`hero-stream-drift.ts`), catalog marquee, bottom stripes. Low cost, low contrast. Acceptable. The drift must honour reduced motion (it checks `prefers-reduced-motion`). **[O]**

Where it is **excessive:** the home hero stacks the de-identification pass, grid lines, two bottom fades (one a `backdrop-filter` blur), the pipeline line and the colour bar. **[O]** `home-hero.tsx`, `hero-bottom-fade.tsx`. Each is fine; together, above the fold, they compete with the headline for the first second. **[R]** Let the headline resolve before the pass starts (a ~300 ms delay) and replace the blurred bottom fade with a plain gradient fade; the grain is already doing the softening. A second hero component, `hero-section.tsx`, with side patterns and a blur reveal, is no longer mounted by any page and should be removed or formally retired.

Where it is **inconsistent:** eight distinct `cubic-bezier` values exist in TS/TSX files beyond the two tokens (`(0.65,0,0.35,1)` on the header, `(.32,.72,0,1)` and `(.4,0,.9,1)` in the de-id pass, `(0.4,0,0.2,1)` twice, `(0.22,1,0.36,1)`, `(0.37,0,0.63,1)`). **[O]** Each was reasonable locally; collectively they are five motion personalities.

Where it is **abrupt:** `transition-none` appears 18 times as a deliberate "do not animate the first render" guard. **[O]** Correct use. Where it is **disconnected:** none found; triggers and effects are adjacent.

### 12.4 Cohesion: the default motion set

**[R]** Four durations, three curves, one distance scale. Everything in UI maps to one row. Ceremonies are exempt and documented individually.

| Token | Value | Use |
|---|---|---|
| `motion/duration/instant` | 100 ms | Tooltip, exit of small popovers |
| `motion/duration/fast` | 150 ms | Press, hover colour, input border |
| `motion/duration/base` | 200 ms | Disclosure, tab crossfade, popover enter, menu exit |
| `motion/duration/slow` | 300 ms | Primary button hover stack, mobile nav enter, reveal fade |
| `motion/duration/reveal` | 500 ms | Scroll-in reveals, count-up |
| `motion/easing/snap` | `cubic-bezier(0.23, 1, 0.32, 1)` | Every enter, every hover, every press |
| `motion/easing/swift` | `cubic-bezier(0.77, 0, 0.175, 1)` | On-screen movement between two positions |
| `motion/easing/drawer` | `cubic-bezier(0.32, 0.72, 0, 1)` | Sheets and drawers (already in the de-id pass) |
| `motion/easing/exit` | `ease-in` | Exits only, and shorter than the enter |
| `motion/distance/sm` | 8 px | Reveal slide, menu slide |
| `motion/distance/md` | 14 px | Stripes step |
| `motion/scale/press` | 0.98 | Every pressable |
| `motion/scale/enter` | 0.97 | Popovers, dialogs |

Defaults by interaction:

| Interaction | Default |
|---|---|
| Hover | `fast` + `snap`, colour/opacity only, gated to `(hover: hover) and (pointer: fine)` |
| Press | `transform: scale(0.98)`, `fast`, `snap`; on touch-first controls, the hover stack reveals on `:active` |
| Enter (UI) | opacity 0 → 1 and `scale(0.97)` or `translateY(8px)` → rest, `base`, `snap`, origin at the trigger |
| Exit (UI) | opacity → 0, `instant` or `base`, `ease-in`; always faster than enter |
| Enter (content on scroll) | opacity (+ optional 8 px rise), `reveal`, `snap`, once, threshold 0.3 |
| Navigation | header frame 200 ms `swift`; mobile nav 300 ms in / 200 ms out |
| Popover / tooltip | 150 ms / 125 ms, `snap`, `transform-origin` from trigger |
| Modal | 200 ms, `snap`, centred origin, overlay fades 150 ms |
| Feedback (success) | colour change only, `fast`; no pop |
| Loading | scan line or 1 px bar, linear |

### 12.5 Physicality

Direction is consistent: things enter from where they come from. The mobile nav descends from the header; the primary button's colour strips enter from the button's own edges; the header drops into its frame; the shelf tiles rise into place in reading order. **[O]** Popovers do not exist yet, so the trigger-origin rule is a recommendation, not an observation.

Velocity: enter curves are strong ease-out (fast start). Exits are plain `ease-in` or shorter durations. **[P]** Correct.

Momentum: the wordmark shimmer follows the pointer with a 0.44 lerp per frame, which gives it a trailing, physical feel without a spring library. **[O]** The collage tilt writes transforms directly to `style` on pointer move to avoid re-rendering siblings. **[O]** Both are good models for any future pointer-driven decoration.

Interruption: see 12.6. Reversal: hover stacks are CSS transitions, so leaving mid-hover reverses smoothly. **[O]**

### 12.6 Interruptibility

Interactive states use transitions, not keyframes, so rapid hover in/out, open/close and tab-switching retarget mid-flight. **[P]** The FAQ and valuation accordions keep content mounted and animate `grid-template-rows`, which is interruptible and avoids measuring height. **[O]** Good.

Known risks: **[O]**
- Scroll reveals use keyframes (`reveal-*`). They are one-shot and latched (`once: true`), so they never need to reverse. Acceptable.
- The count-up and the step cycles are rAF-driven with explicit cleanup on unmount and on viewport exit. **[O]** Acceptable.
- A manual click on an auto-advancing tab restarts the interval rather than stopping the cycle. **[O]** `use-deidentification-cycle.ts`: "Clicking even the current tab restarts its full reading interval." At 15 s this is defensible; the Data & Trust de-identification steps run at 5 s, where a reader who chose a step will be moved off it. **[R]** One rule for all cycles: a manual selection stops auto-advance until the section leaves and re-enters the viewport.
- The valuation accordion's 500 ms open means a user who clicks two steps quickly watches two half-animations. **[R]** 200 ms, same as FAQ.

### 12.7 Performance

What is good: transitions name `opacity`, `transform`, `colors`, `[grid-template-rows]`, `[width]` explicitly in most places. **[O]** `will-change` is set only on the de-id scene and its moving parts. **[O]** Textures are optimised SVG/WebP with a dedicated script. **[O]** `scripts/optimize-textures.mjs`. Performance budgets exist and are checked in CI. **[O]** `docs/performance/`.

What to watch: **[O]**
- 42 bare `transition` (all properties) declarations. Replace with the property list.
- Keyframes that animate `height` and `width`: `reveal-grow-height`, `reveal-grow-width`, `reveal-unfurl`, `terms-line-grow`. They run once on decorative, isolated elements, so they are survivable, but a `clip-path: inset()` or `scaleY` with `transform-origin: top` gives the same reveal without layout. **[R]** for any new work; migrate old ones opportunistically.
- `backdrop-blur-[16px]` on the fixed nav over a grain image (see §11.5), and a second `backdrop-filter: blur()` in the home hero's bottom fade. Two backdrop filters on the first screen is one too many.
- `filter: drop-shadow(0 0 60px …)` on the wordmark hover and `filter: blur(10px)` in the blur reveal. Both are bounded and short-lived. Acceptable; do not add more filter animations.
- `mix-blend-mode` on 80+ layers. Blends force compositing; they are static, so the cost is paint, not frames. Acceptable.
- Seven MP4 step videos. They play only in view and are deferred. **[O]** `use-in-view-playback.ts`. Acceptable.

Implementation guidance for the existing stack: CSS transitions for every interactive state; CSS keyframes for one-shot reveals; rAF only when the value depends on pointer or scroll position (shimmer, tilt, stripes); never a layout property in a transition that a user can trigger repeatedly. WAAPI is a reasonable upgrade path for the de-id engine if it ever needs scrubbing or pausing mid-animation.

### 12.8 Accessibility

`prefers-reduced-motion` is respected in two layers: Tailwind `motion-reduce:` variants (18 `transition-none`, 5 `opacity-*`, 5 `hidden`, 4 `transform-none`, 3 `animate-none`) and explicit `matchMedia` checks in the five rAF hooks. **[O]** Under reduced motion the wordmark sweep becomes a 300 ms opacity change, the stream drift stops, the collage does not tilt, the signature does not draw. **[O]** This is the right shape: reduced, not dead.

Focus visibility: `focus-visible:outline-2` exists on legal and cookie controls only. **[O]** Nav links, CTAs, tabs and accordion buttons rely on the browser default, and several sit inside `overflow-hidden` containers that will clip it. **[R]** A global rule: `:focus-visible { outline: 2px solid var(--color-ink); outline-offset: 2px }` on Paper and `outline-color: #fff` on dark surfaces, with `overflow` never hiding it.

Touch: hover stacks are gated behind `(hover: hover)` on the primary button and role rows, and the mobile CTA reveals on `:active` instead. **[O]** The growth card hover and nav link hover are not gated. **[R]** Gate them.

Keyboard: Escape closes the mobile nav; `inert` is applied to closed accordion regions; `aria-expanded`, `aria-controls`, `aria-busy`, `role="alert"` are used correctly. **[O]** Tabs need arrow-key support (verify).

Contrast: four text colours fail AA as shipped; see the table in §5.3 and the P0 in §23. **[O]**

Readability under animation: text is never animated while a user might be reading it, except the tab crossfade, which replaces text wholesale. **[P]** Correct.

---

## 13. Invisible details

Things most users will never name but will feel. Each is either already right (keep) or a small fix.

| Detail | State | Note |
|---|---|---|
| Press feedback on the two most-used buttons | **Missing** | Hero and nav "Value my data" have no `:active` scale. Everything else does. |
| Focus ring clipped by `overflow-hidden` | **Likely** | Primary buttons wrap the hover stack in an overflow-hidden container. Verify with Tab. |
| Hover timing | Right | 150 ms colours, 300 ms for the rich hover stack. Do not exceed. |
| Border opacity on dark | Right | Dashed white at 16 % on Night; 60 % white text. Reads as engraved, not grey. |
| Shadow softness | Right | The one UI shadow is `-10px` spread, 10 % Ink. If another is ever added, copy it exactly. |
| Baseline alignment of serif numbers and mono labels | Right | `leading-none` on the number, label in its own block beneath. Keep numbers from sharing a line with mono. |
| Icon alignment in tags | Right | Icon cell shares the border via `-mr-px`; the double hairline is collapsed. |
| Loading transition on submit | Right | Label swap, disabled fieldset, cursor-wait, answers preserved on failure. |
| Content shift on reveal | Right | Reveal keyframes animate opacity/transform; sections reserve their height. The de-id pass reserves `aspect-ratio: 1440/520` so the hero never collapses before the engine sizes it. |
| Modal origin | N/A | Only the cookie dialog; when more arrive, centre origin for modals, trigger origin for popovers. |
| Cursor | Right | `cursor-pointer` set explicitly on custom buttons; `cursor-wait` while sending. |
| Touch hover false positives | **Partial** | Gated on primary button and rows, not on cards and nav links. |
| Interrupted transitions | Right | Transitions, not keyframes, for everything interactive. |
| Disabled states | Partial | Only the form submit has one. |
| Error transitions | **Missing** | Error text appears without a fade; and its colour is Tailwind's, not the brand's. |
| Empty states | **Missing** | None designed. |
| Image drag and text select on decoration | Right | `user-select: none; -webkit-user-drag: none` on all `img, svg`. |
| Hover delay bleeding into stagger | Right | Documented and fixed in `globals.css` for the collage: stagger lives on `animation-delay`, never `transition-delay`. |
| First-paint flashes | Right | 18 `transition-none` guards on initial render. |
| Dash pattern fidelity | Accepted | CSS dashed is not 4/4; illustrations draw their own. |
| Responsive edge: 1560 to 1800 px | Right | Bespoke nav padding so the framed header aligns to the column. Commented. |
| Legacy filename | Off | `sunset-logo.svg` is the Replay signature. |
| Text contrast | **Off** | Nav, eyebrows and small labels sit just under 4.5:1. Nobody can say why the site feels slightly faint; this is why. |
| Em dash in error copy | Off | "saved in this tab—please try again" breaks the house rule. |

---

## 14. Brand ↔ product bridge

Use this table to answer "does this new feature feel like Replay?" Each row is one line of reasoning from identity to pixels.

| Brand DNA | Design principle | Product expression | Motion expression |
|---|---|---|---|
| A document, not a dashboard | Paper first, ink second (2.1) | Paper ground with grain; cards as regions with lines; no shadows | States change ink, not elevation |
| A register of licensed data | Square, registered, hairline (2.2) | Zero radius; 1 px dashed and solid lines; indexed lists; corner folds | Lines grow, fill or darken; shapes never morph |
| The worth reveal is the magic moment | One blue, and it is the reveal (2.3) | Cobalt gradient + weave on the primary hover and value panels only | Blue arrives on hover or on scroll-in, 300 to 500 ms, then stays |
| Trust by showing the process | Show the working (2.4) | Specimens, scan line, redaction bars, isometric slabs; stats count | Explanatory sequences are long, literal, scroll-gated and one-shot |
| Institutional voice | Engraved, not campaigned (2.5) | Serif statements, mono metadata, sentence case, full stops | Microcopy never cheers; no celebratory motion |
| Precise and calm | Fast ink, slow ceremony (2.6) | 150/200/300 ms UI; 500 to 900 ms ceremonies | Strong ease-out, no springs, exits faster than enters |
| Amex, not Spirit | Premium by restraint (§3) | One primary action per page; one blue; one colour bar | Rich hover is rare; everything else is quiet |
| Not Sunset | The anti-wind-down filter (memory) | No tan, no rounded cards, no horse, no landscapes; cool paper and cobalt | Nothing fades to black; nothing closes |

---

## 15. Marketing versus product

### Shared DNA (never varies)

Paper, Ink, Night, Mist and the one blue. STK Bureau Serif for voice, Geist for explanation, Geist Mono for filing, at the tracking percentages in §6. Zero radius. Hairline dashed and solid borders in Line and Strong line. The colour bar. Grain over flat colour. The signature and its clear space. Sentence-case headlines with full stops. The press scale, the snap curve and the four durations.

### Marketing flexibility (where expression is allowed)

Hero-scale serif (72 px and up; the brand guideline uses 200 px for section titles). The full texture set: weave, hatch, canvas, torn specimens, record-header type as texture. Blend modes. The artwork pastels. Long explanatory animations and auto-advancing sequences. The footer wordmark shimmer. The Careers collage. OG images and social headers built from the hero and the colour bar. **[O]** Figma Brand Guideline 6.x shows exactly this range.

### Product discipline (where usability wins)

A future authenticated surface keeps the shared DNA and drops the rest. Type compresses one step (§6.3). Textures reduce to grain on Paper only; no weave except on the single primary action's hover. No auto-advancing anything. No scroll reveals. No blend modes. Semantic colours appear (error, success) and are the only accents on screen. Motion is `fast` and `base` only; the `reveal` and ceremony tiers do not exist in product. Keyboard-first: every control has a visible focus state, every list is arrow-navigable, nothing animates on a keyboard action. Loading uses the scan line when Replay is processing data, a 1 px bar otherwise.

The test: a product screen with the chrome removed should still be identifiable as Replay from its type, its lines and its one blue.

---

## 16. Content and voice

Audited across the landing page, Data & Trust, AI Buyers, Blog, About, Careers, Referrals, the forms, the consent UI and the Figma copy frames. **[O]**

**Voice.** Plain, declarative, second person, present tense. The reader is "you", the company is "Replay" or "we". Claims are specific ("60+ categories", "26 days median valuation to first payment", "US buyers only"). Objections are answered in the same breath they are raised ("You'll be asked to represent that the data is yours to license. However, we understand it's almost impossible to verify…"). **[P]**

**Sentence structure.** Short. Often a statement followed by a shorter one: "This is a license, not a sale." "Your exposure is capped." Fragments are allowed when they are lists of nouns: "Names, emails, API keys, access tokens, customer records." **[P]**

**Capitalisation.** Headlines and buttons in sentence case. **[P]** Exception: eyebrows, footer links, labels and record headers are uppercase because they are mono and read as filing, not speech. **[P]** "Value my data" is always sentence case even where other CTAs are uppercase. **[O]** `lib/cta.ts`. Figma 3.3 shows "VALUE MY DATA" uppercase; the code deliberately overrides this. **[O]** mismatch, see §21.

**Punctuation.** Full stops on headlines. No exclamation marks anywhere. No em dashes (house rule; one violation found in error copy). Ellipsis for in-progress ("Sending…"). Numbers with units written tight: `$100K+`, `25-100 Employees`, `26 days`. **[P]**

**Headline behaviour.** The verb carries the headline: "Fund growth by licensing the data you already have." "Securely license your data. Stay in compliance." "Find out what your data is worth before you decide anything." **[P]** Headlines name the reader's asset ("the data you already have", "your data") in nearly every case. **[P]**

**CTA language.** One brand CTA, "Value my data". Secondary: "Read the standard", "Request catalog access", "Submit referral", "Send for review". Verb first, object second, no "now", no "today", no "get started". **[P]**

**Terminology (use these, not synonyms).** License (never sell, for the seller's data). De-identify / de-identification (never anonymise). Operating data / operating records (never "exhaust", never "big data"). Frontier AI labs and data labs (the buyers). Named buyers. Record classes. Valuation. Revenue share. Raw data vs cleaned output. The standard (the de-identification standard). **[P]**

**Product language.** Steps are named with a one-word label and a two-word title: Value / Get a valuation; Terms / Receive an offer; Protect / De-identify your data; Payout / Get paid. **[O]** Tabs are nouns: "PII Coverage", "Our Pipeline", "Data Policy". **[O]**

**Error messages.** Full sentences, first person plural, with the next step: "We couldn't receive your request. Please try again." **[O]** Never blame the user; never say "oops".

**Microcopy.** Form labels are plain nouns ("Work email", "Years of operation"). Helper text is one sentence. Consent copy is unambiguous and the two buttons are styled identically. **[O]**

**Words never used.** Unlock, leverage, seamless, cutting-edge, next-generation, powerful, revolutionise, journey, empower, wind down, shut down, closure. **[I]** from the brief and the shipped copy.

---

## 17. Responsive behaviour

Principles first, breakpoints second.

**Hierarchy survives; decoration leaves.** Mobile keeps the serif headline, the eyebrow and the primary CTA at full strength, and drops side patterns, framed nav, the torn bottom edge on cards, and most parallax. **[P]** `hidden sm:block` on decoration; `lg:` on framing.

**Navigation collapses to a sheet, not a hamburger drawer.** Full-screen Paper beneath the 64 px header, same link styles, CTA at the bottom. **[O]**

**Density holds; scale drops.** Gaps step 24 → 24, section gaps 176 → 64, headlines 72 → 42, body 16 → 14.5, side padding 72 → 24. Component padding (20 px cards, 48 px fields) does not change. **[P]**

**Typography steps, it does not fluid-scale.** Three fixed sizes per role. The one container-query exception is the revenue shelf, whose type scales with its own width (`cqw`) because the illustration is a drawn object, not text. **[O]**

**Interaction models change by capability, not viewport.** Hover stacks are gated on `(hover: hover)`; touch-first buttons reveal on press. **[O]** Primary button. Media that would float beside an accordion on desktop moves beneath the open step on phones with a 200 ms swap. **[O]**

**Images and illustrations crop, they do not squash.** The de-id scene scales from a 1440 × 520 design and crops rather than shrinks on narrow screens. **[O]** `deid-pass.css`. Stripes are capped at their design height.

**Motion reduces with viewport in practice.** Fewer reveals on mobile because fewer decorative layers exist there; auto-cycles pause off-screen, which on a phone is most of the time. **[I]**

**Keyboard and mouse.** Desktop gets framed nav and footer-link underlines; keyboard users need the focus rule in §12.8 on every viewport.

**[R]** Document the three tiers and move all `min-[…]` breakpoints behind named layout constants with a comment, so a new page can be built without reading the old ones.

---

## 18. Design tokens

**The canonical, machine-readable version of this section is the YAML front matter of `DESIGN.md`**, exported to `tokens/theme.css` (Tailwind v4 `@theme`) and `tokens/tokens.dtcg.json` (W3C). The tree below explains the architecture; if a value differs, DESIGN.md wins.

A semantic architecture, mapped to what exists today. Values marked [O] are in use; [R] rows are proposed names for existing values or gaps to fill. Implement in `@theme` in `globals.css` so Tailwind generates the utilities (`bg-surface-paper`, `text-content-body`, `border-line`).

```text
color/
  brand/        blue-deep #133264 [O]   blue-bright #147dba [O]
  surface/      paper #fcfcfc [O]  white #ffffff [O]  mist #eaebf1 [O]
                ink #141518 [O]  night #080808 [O]  overlay paper@.97 [O]
  content/      primary #141518 [O]  body #727272 [O]  reading #565656 [O]
                label #898989 [O]  inverse #ffffff [O]  inverse-muted #fff@.6 [O]
  border/       line #d4d4d4 [O]  strong #a8a8a8 [O]  focus ink [O]
                inverse #fff@.16 [O]
  interactive/  primary-rest ink [O]  primary-hover gradient/brand [O]
                row-hover #000@.03 [O]  row-press #000@.05 [O]
                disabled-opacity .6 [O]
  semantic/     error #bf000f [O-figma, R-code]  success olive #54702f [R]
                info blue-deep [R] (blue-bright fails as text)
  accent/       sky #499df8  olive #54702f  sun #eae058  bar-gray #7e7e7e
                teal #0e9692  slate #3a5979  [O]
  artwork/      butter #f0edd1  sage #b7d3c1  cream #fbf1d0  lavender #c1b4d8 [O-figma]

gradient/
  brand         linear-gradient(180deg, blue-deep 27%, blue-bright 144%) [O]

texture/
  grain-light   /images/grain-light-texture-optimized.svg, multiply, ~.11 [O]
  weave         /images/button-hover-weave.webp, soft-light, 185px [O]
  bar-noise     hero bar noise, soft-light, 720x30 [O]

typography/
  family/       serif "STK Bureau Serif" [O]  sans Geist [O]  mono "Geist Mono" [O]
  size/         h1 72/56/42  h2 44/36  h3 24  stat 56-72  body 16/14.5
                small 14  label 12  eyebrow 10  nav 14  cta 16/14/12 [O]
  weight/       400 everywhere, including mono (Figma 4.3: "never use bold") [O]
  leading/      display 1.0  card 1.1  body 1.4  label 1.33  eyebrow 1.5 [O]
  tracking/     display -0.04em  card -0.01em  body -0.03em
                label +0.025em  eyebrow +0.08em  cta +0.08em  cta-brand +0.01em [O]

space/          1=4 2=8 3=12 4=16 5=20 6=24 8=32 10=40 16=64 20=80 [O]
                container-x 24 / 72 [O]  section-y 64 / 80 / 176 [O]

radius/         none 0 [O]  dot 9999 (status dots only) [O]

shadow/         none [O]  card 0 8px 28px -10px rgba(20,21,24,.10) [O, one use]
                sheet 0 -2px 12px rgba(0,0,0,.04) [O, consent only]

motion/
  duration/     instant 100  fast 150  base 200  slow 300  reveal 500 [R, from O]
  easing/       snap cubic-bezier(.23,1,.32,1) [O]  swift cubic-bezier(.77,0,.175,1) [O]
                drawer cubic-bezier(.32,.72,0,1) [O, de-id]  exit ease-in [O]
  distance/     sm 8px  md 14px [O]
  scale/        press .98 [O]  enter .97 [R]
  cadence/      scroll-play-threshold .3 [O]  step-cycle 10000-15000 [O, inconsistent]

layout/
  container     1560 [O]   design-width 1440 [O]   measure 560 / 669 [O]
  nav-height    64 [O]     color-bar 8-9 [O]

breakpoint/     sm 640  lg 1024  xl 1280 [O]   (md unused; custom min-[] are local)
```

Rules for the token layer: **[R]**
1. Semantic names only in components (`bg-surface-mist`, never `bg-[#eaebf1]`).
2. No new colour without a token, and no new token without a row in §5.
3. Motion tokens are the only durations and curves allowed in UI code; ceremonies declare their own values in the hook that owns them, with a comment.
4. Tokens live in `globals.css` and are mirrored as Figma variables in one collection with light and dark modes. Today Figma has zero variables and zero styles. **[O]**

---

## 19. Design decision framework

For situations the rules do not cover.

### When introducing a new colour
1. Which named role is it filling: surface, content, border, accent, semantic, artwork? If none, it is not a colour, it is a mistake.
2. Is there an existing token within ΔE of it? Use that one. (The codebase already has six near-blacks.)
3. Is it blue? There is one blue. No.
4. Is it going on UI? Then it is not a pastel.
5. Does it pass 4.5:1 on Paper and on Night? If it only passes on one, it is a surface-specific token and gets a dark-mode alias.

### When introducing a new component
1. Is it a card, a tag, a button, a field, a row, a panel or a disclosure wearing a different name? Extend the existing one with a variant.
2. Does it have a radius? Remove it.
3. Does it cast a shadow? Replace it with a surface step or a line.
4. Write its states before its visuals: default, hover (gated), focus-visible, active (press scale), disabled, loading, error.
5. Does it live in `components/ui/`? Shared components do not belong in `modules/landing/`.
6. Does it exist in Figma as a component with variants? Make it so.

### When introducing a new animation
1. How often will one person see it per session? If more than a handful of times, it is `fast` or `base`, opacity and transform only, and interruptible.
2. What is its job: feedback, spatial, state, explanation, delight, ambient? If you cannot name one, delete it.
3. Does it use `snap`, `swift` or `drawer`? If it needs a fourth curve, write down why in the hook.
4. Does it animate a layout property? Use `clip-path`, `scale` or `grid-template-rows` instead.
5. What happens under `prefers-reduced-motion`? Opacity and colour survive; movement does not.
6. Is it triggered by a keyboard action? Then it does not animate.
7. Can it be interrupted and reversed without a visual glitch? If not, use a transition, not a keyframe.

### When creating a new visual asset
1. Does it show real operating material or a real mechanism? Stock, abstract and "AI-looking" assets fail here.
2. Is every flat colour area carrying grain or weave?
3. Are its edges torn, framed with registration ticks, or cut by the frame? Fully contained, centred, drop-shadowed objects are off-brand.
4. Does it use artwork pastels only in artwork, and never purple as a dominant?
5. Could a stranger tell which company's record it is? It should not; de-identified specimens use placeholders.

### When breaking an existing rule
1. Name the rule and the principle behind it (§2).
2. State what the user gains that the rule prevents.
3. Confine the break to one surface and one component, and comment it in code with the reason.
4. If the same break is needed a second time, it is not a break; it is a new rule, and this document gets updated.

---

## 20. Established, emerging, missing

### Established (strong, repeated, safe to enforce)
- Palette roles for Paper, Mist, Ink, Night, Body, Reading, Label, Line, Strong line, the two blues and the colour bar.
- The three typefaces and their jobs; the H1/H2/body scale and tracking.
- Zero radius; 1 px dashed and solid lines; corner fold; registration ticks.
- Container 1560 / padding 24 and 72 / 24 px base gap.
- Grain over Paper; weave over blue; noise over the colour bar.
- Primary button and its hover stack; "Value my data" in sentence case.
- Section tag; FAQ disclosure; count-up stats; scroll-play rule.
- Strong ease-out motion with no springs; two tokenised curves.
- Reduced-motion handling in hooks and classes.
- Voice: sentence case, full stops, specific claims, verb-first CTAs, fixed terminology.
- Module structure, kebab-case, logic in hooks, logging-free performance budgets.

### Emerging (present but undefined)
- Secondary button (cookie buttons).
- Status dot + mono label as badge.
- Scan line as a processing device.
- The record-ID format as real metadata.
- Semantic error colour (defined in Figma, not shipped).
- Dark-surface variants of tag, tab and text tokens (`#a9b8c8`, `#f1f1f1` and friends are ad hoc).
- Drawer curve (in the de-id pass, not in UI).
- The framed header on scroll as a nav behaviour worth keeping on other pages.

### Missing (needed before the system scales)
- Tokens in code (`@theme`) and in Figma (variables, text styles, components). Figma currently has 0 styles, 0 variables and 6 accidental components.
- A shared `components/ui/` with Button, SecondaryButton, Tag, Field, Select, Card, Panel, Disclosure, Tabs, Dot, Divider. Today most of these are exported from `modules/landing/`.
- Focus-visible rule applied globally.
- Press feedback on all pressables.
- Semantic success/info; empty states; inline field errors; tooltips; popovers; dialog; table.
- Icon set documentation.
- A dark-mode token map (Night sections prove the brand works dark; nothing is systematised).
- Motion token layer and a stop-on-interaction rule for auto-cycles.
- Content design: a short glossary, an error-copy pattern, and a rule for placeholder figures (every bracketed or benchmark number is unconfirmed until Brendan signs off; this is current practice and should be written down).

---

## 21. Current inconsistencies and design debt

| Current | Recommended | Why |
|---|---|---|
| Six near-black values (`#080808`, `#0c0c0b`, `#010101`, `#090909`, `#181a1b`, `#171717`) alongside Ink `#141518` | Ink for type and buttons, Night for dark sections, nothing else | They differ by less than a hairline of contrast and multiply the token count for no visible gain |
| Eight mid grays for text (`#777`, `#7b7b7b`, `#7e7e7e`, `#8a8a8a`, `#8d8d8d`, `#919191`, `#858585`, `#a2a2a2`) | Body `#727272`, Label `#898989`; Bar gray stays in artwork | Nav links at `#777` and body at `#727272` on the same screen read as a mistake under scrutiny |
| Eleven light grays for lines (`#d9d9d9`, `#ddd`, `#dedede`, `#e0e0e0`, `#cecece`, `#c2c2c2`, `#b2b2b2`, `#b8b8b8`, `#bcbcbc`, `#aaa`, `#a6a6a6`) | Line `#d4d4d4`, Strong line `#a8a8a8` | Figma names exactly two; the code has drifted per page |
| `--background: #ffffff; --foreground: #171717` in `globals.css` | Paper and Ink | Boilerplate values that every page overrides; a new page that forgets will render on the wrong white |
| Error text uses Tailwind `text-red-700` | `#bf000f` per Figma 3.1 | The only semantic colour in the brand is the one the code ignores |
| Cookie banner surface `#faf9f6` | Paper or Mist | A warm off-white from the Sunset palette, the exact tone the rebrand exists to leave behind |
| "Value my data" is sentence case in code; Figma 3.3 shows "VALUE MY DATA" | Sentence case everywhere for the brand CTA; update Figma | The shipped decision is right (it is a sentence, not a label); the file should match |
| Footer links tracked at +6 % (12 px) and +6 % (14 px); Figma label spec is +2.5 % | Pick one and record it in the type scale | Two sources, two numbers, same role |
| Mobile H1 uses the Regular cut on four pages and Book on four | Book for all headlines; Regular for H3 only | The Regular trial cut has 71 glyphs; headlines with punctuation it lacks fall back mid-word |
| `cta-type` declares `font-weight: 500` | Remove | No 500 cut is loaded; the declaration does nothing and implies a weight that does not exist |
| FAQ disclosure 200 ms; valuation disclosure 500 ms | 200 ms for both | Same component, two tempos; the slow one feels laggy on repeated clicks |
| Auto-cycle intervals 15 s (home), 10 s (AI Buyers), 5 s (de-id), with a comment claiming "same pace" | One documented cadence per content type, or a comment explaining each | The comment is wrong, which means the next person will "fix" one of them |
| A click restarts an auto-cycle's timer rather than stopping it (5 s on Data & Trust) | Stop on interaction; resume on re-entry | A reader who chose a step is moved off it |
| Eight bespoke `cubic-bezier` values beyond the two tokens | `snap`, `swift`, `drawer`, `ease-in` | Five motion personalities in one site |
| 42 bare `transition` declarations | Name the properties | `transition: all` animates things nobody asked for and costs frames |
| Keyframes animating `height`/`width` (`reveal-grow-*`, `reveal-unfurl`, `terms-line-grow`) | `clip-path: inset()` or `scaleY` with origin | Layout animation; cheap today because one-shot, expensive the day it is reused |
| Hero and nav CTA have no `:active` scale; five other pressables do | `active:scale-[0.98] duration-150 ease-snap` on every pressable | The most-pressed controls are the least responsive |
| Focus-visible styled on 4 files; browser default elsewhere, inside `overflow-hidden` | Global `:focus-visible` rule, offset outside the clip | Keyboard users lose the ring exactly on the primary buttons |
| Hover gated on 3 components; growth card and nav links not gated | Gate every hover behind `(hover: hover)` | Touch devices show sticky hover states |
| Navbar, Footer, SectionTag, HeroCtaButton, PrimaryButtonHover live in `modules/landing/` and are imported by every page | Move to `components/ui/` | The module convention says shared UI is shared; today About imports its nav from the landing module |
| Figma: 0 styles, 0 variables, 6 accidental components; button states exist as loose frames | One variable collection (light/dark), text styles for the scale, components for §11 | The design file cannot currently be used to make a consistent new page without copying |
| `sunset-logo.svg` is the Replay signature | `replay-signature.svg` | The old brand's name on the new brand's mark |
| Error copy contains an em dash | Rewrite with a full stop | House voice rule |
| Lavender `#c1b4d8` in the Figma artwork palette | Drop, or cap at a trace | The brief: "Hate purple" |
| CSS `border-dashed` vs Figma 4/4 dash | Accept for UI; SVG for illustration | Already the de facto rule; write it down |
| Nav links `#777` (4.36:1), eyebrows `#7b7b7b` (4.13:1), Label gray on Paper (3.41:1), Body gray on Mist (4.04:1) | Body `#727272` on Paper/White; Reading `#565656` on Mist; Label gray only on Night | All four fail WCAG AA for the text sizes they carry |
| Footer IA: code ships `01 Product / 02 Company / 03 Partners / 04 Legal` (Product = Overview, How it works, Valuation, Data cleaning); final Figma (`7388:31366`) is `01 Company / 02 Resources / 03 Partners / 04 Legal` (Customers, Blog, Careers under Resources) | Ship the Figma IA once Customers and Blog pages are live; until then, hide empty links rather than keep the old structure | Final design and production disagree on navigation |
| STK Bureau Serif served as trial files | Licensed files before launch | Legal exposure on every page |
| WIP 4.2 names Hedvig Letters Serif as an accent; code loads Newsreader | Drop Hedvig from 4.2; Newsreader as silent fallback only | Two documents, two serifs |
| Reviewer's note left inside WIP 2.2 body copy | Move to a Figma comment | It will ship to the client verbatim |
| 14 texture files for 6 textures | The canonical set in §10.1a | Drift between near-identical exports |
| `footer-logo.svg` (not the Replay mark) and `Vector.svg` unreferenced in `public/` | Delete | They look like masters and are not |
| Colour-bar widths sum to 111 % | Normalise | Code should say what the screen shows |
| WIP 5.0 Art Direction is empty | Fill from §10 and the kit's `textures/` and `patterns/` | The most distinctive part of the brand has no guideline page |

---

## 22. Brand evolution: the next one to three years

**Sacred.** The paper-and-ink surface model. Zero radius. STK Bureau Serif as the voice at −4 %. The one blue and the rule that it is the reveal. The colour bar. Sentence case with full stops. "Value my data". The de-identification pass as the product demo. The anti-wind-down filter.

**Formalise now.** The token layer in code and Figma. The component set in §11. The four-duration, three-curve motion set. The secondary button and the dot badge. The focus rule. The glossary.

**Can evolve.** The texture library can grow (a second weave for certificates, a canvas for case studies) as long as every texture is multiplied or soft-lit over a palette colour. The isometric illustration style can deepen into a consistent axonometric system with a fixed angle and a fixed hatch. The record-ID format can become real product metadata. Dark mode can become a first-class mode, since Night already carries entire sections.

**Where the brand can become more recognisable.** Three devices are already distinctive and under-used: the colour bar, the scan line, and the footer wordmark's grain-and-shimmer treatment. Used consistently (bar under every hero and on every social asset; scan line as the processing state in product; grain-filled serif as the closing device of decks and documents), they become signatures a buyer recognises before reading the name.

**Visual territory to own.** "The assay office for company data": certificates, registers, hallmarks, guilloché, record IDs. No competitor in the data-labelling space (Scale, Surge, Mercor, Turing, Handshake, micro1) looks like this; they look like infrastructure. **[O]** Memory, competitor filters. The adjacent licensed-data marketplaces look like marketplaces. Replay can look like the institution that certifies the asset.

**Signature interactions with potential.** (1) The primary button hover: cobalt flood with strips entering from the edges. Extend the strips idea to the selected tab and the active accordion step so "the bar appears when something is chosen" becomes a rule. (2) The scan line. (3) The count-up tied to viewport entry. (4) The bottom stripes stepping with scroll, which could become the page-transition device if the site ever has one.

**Intentionally quiet.** Body copy. Forms. Legal pages. Tables when they arrive. Error states. Navigation. None of these should ever acquire texture, blue or motion beyond `fast`.

**Over-designed today.** The home hero stacks four decorative systems above the fold. The team-collage tilt is right for Careers and would be wrong anywhere else. The number of distinct grays.

**Under-designed today.** Focus states. Press feedback on the primary CTAs. Errors and empty states. The dark-surface token set. The Figma file as a system rather than a canvas.

---

## 23. Prioritised action plan

### P0: Critical system problems

| Priority | Area | Problem | Recommendation | Impact |
|---|---|---|---|---|
| P0 | Tokens (code) | ~60 hex values hard-coded; 3 tokens exposed; `--background` wrong | Add the §18 colour, type and motion tokens to `@theme`; migrate by find-and-replace per §5.9 | Every future component inherits the system instead of a copy of it |
| P0 | Accessibility | Focus rings default and clipped; hover not gated on touch | Global `:focus-visible` rule; gate all hovers | Keyboard and touch users get the quality mouse users get |
| P0 | Press feedback | Hero and nav CTA have no active state | Add `scale(0.98)` 150 ms snap to `HeroCtaButton` and nav CTA | The brand's two most-pressed controls feel alive |
| P0 | Semantic colour | Error is Tailwind red; consent banner is Sunset off-white | Ship `#bf000f`; banner on Paper | Removes the last visible Sunset tone and the one off-brand red |
| P0 | Contrast | Nav, eyebrow, Label-on-Paper and Body-on-Mist fail AA | Swap per §5.3; add `npx @google/design.md lint DESIGN.md` to CI so a regression fails the build | Legible for everyone; the linter guards it from now on |
| P0 | Font licence | STK Bureau Serif shipped as trial files | Buy and swap the web licence before launch | Removes legal exposure |

### P1: Consistency and scalability

| Priority | Area | Problem | Recommendation | Impact |
|---|---|---|---|---|
| P1 | Shared UI | Shared components live in `modules/landing/` | Move Navbar, Footer, SectionTag, buttons to `components/ui/`; add SecondaryButton, Field, Select, Card, Panel, Disclosure, Tabs, Dot | New pages compose instead of copy |
| P1 | Figma system | No variables, styles or components | One variable collection (light/dark) mirroring §18; text styles for §6; components for §11 with states as variants | Designers and the Figma MCP can build on-brand without cloning old frames |
| P1 | Motion tokens | Eight bespoke curves; two accordion speeds; three cycle intervals; bare `transition` | Adopt the §12.4 set; 200 ms disclosures; one documented cadence; name properties | One motion personality; fewer dropped frames |
| P1 | Auto-cycles | A click restarts the timer; 5 s / 10 s / 15 s cadences disagree | Stop on interaction; one documented cadence | Respects the reader |
| P1 | Typography | Regular cut on headlines; inert `font-weight: 500`; label tracking mismatch | Book for H1/H2; remove 500; record one tracking value | Headlines never fall back mid-word |
| P1 | Naming | `sunset-logo.svg` | Rename | Removes a trap for the next engineer |
| P1 | DESIGN.md | Agents and new designers start from scattered sources | Commit `DESIGN.md` at the repo root; reference it from `AGENTS.md` and `CLAUDE.md`; paste `tokens/theme.css` into `globals.css` `@theme`, mapping the font variables to the existing `next/font` ones | One contract for people and agents; tokens in code in one step |
| P1 | Footer IA | Code and final Figma disagree | Ship the Figma structure as pages go live | Navigation matches design |
| P1 | Textures | 14 files, 6 textures | Point components at the canonical set; delete duplicates | Less drift, smaller repo |
| P1 | Guideline hygiene | Reviewer note in 2.2; Hedvig in 4.2; 5.0 empty | Clean 2.2 and 4.2; fill 5.0 from §10 | The client-facing guideline is accurate |

### P2: Refinement and distinction

| Priority | Area | Problem | Recommendation | Impact |
|---|---|---|---|---|
| P2 | Hero | De-id pass, grid, blurred fades and colour bar compete above the fold; `hero-section.tsx` is dead code | Delay the pass ~300 ms; plain gradient fade; delete the unused hero | Headline lands first; one hero to maintain |
| P2 | Signature devices | Colour bar, scan line and grain wordmark used inconsistently | Bar under every hero and on every social asset; scan line as the processing state; grain serif as the closing device in decks | Recognition before reading |
| P2 | Icons | Ad hoc set | Document the 18; adopt Remix outline as the source | Consistent weight and construction |
| P2 | States | No empty, inline-error, tooltip, popover, table | Design per §11.8 to §11.15 before any product surface ships | Product inherits the brand on day one |
| P2 | Nav performance | Backdrop blur over grain on a fixed element | Measure; drop the blur if 97 % Paper reads solid | Smoother scroll on mid-range devices |
| P2 | Record IDs | `RL-2026-001` is texture only | Make it real metadata on datasets, standards and case studies | The register becomes literal |
| P2 | Palette hygiene | Lavender in artwork | Drop or cap | Honours the brief |

---

## 24. Source map

| System | Figma | Repository | Notes |
|---|---|---|---|
| Palette names and values | Brand Guideline page → "Brand Guidelines" section → frames 3.1 Brand Palette (`7454:33318`), 3.2 Neutrals & Surfaces (`7454:33025`), 3.3 Colour in Use (`7454:33131`), 3.4 Usage Principles (`7454:33204`) | `app/globals.css` (`--color-ink`, `--color-blue-deep`, `--color-blue-bright`, `.bg-brand-gradient`); hex counts from `grep -rhoE '#[0-9a-f]{3,8}' modules components app` | Figma is the naming authority; code is the usage authority |
| Type scale | 4.3 Type Setting (`7446:25339`); 4.1/4.2 typefaces; 4.4/4.5 fallbacks | `app/layout.tsx` font loading; H1 class pattern in `modules/*/components/*-hero.tsx`; H2 pattern across 20 files; `cta-type` utility and `lib/cta.ts` | Tracking: Figma %, code px of size |
| Logo | Review file Brand Guidelines (WIP) `7547:3495`: 2.1 `7547:3845`, 2.2 `7547:3985`, 2.3 `7547:3995`, 2.4 `7547:4040`, 2.5 `7547:4652`, 2.6 `7547:4699`; master vectors `7547:3855` (signature), `7547:3994` (mark). Work file 2.0 to 2.6 (`7386:5516` …) | `public/images/sunset-logo.svg` (master), `lib/replay-wordmark-paths.ts` (footer lockup), `favicon-*.svg`. Unreferenced: `images/footer-logo.svg`, `public/Vector.svg` | Construction measured from the master |
| Colour bar | 3.3 card footers; Socials/OG frames | `process-bar.tsx`, `nav-color-strip.tsx`, `lib/constants.ts` (`PROCESS_BAR_COLORS`, `NAV_STRIP_SEGMENTS`) | Fixed proportions |
| Textures | Dev Handoff annotation "Base texture Blend Mode: Multiply…" (`6212:10030`) | `public/images/*texture*`, `grain-card.tsx`, `primary-button-hover.tsx`, `scripts/optimize-textures.mjs` | |
| Layout | LP page (`5134:1458`), Dev Handoff `LP - V4` (`6027:12679`); 1440 design width | `max-w-[1560px]` (46 uses), `px-6 sm:px-18`, gap counts | |
| Shape | Every page frame | Radius grep: 7 `rounded-*` total; `border-dashed` 186 | |
| Buttons and states | Dev Handoff button frames `Default` (`6172:58`), `Hover` (`6172:69`), accordion states (`6141:9041`, `6141:9047`, `6174:4499`, `6141:9044`), `Footer link: Hover` (`6375:1391`) | `hero-cta-button.tsx`, `primary-button-hover.tsx`, `navbar.tsx`, `footer.tsx`, `cookie-consent.tsx`, `value-my-data-form.tsx` | |
| Section tag | Throughout LP | `section-tag.tsx` | |
| Disclosure | Dev Handoff accordion frames | `faq-item.tsx`, `valuation-accordion.tsx`, `use-accordion.ts` | |
| Motion | Dev Handoff "Animations" section (`6164:18726`), Animation Playground page (`5984:6192`) | `globals.css` (`--ease-snap`, `--ease-swift`, keyframes), `modules/landing/hooks/*`, `use-replay-wordmark.ts`, `use-digit-count-up.ts`, `use-in-view.ts`, `deid-pass.css`, `deid-pass-engine.js`, `use-team-collage-tilt.ts`, `lib/constants.ts` (`SCROLL_PLAY_THRESHOLD`, `*_MS`) | Emil skill at `.agents/skills/emil-design-eng/SKILL.md` |
| Reduced motion | — | `motion-reduce:` variants; `matchMedia` in five hooks | |
| Illustration | Data Privacy page (`6294:593`), AI Buyer Page (`6846:138`), Animations section | `modules/data-trust/*`, `modules/ai-buyers/*`, `modules/landing/components/*illustration*` | Griffin isometric reference per project memory |
| Voice | Copy frames on About (`7154:24`) and Referral (`7154:25`) pages | `modules/*/lib/constants.ts`; `lib/site-config.ts` | Brendan signs off claims |
| Code conventions | — | `AGENTS.md`, `nextjs-conventions/SKILL.md` | Modules, kebab-case, hooks for logic |
| Brief and workshop | — | Project files: Brand + Website Questionnaire, Brand Workshop board PDF | Personality, references, anti-references |
| Final pages | Review file `UstspKowhUbYUC0zzT5DRc` page Final Pages `7384:3573`: Landing `7384:27176`, Landing mobile `7384:25105`, AI Buyers `7384:8906`, Data privacy `7384:13962`, About `7384:6776`, Referral `7384:4200`, Blogs `7384:17751`, Customers `7384:21631`, Footer `7388:31366` | `modules/*` | Footer IA differs (§21) |
| Brand guideline copy | Review file 2.1, 2.2, 3.1 to 3.4, 4.1 to 4.5 (`7547:*`) | — | 5.0 Art Direction empty |
| Textures | — | `public/images/**` (14 files → 6, §10.1a) | Duplicates measured by image difference |
| Prior decisions | — | Stored project memory: identity brief, anti-wind-down filter, locked tokens | |
| Format | DESIGN.md spec (Google Labs, `alpha`, CLI 0.3.x) | `DESIGN.md`, `tokens/` | Lints with 0 errors, 0 warnings |

---

*Maintained by PIXELUP. Changes to any [O] or [P] rule require a code or Figma change first and a document change second; changes to any [R] require a decision recorded in §23.*
