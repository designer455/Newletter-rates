# KTAHV — design.md

Brand implementation specification for AI-assisted design, development and copy.

Every rule below carries a **status tag** and a **source locator** like `OK 03:Forest swatch` — meaning *2026 Brand Manual, chapter 03, the panel titled "Forest swatch."* If a rule has no locator, it is not a rule.

---

## Specification metadata

| Field | Value |
| --- | --- |
| spec | kairali-ktahv-design-md |
| version | 3.0.0 |
| date | 2026-07-31 |
| brand | Kairali The Ayurvedic Healing Village (KTAHV) |
| legal entity | Kairali Ayurvedic Health Resorts Pvt. Ltd. |
| domain | ayurvedichealingvillage.com `2017 27:card back` |
| parent | Kairali Ayurvedic Group |
| primary source | Kairali Ayurvedic Group — Brand Manual, 2026 Edition, rev. 2 (chapters 01–11) |
| secondary source | Kairali Brand Manual © 2017 (42 pp., single-chapter "Brand Elements" structure) |
| governance | Governed directly by the master 2026 manual. No KTAHV sub-brand manual exists (unlike Villa Raag). |
| fabrication_allowed | false |
| inference_allowed | false |
| substitution_allowed | false |
| derived_claims | labelled_with_chain |
| build_layer | present_and_separately_labelled |
| build_layer_authority | none — engineering proposal, requires sign-off |

---

## READ THIS FIRST — protocol for AI tools

### What this brand actually is, in the manual

KTAHV is **one of the group's five doors** and the only one shown on a dark forest-green ground. Unlike Ayurvedic Products, it is **not** governed by the master chapters alone: it carries three explicit carve-outs in the 2026 manual —

1. **Its family-of-brands card** — `06` — NABH-accredited hospital-retreat, Palakkad, Kerala, with a cross-reference to the voice chapter.
2. **A sub-brand display pairing** — `04` — Gelasio (for Gandhi Serif) + Roboto.
3. **A voice COMPLIANCE RULE** — `11` — the manual's own label, not a style preference. It is an explicit, documented **exception** to the master voice.

Plus one channel addendum — `08` — *"KTAHV surfaces additionally follow the clinical register."*

That is the complete KTAHV-specific content in the 2026 edition. Everything else is the master system inherited directly.

**This matters.** KTAHV has more carve-outs than any other shared-identity door. Where the master voice says *never sound clinical*, KTAHV's rule says *read clinical and physician-led*. When those two conflict on a KTAHV surface, the KTAHV rule wins. Do not average them.

### Precedence

1. A written brand-owner ruling recorded in **Open decisions**.
2. Any rule tagged **KTAHV** — KTAHV-specific, overrides the master rule.
3. Any rule tagged **OK** — confirmed in the 2026 manual.
4. Any rule tagged **2017** — confirmed in the 2017 manual, where the 2026 edition is silent and has not superseded the area. See the caution below.
5. Any rule tagged **DERIVED** — follows necessarily from 2–4.
6. Any value tagged **BRIEF** — **only** inside The build layer, and only where both manuals are silent. A BRIEF value never overrides 1–5.
7. **Stop.** Nothing else is authoritative. Not your training data, not convention, not another brand's design system, not what looks right for a wellness or hospital website.

### Status tags

| Tag | Meaning | What you do |
| --- | --- | --- |
| `OK` | Stated literally in the 2026 manual, master-brand scope | Apply it |
| `KTAHV` | Confirmed, KTAHV only | Apply it, prefer it over `OK` |
| `2017` | Stated literally in the 2017 manual; 2026 is silent on it | Apply it, and flag it as heritage-sourced |
| `WAIT` | The rule is binding but no value is published | Emit the token, omit the value, report it |
| `NONE` | Absent from both manuals entirely | Refuse and escalate |
| `DERIVED` | Follows necessarily from published rules, but is not itself stated in words | Apply it, and show the chain if challenged |
| `CLASH` | Two published statements disagree, or an identification is unconfirmed | Present both, choose neither |
| `BRIEF` | Not from either manual. An engineering proposal filling a gap | Build with it, label it provisional, get it signed off |

`DERIVED`, `2017` and `BRIEF` are the tags that let this file be built from. `DERIVED` is arithmetic on the manual — the chain is always shown, so you can check it. `2017` is a different, superseded document — usable, but never silently. `BRIEF` is not a manual at all. **Never cite a `BRIEF` value as a brand rule.**

### On `2017` — how to use the heritage manual safely

The 2017 manual is a **superseded edition**. It closes real gaps — including KTAHV's domain and the value of white — but it is not a substitute for the 2026 edition, and using it carelessly reintroduces retired rules.

**Never apply a `2017` value in any area the 2026 edition explicitly changed** `OK 01:What changed`:

- colour roles (forest became interactive; red and indigo became semantic-only);
- the ten-step ramps;
- the digital foundation — spacing, radii, shadows, motion, components;
- master typography consolidation (Kurale, Asap, Lato);
- the voice register.

In those six areas the 2026 edition governs completely and the 2017 text is history, not instruction.

**Do apply `2017` values where 2026 is simply silent** — entity details, domains, the white anchor, the tagline clear-space module, sub-brand lockup orientations, named design elements. Each is tagged and traceable below.

When you emit a `2017` value, say so: *"sourced from the 2017 edition; the 2026 manual is silent — confirm it still stands."*

### On `WAIT` — the rule that makes this usable

The 2026 manual mandates a footer on forest-700 but publishes the colour ramps only as gradient images, so that value exists nowhere in writing. Do **not** refuse, and do **not** invent. Write the token reference and leave the value empty:

```css
footer { background: var(--kg-forest-700); /* WAIT — awaiting brand owner */ }
```

In a design context, label the swatch `forest-700 (unresolved)` and render no approximate colour. Then list every `WAIT` token you emitted at the end of your response, and state that the artefact cannot ship until the values are supplied.

**Never:** compute a tint or shade from an anchor · use a "close enough" hex · silently fall back to the anchor step · copy a ramp from Tailwind, Material or anywhere else · present the output as production-ready.

### Provisional build mode — how to ship while values are outstanding

**Use a visibly-wrong placeholder, never a plausible one.** A plausible substitute is the dangerous outcome: it looks finished and ships wrong. Put every unresolved value in one file, set it to a colour nobody could mistake for the brand, and make the build shout about it.

```css
/* tokens.provisional.css — the ONLY file containing unresolved values.
   Replace values here when the brand owner supplies them. Nothing else changes. */
:root {
  --kg-ink:          #FF00FF; /* WAIT P1 — placeholder, NOT a brand colour */
  --kg-forest-700:   #FF00FF; /* WAIT P1 */
  --kg-forest-800:   #FF00FF; /* WAIT P1 */
  --kg-marigold-300: #FF00FF; /* WAIT P1 */
  --kg-leaf-700:     #FF00FF; /* WAIT P1 */
  --kg-bronze-600:   #FF00FF; /* WAIT P1 */
}
```

- Magenta `#FF00FF` appears nowhere in either manual. That is precisely why it is used — it cannot be mistaken for a decision.
- The build prints a banner listing every unresolved token.
- Production deploys are blocked while `tokens.provisional.css` contains any placeholder. Wire this into CI.
- Every screenshot, demo and review deck carries the words **"provisional — 6 colour values outstanding."**

### On `NONE`

Reply exactly: **"Not published in the Kairali Brand Manual 2026 (rev. 2) or the 2017 edition."** Then name what is missing and which chapter would have held it. Do not answer from general design knowledge, and **do not import conventions from hospital, clinic or wellness-retreat design** because the facility happens to be medical.

### On `CLASH`

Quote both published statements with both locators. Ask for a ruling. If you must proceed, produce both variants and label them.

### Before you send

- [ ] Does every value I emitted have a locator I can name?
- [ ] Did I emit any hex, px, ms or font name that is not in this file?
- [ ] Is my `WAIT` list complete?
- [ ] Did I write KTAHV copy in the **clinical register** (§ Voice), not the general leisure-avoidant master tone alone?
- [ ] Did I use any leisure word — *spa, resort, holiday, getaway, escape*?
- [ ] Did I claim, imply or hint at a **cure**?
- [ ] Did I label every `2017` value as heritage-sourced?
- [ ] Did I cite a `BRIEF` value as though it were a brand rule? (It never is.)

---

## Source register

Two manuals govern this document. They are not interchangeable.

| # | Document | Structure | Status | Role here |
| --- | --- | --- | --- | --- |
| 1 | Kairali Ayurvedic Group — Brand Manual, **2026 Edition, rev. 2** | 11 chapters | Current | Primary authority. All `OK` / `KTAHV` locators refer to it. |
| 2 | Kairali Brand Manual, **© 2017** | 42 pp., "Chapter 1 — Brand Elements", page-numbered | Superseded | Gap-closing only. All `2017` locators are **page numbers**, e.g. `2017 p.08`. |

**Do not cite a chapter number against the 2017 manual.** It has no chapters 02–11; its locators are pages. A citation like `2017 03:Color` is invalid.

**The 2026 manual has eleven chapters.** A citation to a chapter 12 or 13 is invalid.

### Chapter map (2026)

| Ch | Title | Section here | KTAHV content? |
| --- | --- | --- | --- |
| 01 | Introduction | Brand | One clause — "our hospital-retreat" |
| 02 | The Logo | Logo | Inherited |
| 03 | Color | Colour | Inherited |
| 04 | Typography | Typography | **Carve-out** — Gelasio + Roboto |
| 05 | Photography & Texture | Photography | Inherited — see Decision 5 |
| 06 | The Family of Brands | Family position | **The card** |
| 07 | Digital Foundations | Foundations | Inherited |
| 08 | Digital Media & Channels | Channels | **Addendum** — clinical register on all surfaces |
| 09 | Applications & Stationery | Stationery | Inherited |
| 10 | Accessibility & Production | Accessibility | Inherited |
| 11 | Voice | Voice | **COMPLIANCE RULE** |

---

## Brand

| Field | Value | Tag | Source |
| --- | --- | --- | --- |
| Descriptor | The Ayurvedic Healing Village | `KTAHV` | 06:KTAHV card |
| Abbreviation | KTAHV | `KTAHV` | 06 |
| Lockup reads | Kairali · The Ayurvedic Healing Village | `KTAHV` | 06:KTAHV card |
| Business type | NABH-accredited hospital-retreat | `KTAHV` | 06:KTAHV card |
| Location | Palakkad, Kerala | `KTAHV` | 06:KTAHV card |
| Card ground | **Dark forest green** — the only door shown this way | `KTAHV` | 06:KTAHV card |
| Descriptor colour on that ground | Marigold | `DERIVED` | 06 — see chain below |
| Domain | **ayurvedichealingvillage.com** | `2017` | 2017 p.27, p.32, p.36, p.40 — card backs, letterhead, envelope |
| Legal entity | Kairali Ayurvedic Health Resorts Pvt. Ltd. | `2017` | 2017 p.40:letterhead |
| Registered address | Olassery P.O, Kodumbu, Palakkad Dist., Kerala – 678551 | `2017` | 2017 p.40 |
| Telephone | +91-492-3222553 / 3222623 | `2017` | 2017 p.40 |
| CIN | U55103DL1996PTC078294 | `2017` | 2017 p.40 |
| Group division | Kairali **Hospitality** | `2017` | 2017 p.27:card back |
| Established | 1908 — group-level; no separate KTAHV date | `OK` | 01:body |

**The card, in full, as published** `KTAHV 06`:

> **The Ayurvedic Healing Village**
> *NABH-accredited hospital-retreat — Palakkad, Kerala*
> *KTAHV always reads clinical and physician-led — never as leisure. See chapter 11.*

This is the longest of the four shared-identity cards. Products' card is one line; KTAHV's carries a credential and a compliance cross-reference.

**`DERIVED` — the descriptor is marigold, not bronze. Here is the chain:**

1. The 2026 manual states in words: *"only the Kurale descriptor changes — bronze on light grounds, marigold on dark."* `OK 06:body`
2. KTAHV's card is the one card rendered on the dark forest-green ground. `KTAHV 06`
3. Therefore KTAHV's descriptor is marigold, and the three light-ground doors carry bronze.

*Step 2 is read from the page layout as well as the text — the manual describes KTAHV's dark ground in words but does not restate the descriptor colour on the card itself. The conclusion is near certain, but confirm it in the same pass as the decisions below.*

**Statement** — *"Since 1908, Kairali has practised one thing: health through ayurveda."* `OK 01:body`

**Tagline** — health through ayurveda · **always lowercase** `OK 01, 11:We say`

> **`CLASH` — the tagline has two published forms.** The 2017 logo artwork sets it as *"health through ayurveda | since 1908"* on most pages `2017 p.03, p.06`, but *"health thru ayurveda | since 1908"* in the logo-form description `2017 p.04`, the 3D signage artwork `2017 p.17` and the design-element cartouche `2017 p.42`. Both are published. Use **"health through ayurveda"**, which is the form the 2026 edition carries — but never re-typeset either; the tagline ships as artwork.

**Brand quote** — *"Health through ayurveda — a promise kept daily since 1908."* — Kairali Ayurvedic Group `OK 11:pull quote`

### Approved claims

Since 1908 `OK 01` · health through ayurveda `OK 01` · NABH-accredited `KTAHV 06` · hospital-retreat `KTAHV 06` · Palakkad, Kerala `KTAHV 06` · four generations of practice `OK 11` · Panchakarma `KTAHV 11`

> *"Four generations of practice"* appears in chapter 11 as a description of how Kairali **speaks**, not as a marketing claim. It is usable because the master voice applies to this door in full — but it is a tone note promoted to a claim, so keep it in body copy rather than a headline assertion.

**Not an approved claim:** any cure, recovery rate, outcome guarantee, comparative efficacy, additional accreditation beyond NABH, physician credential, bed count, treatment duration, or price. Neither manual publishes any of it — `NONE`. **NABH is the only accreditation published. Do not imply a second one.**

### What the 2026 edition changed `OK 01:What changed`

- Forest green `#006038` becomes the **interactive** colour; leaf green remains the **identity** colour.
- Each 2017 anchor now carries a ten-step digital ramp with accessibility guidance.
- Red and indigo turn **semantic** — error and information, nothing else.
- Spacing, radii, shadows, motion and a full component library now ship with the brand.
- Type consolidated: Kurale, Asap and Lato serve the master brand; sub-brand faces mapped to free-licence equivalents.
- The voice register is written down.
- Rev. 2: Villa Raag joins as the fifth door.

> **The rev. 2 note names chapters 04, 06 and 11 as amended — *for Villa Raag*. It is not a statement about KTAHV.** Separately, and as this document's own cross-check rather than a manual claim: KTAHV happens also to be referenced in those same three chapters (its type pairing, its family card, its voice rule).

**These six areas are exactly where `2017` values must never be used.** See "On `2017`" above.

---

## Logo

No separate KTAHV logo construction exists. The master lockup applies, with the Kurale descriptor line reading **"The Ayurvedic Healing Village."** `OK 02` `KTAHV 06`

Three elements, **never altered** `OK 02:body` `2017 p.04`:

| Part | Value | Constraint |
| --- | --- | --- |
| Icon | Leaf and mortar-pestle | — |
| Lettering | Kairali lettering in **Freefrm721 BT** | Never re-typeset. **Always placed as artwork.** |
| Tagline | Set in **Kurale** | — |

### Clear space

A margin equal to the width of the letter **K** on every side. Nothing enters it. `OK 02:Clear space` `2017 p.12`

**Additionally** — the gap between the Kairali wordmark and the tagline is the height of a **horizontal letter "I"**. `2017 p.12` — *the 2026 edition does not restate this; it is heritage-sourced and should be confirmed.*

### Minimum size

| Context | Size | Tag |
| --- | --- | --- |
| Print, with tagline | 2.5 cm | `OK 02` `2017 p.05` |
| Print, without tagline | 1.5 cm | `OK 02` `2017 p.05` |
| Screen, full lockup | 72 px | `OK 02` |
| Screen, icon alone | 40 px | `OK 02` |

> **`CLASH` — what does 1.5 cm measure?** The 2017 manual captions it *"Minimum Size without Tagline"* and its specimen shows **icon + wordmark, tagline removed** `2017 p.05`. The 2026 spec derivatives read the same figure as **"icon alone."** These are different marks at the same number. Ask for a ruling before setting any small-format artwork. See Decision 3.

### On photography

Place on calm image areas, **or** set the logo on a primary-colour panel at reduced opacity. `OK 02` `2017 p.18`

The opacity percentage is `WAIT`. The 2017 manual says *"minimum opacity"*; neither edition gives a number.

### Approved colourways

| Ground | Treatment | Tag |
| --- | --- | --- |
| Light / ivory | Full colour lockup — **the default** | `OK 02` |
| Any primary | Solid single-colour lockup, or lockup reversed out of a primary ground | `2017 p.09` |
| **Dark forest green** | **Kairali wordmark in white, descriptor "The Ayurvedic Healing Village" beneath — this is KTAHV's own card treatment** | `KTAHV 06` |

The 2017 manual additionally publishes reversed lockups on the secondary greens and on the tertiary red and indigo `2017 p.10, p.11`. **Do not use these.** Red and indigo became semantic-only in 2026 `OK 01:What changed` — this is precisely the case where a `2017` value must not be applied.

Per-colourway ink values are not enumerated in either edition — `WAIT`. **Use the supplied artwork; do not sample it and re-derive values.**

### Never `OK 02:Never` `2017 p.13`

Recreate the logo from the manual · switch or restyle its colours · stray from the approved palette · stretch or distort it · rotate it to anything but 0° or 90° · alter any of its fonts · rearrange its elements.

> **Hard blocker.** No logo artwork files are published in either edition — no SVG, EPS, AI or PNG paths. `NONE 02`. The 2017 manual states the rule directly: *"Always use logo files from the Brand Guidelines respective folders. Never try to recreate them from the guidelines."* `2017 p.13`
>
> **No AI tool may generate, redraw, typeset or trace the logo, or place it on signage or facility mockups, under any circumstances.** Obtain artwork from the brand owner.

### Lockup orientations

Sub-brand lockups exist in **vertical** and **horizontal** arrangements, used as the available space requires. `2017 p.37` — *published for the Healing Village specifically in 2017; the 2026 edition does not restate it.*

---

## Colour

### Anchors `OK 03:swatches` `2017 p.08, p.10`

| Token | Name | Hex | PMS | CMYK | RGB | Role | Anchor step |
| --- | --- | --- | --- | --- | --- | --- | --- |
| `--kg-leaf` | Leaf | `#8E9D35` | 7495 C | C45 M20 Y100 K10 | 141 · 157 · 53 | Identity, focus, secondary | 500 |
| `--kg-forest` | Forest | `#006038` | 349 C | C90 M36 Y92 K32 | 0 · 96 · 56 | Actions, links, headers | 500 |
| `--kg-marigold` | Marigold | `#EEB41E` | 7409 C | C6 M30 Y100 K0 | 238 · 179 · 29 | Accent only, never body text | 400 |
| `--kg-bronze` | Bronze | `#C1882C` | 7510 C | C23 M47 Y100 K4 | 193 · 136 · 44 | Taglines, overlines | 400 |

The four anchors are **unchanged since 2017** and remain the print reference. `OK 03:body` — verified: the RGB and CMYK builds in the 2017 manual match the 2026 hex values exactly.

**Role change to note:** in 2017, Forest `#006038` was a *secondary* colour, used only *"in case primary colour does not suit the creative"* `2017 p.10`. In 2026 it is the interactive colour. **The 2026 role governs.**

### Semantic `OK 03:Heritage red & indigo`

| Token | Hex | Meaning |
| --- | --- | --- |
| `--kg-error` | `#BE202E` | Error only |
| `--kg-information` | `#26265F` | Information only |

These no longer appear decoratively. There is **no** success colour and **no** warning colour — `NONE`.

> **`CLASH` resolved by the 2017 manual.** The 2017 tertiary panel labels the indigo swatch **`#8d9c34`** while publishing its build as PMS 274 C, C100 M98 Y32 K24, **R38 G38 B95** `2017 p.11`. R38 G38 B95 converts to **`#26265F`** — the value the 2026 edition carries. The hex label `#8d9c34` is a transcription error in the 2017 artwork (it is one character from the leaf green `#8e9d35`). **Use `#26265F`.** No ruling needed; recorded here so nobody "corrects" it back.

### Neutrals

| Token | Value | Tag | Note |
| --- | --- | --- | --- |
| `--kg-white` | `#FFFFFF` | `2017 p.08` | **Gap closed.** White is published as a fourth *primary* colour in 2017 — PMS 663 C, C0 M0 Y0 K0, R255 G255 B255. The 2026 edition names white as a carrying ground without restating a value. |
| `--kg-ivory` | `#F7F4EA` | `OK 08:Favicon` | Ivory is the dominant ground across the whole system, yet its value appears once in the 2026 manual — in the favicon panel. That single published value is used here. |
| `--kg-ink` | — | `WAIT P1` | Ink carries footers, dark grounds, single-colour print and the 15.6 : 1 primary-text pairing, and has **no published value anywhere in either edition.** |

### Composition `OK 03:Proportions`

Ivory and white carry the composition. **Forest works. Leaf identifies. Marigold punctuates.** One accent moment per view.

### Ramps `OK 03:ramp caption`

Five families — Leaf, Forest, Marigold, Bronze and **Warm neutrals**. Steps 50→900. Ramp steps are screen-first; convert to CMYK per job `OK 10`.

**All 50 step values are `WAIT`.** The manual renders the ramps as continuous gradient swatches and publishes no value per step. Five steps are named as required elsewhere and are therefore blocking:

| Token | Required by | Source |
| --- | --- | --- |
| `--kg-forest-700` | Website footer, dark surfaces | 08 |
| `--kg-forest-800` | Dark surfaces | 08 |
| `--kg-marigold-300` | Dark-surface descriptors and accents — **including KTAHV's own descriptor** | 08 |
| `--kg-leaf-700` | Body text in leaf | 10 |
| `--kg-bronze-600` | Body text in bronze | 10 |

`--kg-marigold-300` is the highest-priority ramp value for this door specifically: it is the colour of KTAHV's descriptor line on its own dark card.

### `CLASH` — two forest values

| Statement | Value | Source |
| --- | --- | --- |
| A | `#006038` — the Forest anchor, PMS 349, print reference, the interactive colour | `03:Forest swatch`; `01`; `2017 p.10` |
| B | `#004226` — the favicon and app-icon tile ground, also called "forest" | `08:Favicon & app icons` |

Both are published verbatim and the manual calls both "forest." `#004226` may be a ramp step, but the manual does not say so. **Neither value appears in the 2017 manual as `#004226`** — the 2017 secondary green is `#006038`, which supports A being the true anchor but does not identify B. See Decision 2.

### `CLASH` — the orphaned secondary green

The 2017 manual publishes a **second** secondary green, `#a0b65e` (C39 M64 Y89 K36, R160 G182 B94) `2017 p.10`. It has no counterpart in the 2026 edition, which lists four anchors and two semantics.

Two readings: it was retired in 2026, or it survives unnamed as a ramp step (its lightness is consistent with a leaf-300/400). **Choose neither.** See Decision 4.

*Note also that the 2017 panel assigns `#a0b65e` the PMS number **7495 C** — the same number it assigns the primary leaf `#8e9d35`. One of the two is a misprint. This does not affect digital work but will affect any spot-ink print job.*

### Restrictions `OK`

- Marigold is never body text.
- Error and information colours are never decorative.
- Leaf green is never used for text on dark grounds.
- The published anchor values are the print reference.

`NONE`: HSL · LAB · LCH · gradients · opacity scale · dark-mode palette · disabled / hover / pressed palettes. *(Hover behaviour is a published rule — see Foundations. Only the palette values are absent.)*

### Copy-paste tokens

```css
:root {
  /* published — safe to use */
  --kg-leaf:        #8E9D35;  /* OK 03 */
  --kg-forest:      #006038;  /* OK 03 */
  --kg-marigold:    #EEB41E;  /* OK 03 */
  --kg-bronze:      #C1882C;  /* OK 03 */
  --kg-error:       #BE202E;  /* OK 03 — error only */
  --kg-information: #26265F;  /* OK 03 — information only */
  --kg-ivory:       #F7F4EA;  /* OK 08 */
  --kg-white:       #FFFFFF;  /* 2017 p.08 — heritage-sourced, confirm */

  --kg-forest-tile: #004226;  /* CLASH — favicon ground only, see Decision 2 */

  /* WAIT — do not fill these in yourself */
  --kg-ink:            /* WAIT P1 */;
  --kg-forest-700:     /* WAIT P1 */;
  --kg-forest-800:     /* WAIT P1 */;
  --kg-marigold-300:   /* WAIT P1 — KTAHV descriptor on dark */;
  --kg-leaf-700:       /* WAIT P1 */;
  --kg-bronze-600:     /* WAIT P1 */;

  /* NONE — not published. Do not invent. */
  /* --kg-success, --kg-warning */

  /* RETIRED — 2017 only, do not use */
  /* #a0b65e — see Decision 4 */
}
```

---

## Typography

### Master families `OK 04:body, 04:specimen` `2017 p.06, p.07`

| Role | Typeface | Weight / style notes |
| --- | --- | --- |
| Display, h1–h3, the tagline's face | **Kurale** | 400 only — **never bolded** |
| Body, UI, h4+ | **Asap** | 400–700; semibold for labels; italic for botanical names |
| Captions, data | **Lato** | 300–700 |
| Logo lettering only | **Freefrm721 BT** | Reserved for logo artwork alone — never used as running type |

The 2017 manual confirms the same four roles: Freefrm721 BT *"used only in Logo and nowhere else"*, Kurale as the tagline/heading face, Asap as the generic body face in four weights, Lato as the secondary face in eighteen weights *"where a slick and different look is required."* `2017 p.06, p.07`

### KTAHV sub-brand display voice `KTAHV 04`

**Gelasio** (for **Gandhi Serif**) **+ Roboto.**

The 2026 manual pairs each sub-brand with its own display voice, mapping the original face to a free-licence Google font where the original is not freely licensed. For KTAHV the display face is **Gelasio**, substituting for Gandhi Serif, and the supporting face is **Roboto**.

**The 2017 manual confirms the original pairing directly** `2017 p.39`:

> *"Kairali's Healing Village secondary font is **Roboto**, used for body text. This font easily available on web. Kairali Secondary heading font is **Gandhi Serif** which is used in all creatives. **These fonts are used only for healing village creatives.**"*

Two things this closes and one it does not:

- **Closed:** Gandhi Serif is a *heading* face and Roboto a *body* face — the 2026 entry does not say which is which. Gelasio therefore substitutes in the **heading** role.
- **Closed:** the pairing is **exclusive to KTAHV**. The 2017 manual states this in terms. No other door may use it.
- **Open:** the identity, foundry and licence of "Gandhi Serif" itself. `NONE` — see Outstanding values.

> **Sister-door reference, for boundary purposes only.** The 2017 manual assigns Ayurvedic Centre a different secondary pairing — **Yesava One** (headings) + **Open Sans** (body) `2017 p.35`. Never apply it to KTAHV.

### Published specimens `OK 04:specimen`

The manual's own Lato specimen is directly KTAHV content:

> **AYURVEDIC HEALING VILLAGE · PALAKKAD** and **1908 — 2026**

| Element | Face | Example given |
| --- | --- | --- |
| Display (h1–h3) | Kurale 400 | *"Health through ayurveda"* |
| Body / UI (h4+) | Asap 400–700 | *"Our treatments follow protocols refined over four generations."* |
| Caption / data | Lato 300–700 | *"AYURVEDIC HEALING VILLAGE · PALAKKAD"* / *"1908 — 2026"* |

### System fallbacks `OK 08:Email`

Georgia for Kurale · Trebuchet MS for Asap.

### House style `OK 11:We say`

Title Case for headings · sentence case for body · botanical names in *italic* · the tagline always lowercase.

`NONE`: type scale in px · line-heights · letter-spacing · webfont files and URLs · Freefrm721 BT licensing status. Only **floors** are published: slide titles ≥36 px, slide body ≥24 px, video captions ≥28 px, leaf headlines ≥24 px, bronze overlines ≥14 px bold.

---

## Photography & texture

**Professional photography only.** Warm, human, real. `OK 05:body`

Three sanctioned treatments — **no others** `OK 05:body, 05:captions` `2017 p.21`:

| Treatment | Subjects as published | Notes |
| --- | --- | --- |
| Natural warm colour | Treatments, facility, herbs | The manual's own specimen shows an Ayurvedic treatment being administered — **directly KTAHV subject matter** |
| Black & white | Portraits, editorial | — |
| Heritage marigold overlay | Supporting backgrounds only | Multiply blend, reduced opacity |

Overlay opacity percentage: `WAIT`. The 2017 manual describes the same technique — *"Black & White image, Yellow Overlay"* and *"Colour image, Yellow Overlay multiplied and opacity reduced"* — and names it **"Kairali Colour Photo Treatment."** `2017 p.21` That published name is not carried in the 2026 edition; use it only internally.

> **`CLASH` — may amateur photography be used?** The 2026 edition states **"professional photography only."** The 2017 manual states: *"Photos should always be professional and of high quality. **Amateur photos can be used for publications, such as news, blogs etc.** It could be Black & White."* `2017 p.20` The 2026 rule is later and unqualified. **Follow 2026 — professional only.** Recorded so the 2017 carve-out is not reintroduced.

### Textures `OK 05:caption` `2017 p.41`

Paper and weave textures ground print and hero moments — **always subtle**. The 2017 manual publishes the paper texture explicitly and permits it *"in yellow or green shades"*, showing a Paper Texture Green Overlay `2017 p.41`.

### Heritage engraving `OK 05:caption`

Used for anniversary and provenance storytelling — directly relevant to KTAHV's "since 1908" positioning.

**The 2017 manual names this asset: the "Maharishi image"** `2017 p.42` — an oval engraving of physicians administering a treatment on a *droni*. It is published in two forms: line art, and the same art on a sepia paper ground.

### Other published design elements `2017 p.42`

Three further brand elements are published in 2017 and not restated in 2026. Use with confirmation:

- a **cartouche / quatrefoil shape** used as a containing frame for the logo on a leaf-green ground;
- the **leaf used as a pattern**;
- a two-leaf **graphic of leaves** mark.

All are to be rendered *"in Primary color."*

**AI-generated imagery is not sanctioned.** Neither manual contains an AI-image policy, and *"professional photography only"* is a positive requirement. Never present generated or stock imagery as brand-compliant. `NONE 05`

**Patient imagery.** Neither manual publishes a consent, anonymisation or clinical-photography policy. For a NABH-accredited facility this is a legal requirement, not a design preference. `NONE` — escalate to the facility's medical administration, not to the brand owner.

---

## Family position

**One family, five doors.** Four businesses share the icon and lettering; only the Kurale descriptor changes — **bronze on light grounds, marigold on dark**. The fifth, Villa Raag, carries its own mark under the group's endorsement. `OK 06`

| Door | Domain | Descriptor as published | Ground | Role |
| --- | --- | --- | --- | --- |
| Ayurvedic Group | kairali.com | the parent brand | Light | Parent |
| Ayurvedic Products | kairaliproducts.com | oils, teas, medicines | Light | Shared identity |
| Ayurvedic Centre | kairalicentres.com | 18 centres, 9 countries | Light | Shared identity |
| **The Ayurvedic Healing Village** | **ayurvedichealingvillage.com** `2017` | NABH-accredited hospital-retreat — Palakkad, Kerala | **Dark forest green** | **Shared identity — this door** |
| Villa Raag | villaraag.com | the coastal sanctuary — Agonda Beach, South Goa | — | Endorsed brand, own manual |

> **Gap closed.** The 2026 manual publishes a domain for every door **except** KTAHV. The 2017 manual publishes **www.ayurvedichealingvillage.com** on the Healing Village letterhead, envelope and every card back in the group `2017 p.27, p.32, p.36, p.40`. This is heritage-sourced — confirm the domain is still live and still the intended public URL before building against it.

The 2017 manual also records the division structure the doors sat in: **Kairali Hospitality** (the Healing Village), **Kairali Manufacturing** (Ayurvedic Products), **Kairali Ayurvedic Centres** `2017 p.27`. The 2026 edition does not use these division names. Do not put them on customer-facing material without a ruling.

### The boundary with Villa Raag `OK 06, 11`

The manual publishes a **mutual** boundary. It binds both ways.

- **KTAHV** is clinical and physician-led. It never reads as leisure.
- **Villa Raag** is restorative and leisure-led, governed by its own manual.

Villa Raag content must never use *patient, physician, cure*, or *treatment* in reference to its own programmes. KTAHV content must never use *spa, resort, holiday, getaway, escape*.

**Villa Raag must never be presented as one of the four shared-identity doors.**

### Boundaries with the other doors

No equivalent register boundary is published between KTAHV and Ayurvedic Products or Ayurvedic Centre. `NONE 06`. Do not invent one. Note in particular that **the KTAHV compliance rule is scoped to KTAHV surfaces** and does not extend to kairaliproducts.com or kairalicentres.com.

---

## Foundations

*Chapter 07 — the interface layer, new in the 2026 edition. Applies to KTAHV in full. The 2017 manual has no digital chapter; nothing in this section may be sourced from it.*

The brand ships as a coded design system: tokens, webfonts and **fifteen** interface components. Stated rules: **soft corners, pill actions, warm shadows, calm motion.** `OK 07`

### Rhythm `OK 07:Rhythm`

| Property | Value |
| --- | --- |
| Spacing base | 4 px |
| Control heights | 32 / 40 / 48 px |
| Radii | 6 / 10 / 16 / 24 px, plus pill |
| Content (prose) measure | 720 px |
| Layout container | 1120 px |

### Actions `OK 07:Actions`

- Radius: **pill**. Label type: Asap semibold.
- Hover: *"**hover deepens one ramp step — never lifts.**"* **Verbatim.** The manual does not define "lifts" — do not restate any reading of it as a published rule.
- Published examples: **"Book a consultation"** (filled), **"View treatments"** (outline).
- Button padding: `NONE`.

> **Note for this door.** Both published button labels are consultation-flavoured — which is to say, both are KTAHV-shaped. They are usable here verbatim, and are the closest thing the manual gives to sanctioned KTAHV action copy.

**Dependency:** executing "one ramp step" requires ramp values that are `WAIT`. A hover state cannot be built until the ramp is supplied.

### Surfaces `OK 07:Surfaces`

White cards on ivory · **16 px** radius · warm-tinted shadow plus a hairline border.

Shadow token values (offset, blur, spread, colour): `WAIT`. Hairline border width and colour: `WAIT`.

> **The manual's card specimen is KTAHV content.** It shows an overline **SIGNATURE TREATMENT** above a Kurale title, **"Shirodhara."** Both the card specification and its example content apply to this door directly.

### Motion and focus `OK 07, 10`

- Gentle **ease-out** fades, **150–400 ms**. `ease-out` is a CSS keyword, so directly implementable; no custom curve is published.
- Nothing bounces.
- A **leaf-green focus ring on every control**. Ring width: `NONE`.
- Honour `prefers-reduced-motion` — fades become instant.

### The fifteen components `OK 07:footnote`

Button · IconButton · Input · Select · Checkbox · Radio · Switch · Card · Badge · Tag · Tabs · Dialog · Toast · Tooltip · LogoLockup

Live specimens are held in the design-system library, outside the manual. Per-component anatomy, states and props are `NONE` here.

> **Critical for this door.** These fifteen are the complete published set. A hospital-retreat surface normally needs components that are **not** in it: appointment or consultation booking calendar, date-range picker, physician profile card, programme comparison table, intake or medical-history form, condition filter, secure patient portal, document upload. `NONE 07`.
>
> Badge and Tag exist but have no published anatomy, so they cannot be assumed to serve as availability or condition indicators. Build these only against a brand-owner brief, and do not present them as manual-compliant.

`NONE`: grid gutter · responsive breakpoints · z-index scale · component anatomy and states · elevation scale · **icon library**.

**There is no iconography chapter in either manual and no icon style is published.** The only icon rules that exist are: IconButton is a component `07` · the icon watermark sits at ≤8% opacity `08` · the favicon uses the icon alone at 70% of the tile `08` · Leaf 500 may be used for icons `10` · icons never carry meaning alone `10`. Any broader icon style rule is fabrication.

---

## Channels

*Chapter 08. Websites, apps, social, email, video and slides all draw from the same tokens.* `OK 08`

> **KTAHV addendum, published verbatim** `KTAHV 08`: *"KTAHV surfaces additionally follow the clinical register."*
>
> This is an explicit, KTAHV-only addition on top of every rule in this section. It means the Voice section is not merely a copy guideline for this door — it is a channel requirement. Every surface below inherits it.

### Favicon and app icons `OK 08`

The icon alone — **never the full lockup**. Centred at **70% of the tile**. Grounds: forest `#004226` (see Decision 2) or ivory `#F7F4EA`. Export at 16 / 32 / 180 / 512 px. No effects, borders or gradients.

### Social media `OK 08`

Avatar: icon on a white or ivory circle. Post formats 1:1 and 4:5; stories 9:16. The logo sits in a corner with full clear space, or closes the post as an end frame. **One marigold accent per post.** Photography follows the Photography section.

*"Sub-brand accounts use their own descriptor lockup."* **Verbatim.** `OK 08`

> **Reading, not manual wording.** If KTAHV operates its own account, its descriptor lockup is the **"The Ayurvedic Healing Village"** Kurale line, in place of the master tagline. The manual states the rule in the single sentence quoted; this application of it to KTAHV is this document's, not additional manual text.

### Websites and apps `OK 08`

12-column grid · 1120 px container · 720 px prose measure · header 64 px on ivory with the horizontal lockup at 34–40 px · footers on forest-700 (`WAIT`) or ink (`WAIT`) with an inverted wordmark. Foundations components and the Accessibility rules apply to every screen.

**Plus the KTAHV clinical-register addendum above.**

### Email `OK 08`

Single **600 px** column on white · lockup at **44 px** height in the header · system fallbacks Georgia / Trebuchet MS · forest-coloured links · pill buttons implemented as bulletproof VML/table buttons · signatures: name in Asap semibold, role and contacts in Lato, logo at **36 px** · **no promotional banners**.

### Motion and video `OK 08`

Logo enters by a fade with a scale settle from **102% to 100%, over 400 ms ease-out** — never spins, bounces, or draws on. Lower thirds: forest bar, name in Kurale, role in Asap. Captions: Asap, **≥28 px at 1080p**. End card: ivory ground, centred lockup, tagline. Sound and pacing stay calm.

### Presentations and share images `OK 08`

16:9 slides · titles Kurale **≥36 px** · body Asap **≥24 px** · ivory or white grounds · **one** forest section divider per chapter · icon watermark at **≤8% opacity**. Link/OG images 1200 × 630 px, showing the lockup plus one Kurale line, on an ivory ground or a sanctioned photograph.

### Dark surfaces `OK 08`

Forest-700/800 (`WAIT`) or ink (`WAIT`) grounds only. The wordmark inverts to **white**. Descriptors and accents use **marigold-300** (`WAIT`). Body text is **ivory at 90% opacity**. **Leaf green is never used for text on dark grounds.**

> KTAHV's own card is a dark surface. Every value it needs — the ground, the descriptor colour — is currently `WAIT`. This door is more blocked by the missing ramp than any other.

---

## Stationery and applications

*Chapter 09. Specifications carry over unchanged from 2017 — the two editions agree line for line.* `OK 09` `2017 p.40`

| Item | Stock | Weight | Size |
| --- | --- | --- | --- |
| Visiting card — senior | Cordenons So Wool Ivory | 250 gsm | 9 × 5.5 cm |
| Visiting card — executive | Laid Natural | 250 gsm | 9 × 5.5 cm |
| Letterhead | Cordenons Natural Evolution Ivory | 120 gsm | A4 · 21 × 29.7 cm |
| Envelope | Cordenons Natural Evolution Ivory | 145 gsm | open 25.6 × 24 cm · closed 22 × 10.8 cm |
| Basic paper | Deo Matte | 300 gsm | — |

All stationery text is set in **Asap**. Card backs list the group's businesses in the standard arrangement — now **five**, ending with Villa Raag. `OK 09`

**Only personal details change between individual cards.** The layout, logo and materials never do. `OK 09` `2017 p.40`

The 2017 manual publishes two KTAHV card variants — *"Visiting Card for Healing Village"* and *"Visiting Card for Executive"* — differing in which address block appears, and a letterhead carrying the Kairali Ayurvedic Health Resorts Pvt. Ltd. entity line `2017 p.40`.

### Sanctioned finishes `OK 09` `2017 p.14–17`

Spot UV · blind embossing · wooden embossing · gold foiling · laser cutting · frosted vinyl (etched-glass effect) · **3D signage on forest green or dark wood** · jute printing · fabric printing · ceramic transfer.

The 2017 manual publishes worked examples of every one of these, plus **tags** and **hanging signage** `2017 p.14–17`. Its ceramic example is a tea cup; its jute example is a bag.

### Single colour `OK 09`

Forest green, ink, or blind and foil finishes only. **Never partial recolouring.**

### Partner and supplier logos `OK 09` `2017 p.19`

Two arrangements: **horizontal** (Kairali left, hairline divider, partner right) and **vertical** (Kairali above, divider, partner below). The partner mark **never exceeds the visual weight** of the Kairali logo. Both keep the full K-width clear space.

`NONE`: facility signage drawings · wayfinding system · room and treatment-room signage · uniform and linen specification · embossing depth · foil specifications · laser-cut dimensions · ceramic transfer templates · print source files.

> For a physical hospital-retreat, **wayfinding and facility signage is the largest production gap.** Neither edition publishes a system. The 3D signage examples are logo applications, not a wayfinding standard. Escalate rather than extrapolate.

---

## Accessibility and production

**Digital standard: WCAG 2.2 AA** `OK 10`

### Contrast pairings `OK 10:table`

| Colour on white | Ratio | WCAG 2.2 | Permitted use | Restriction |
| --- | --- | --- | --- | --- |
| Forest 500 | 7.7 : 1 | AA + AAA | Body text, actions, links | Unrestricted |
| Ink on ivory | 15.6 : 1 | AA + AAA | Primary text | Unrestricted — *but ink has no published value* |
| Leaf 500 | 3.0 : 1 | Large text / UI | Headlines ≥24 px, icons, focus rings | Body text uses Leaf 700 (`WAIT`) |
| Bronze 400 | 3.1 : 1 | Large text / UI | Overlines ≥14 px bold, taglines | Body text uses Bronze 600 (`WAIT`) |
| Marigold 400 | 1.9 : 1 | Decorative | Decorative only | **Never text on white.** Ink on marigold passes at 8.3 : 1 |

### Digital standards `OK 10`

- Touch targets **≥44 px**
- A visible **leaf-green focus indicator** on every control
- Honour `prefers-reduced-motion` — fades become instant
- Form fields **always** labelled
- **Icons never carry meaning alone**

All five bind this door directly: a consultation booking form must be fully labelled; a condition or programme filter must meet 44 px; a clinical availability state cannot be conveyed by an icon alone.

### Print production `OK 10`

Anchors print as PMS spot inks — **7495 · 349 · 7409 · 7510** — or as the CMYK builds above · ramp steps are screen-first, so convert to CMYK per job · **3 mm bleed** on all trimmed pieces · logo minimums **2.5 cm** and **1.5 cm** (but see the Decision 3 clash on what 1.5 cm measures).

`NONE`: ARIA patterns · alt-text rules · screen-reader guidance · keyboard navigation order · focus-ring width · accessibility test matrix · plain-language or health-literacy standard.

> **Health-literacy note, not a manual rule.** A hospital-retreat's public surfaces carry clinical information to patients who may be unwell, elderly or reading in a second language. Neither edition publishes a reading-level or plain-language standard. WCAG 2.2 AA does not supply one either. Raise it — do not invent one.

---

## Voice

### Master voice `OK 11`

Kairali speaks as a family with **four generations of practice** — **warm, precise, unhurried.** We say *"our"* and address *"you."* We never shout.

| We say | We never |
| --- | --- |
| "Treatment," not "service" | Use emoji |
| "Since 1908" — often | Exclaim in headings |
| Title Case for headings, sentence case for body | Promise cures |
| Botanical names in italic | Use spa-cliché superlatives |
| The tagline always lowercase | Sound clinical or transactional |

### The KTAHV register — COMPLIANCE RULE `KTAHV 11`

*The manual labels this box **COMPLIANCE RULE**, not a style preference. Reproduced here in full, as the manual states it:*

> KTAHV is an NABH-accredited Ayurvedic medical facility — a hospital-retreat. Its copy reads **clinical and physician-led, never as leisure**: **patient, physician, treatment, programme, Panchakarma, consultation.** Never *spa, resort, holiday, getaway,* or *escape*. **No claims of cure** — name the conditions addressed and the programmes offered. **Specificity over superlatives:** years, credentials, named conditions, real outcomes. Banned filler everywhere: *bespoke, curated, discerning, unparalleled, nestled, indulge, pamper, exquisite, world-class, unique.*

> **The nuance that must be preserved.** The master voice (above) says the group should never *"sound clinical or transactional."* The KTAHV compliance rule is an **explicit, documented exception** to that instruction — for this facility, clinical and physician-led language is **required**, not avoided.
>
> Follow the KTAHV rule for all KTAHV copy. Follow the master rule for general Kairali Group communications that are not KTAHV-specific. **The banned-filler list and the no-cure rule apply under both registers, without exception.**
>
> The "transactional" half of the master rule is not overridden. KTAHV copy is clinical, but never brisk, procedural or administrative in tone.

### Approved vocabulary (KTAHV) `KTAHV 11`

Patient · physician · treatment · programme · Panchakarma · consultation

### Prohibited vocabulary (KTAHV) `KTAHV 11`

Spa · resort · holiday · getaway · escape — **plus** the group-wide banned filler: bespoke · curated · discerning · unparalleled · nestled · indulge · pamper · exquisite · world-class · unique

### Editorial requirements (KTAHV) `KTAHV 11`

- **Never claim a cure.** Name the conditions addressed and the programmes offered instead.
- **Prefer specificity over superlatives:** years of practice, credentials, named conditions, real — not implied — outcomes.

### Hard copy limits — these bind absolutely `OK 11`

No claims of cure · no banned filler · no emoji · no exclaiming headings · no spa-cliché superlatives.

> **Regulatory note, not a manual rule.** A NABH-accredited facility is subject to medical advertising and health-claim law that varies by jurisdiction — in India, the Drugs and Magic Remedies (Objectionable Advertisements) Act and NABH's own communication requirements bear directly on this door's copy. The manual's *"no claims of cure"* is a **brand** rule, not a legal review. **All KTAHV clinical copy needs qualified sign-off that this specification cannot provide.** This is the single most important escalation in this document.

### Villa Raag register — boundary only, never apply here `OK 11`

Warm, sensory, unhurried. *"Retreat"* and *"sanctuary"* are sanctioned there; KTAHV's clinical vocabulary is not. The banned-filler list applies unchanged. **The boundary runs both ways — see Family position.**

`NONE`: grammar and punctuation guides · glossary · localisation and translation policy · editorial workflow · approval process · programme naming conventions · condition-description standards · testimonial and patient-story policy.

---

# The build layer

**Everything below this line is `BRIEF`. It is not from either Brand Manual.**

A brand manual governs how the brand looks and speaks; it does not specify a website. Routes, page templates, a type scale in pixels, breakpoints and a booking data model are all absent from it — correctly, since they are not brand decisions. A builder still needs them.

**Three properties hold for everything below:**

1. It never contradicts a manual rule. Every proposal cites the published constraints that bound it.
2. It is derived from published constraints wherever possible — the 4 px base, the 720 px measure, the 1120 px container, and the published minimum type sizes.
3. **It carries no authority.** Sign-off converts a `BRIEF` value to a rule; until then it is provisional.

## Published constraints this section must respect

| Constraint | Value | Source |
| --- | --- | --- |
| Spacing base | 4 px — all spacing is a multiple | `OK 07` |
| Content measure | 720 px | `OK 07, 08` |
| Layout container | 1120 px | `OK 07, 08` |
| Grid | 12-column | `OK 08` |
| Header height | 64 px on ivory | `OK 08` |
| Header lockup | 34–40 px | `OK 08` |
| Control heights | 32 / 40 / 48 px | `OK 07` |
| Radii | 6 / 10 / 16 / 24 px + pill | `OK 07` |
| Card radius | 16 px | `OK 07` |
| Touch target floor | ≥ 44 px | `OK 10` |
| Leaf headline floor | ≥ 24 px | `OK 10` |
| Bronze overline floor | ≥ 14 px bold | `OK 10` |
| Motion | ease-out, 150–400 ms | `OK 07` |
| Register | Clinical and physician-led on every surface | `KTAHV 08, 11` |

## Type scale `BRIEF`

The manuals publish **floors, not a scale**. This proposal sits on a 4 px grid and respects every floor.

| Token | Size / line-height | Face | Respects |
| --- | --- | --- | --- |
| `--t-display` | 48 / 56 px | Kurale 400 | — |
| `--t-h1` | 36 / 44 px | Kurale 400 | slide title floor 36 px |
| `--t-h2` | 28 / 36 px | Kurale 400 | leaf headline floor 24 px |
| `--t-h3` | 24 / 32 px | Kurale 400 | leaf headline floor 24 px |
| `--t-h4` | 20 / 28 px | Asap 600 | — |
| `--t-body` | 16 / 24 px | Asap 400 | — |
| `--t-small` | 14 / 20 px | Lato 400 | — |
| `--t-overline` | 14 / 20 px, +0.08em, uppercase | Lato 700 | bronze overline floor 14 px bold |

## Breakpoints `BRIEF`

`sm 640` · `md 768` · `lg 1024` · `xl 1120` — `xl` is set to the **published** container width rather than a conventional 1280, so the container never needs a max-width override.

## Spacing scale `BRIEF`

4 · 8 · 12 · 16 · 24 · 32 · 48 · 64 · 96 px — every step a multiple of the published 4 px base.

## Routes `BRIEF`

`/` · `/about` (since 1908, four generations) · `/treatments` · `/treatments/[slug]` · `/programmes` · `/programmes/[slug]` · `/conditions` · `/conditions/[slug]` · `/physicians` · `/facility` · `/consultation` (booking) · `/contact` · `/legal/*`

*Named `/consultation`, not `/book` or `/reserve` — the published button label is "Book a consultation" `OK 07`, and reservation vocabulary edges toward the prohibited leisure register.*

## Page templates `BRIEF`

Home · Treatment detail · Programme detail · Condition detail · Physician profile · Facility · Consultation request · Editorial / article · Legal.

Every template: ivory ground, 1120 px container, 720 px prose measure, white cards at 16 px radius, one marigold accent per view, forest for all actions and links.

## Consultation data model `BRIEF`

`Programme { slug, name, duration, conditions[], summary, protocol[] }`
`Condition { slug, name, description, programmes[] }`
`Physician { slug, name, qualifications[], years, specialisms[] }`
`ConsultationRequest { name, email, phone, condition, programme?, preferredDates, notes, consent }`

**No field in this model may carry an outcome, success rate or recovery estimate.** No published claim supports one.

## Build order `BRIEF`

1. Tokens (published values only) + `tokens.provisional.css`
2. Type scale and layout primitives
3. The fifteen published components
4. Templates against real copy written in the clinical register
5. Consultation flow — with legal sign-off on every clinical string
6. Ramp values arrive → delete `tokens.provisional.css` → dark surfaces and hover states ship

---

## What still cannot be built without a ruling

| Blocker | Effect | Resolution |
| --- | --- | --- |
| 6 colour values `WAIT` | Footer, dark surfaces and **KTAHV's own descriptor** are magenta | Decision 1 + ramp values |
| Logo artwork `NONE` | No lockup asset for any surface | Request files |
| Minimum-size semantics `CLASH` | Small-format artwork may be set wrong | Decision 3 |
| Facility signage `NONE` | No wayfinding for a physical site | Decision 6 |
| Clinical copy legal review | Every treatment and condition page | External counsel |

Everything else on the site can be built now.

## Open decisions

Six places where the published record says two things that do not agree, or leaves this door without something it needs. **Choose neither side** — a ruling becomes precedence level 1.

### 1 · What is `marigold-300`?

| The manual says | Dark-surface descriptors and accents use marigold-300. `08` |
| --- | --- |
| And also says | The ramps are published only as gradient images; no step value exists in writing. `03` |
| What we need | The hex for marigold-300 — and, with it, forest-700, forest-800, leaf-700, bronze-600. |
| This blocks | KTAHV's own card, every dark surface, every footer, every hover state. **The highest-impact open question for this door**, because KTAHV is the only door whose primary treatment is a dark ground. |
| Ruling | *pending* |

### 2 · Which forest green for app icons?

| The manual says | The Forest anchor is `#006038`, PMS 349 — the print reference and the interactive colour. `03`, `01`, `2017 p.10` |
| --- | --- |
| And also says | The favicon and app-icon tile ground is "forest `#004226`." `08` |
| What we need | Is `#004226` a distinct production value for tiles, or a ramp step — forest-700 or 800 — that should be named as one? |
| This blocks | Favicon and app-icon production. A ruling may also resolve two dark-surface values. |
| Ruling | *pending* |

### 3 · What does the 1.5 cm minimum measure?

| The manual says | Minimum size without tagline: 1.5 cm — with a specimen showing **icon + wordmark, tagline removed**. `2017 p.05` |
| --- | --- |
| And also says | The 2026 edition pairs 1.5 cm print with 40 px screen, which derivative specs have read as **icon alone**. `02` |
| What we need | Confirmation of which mark the 1.5 cm / 40 px floor governs — and, if it is the icon alone, the separate floor for the wordmark-without-tagline. |
| This blocks | Small-format print, favicons above 40 px, embossed and foiled items, tags. |
| Ruling | *pending* |

### 4 · Is `#a0b65e` retired or unnamed?

| The manual says | 2017 publishes a second secondary green, `#a0b65e`, C39 M64 Y89 K36, R160 G182 B94 — and assigns it PMS 7495 C, the same number as the primary leaf. `2017 p.10` |
| --- | --- |
| And also says | The 2026 edition lists four anchors and two semantics. `#a0b65e` appears nowhere. `03` |
| What we need | Is it retired, or does it survive unnamed as a ramp step? And which of the two 7495 C assignments is the misprint? |
| This blocks | Nothing immediately, but it is a live risk: legacy KTAHV collateral may carry it, and a spot-ink print job could be specified against the wrong PMS. |
| Ruling | *pending* |

### 5 · How is a treatment photographed at this facility?

| The manual says | Professional photography only, in three sanctioned treatments; the natural-colour specimen shows an Ayurvedic treatment being administered. `05` |
| --- | --- |
| And also says | Nothing about consent, anonymisation, clinical accuracy, or whether the person shown may be a patient rather than a model. `05` |
| What we need | A written photography protocol for a NABH-accredited facility, agreed with medical administration — not the brand owner alone. |
| This blocks | All facility, treatment and physician imagery. |
| Ruling | *pending* |

### 6 · What is the facility signage and wayfinding system?

| The manual says | Sanctioned finishes include 3D signage on forest green or dark wood, and hanging signage. `09`, `2017 p.15–17` |
| --- | --- |
| And also says | Nothing about wayfinding: no sign hierarchy, no room or treatment-room naming, no directional standard, no multilingual policy, no statutory or accessibility signage. `09` |
| What we need | A wayfinding standard, or written confirmation that the logo-application finishes are all that governs. |
| This blocks | The physical site — the primary expression of this door. |
| Ruling | *pending* |

## Outstanding values

Values the manual requires but does not publish. These need **retrieving or supplying**, not deciding — most already exist in the design-system library.

| Priority | Item | This blocks |
| --- | --- | --- |
| P1 | `marigold-300` | KTAHV's own descriptor on its own card |
| P1 | `forest-700`, `forest-800`, `leaf-700`, `bronze-600` | Any footer, any dark surface, body text in leaf or bronze |
| P1 | `--kg-ink` | Footers, dark surfaces, single-colour print, the 15.6 : 1 pairing |
| P1 | Logo artwork files — SVG / EPS / AI / PNG | Every surface. Nothing ships without these. |
| P2 | All 50 ramp step values | Any hover state, any systematic tint or shade |
| P2 | Gandhi Serif identity, foundry and licence | Confirming Gelasio is the correct substitute |
| P2 | Warm-tinted shadow — offset, blur, spread, colour; hairline border width | Card components |
| P2 | Type scale in px and line-height for h1–h6, body, caption | Any screen at production fidelity |
| P2 | Responsive breakpoints; 12-column grid gutter | Responsive implementation |
| P2 | Component specimens, states and anatomy — in the library | A faithful component build |
| P2 | Webfont files and URLs; icon library — in the library | Web build |
| P3 | Confirmation that ayurvedichealingvillage.com is still the intended public domain | The whole web presence — currently heritage-sourced |
| P3 | Logo-on-panel and marigold-overlay opacity percentages | Photographic overlays, logo-on-panel placements |
| P3 | Freefrm721 BT licensing status and any digital substitute | Logo handling in digital production |
| P3 | Whether the 2017 division name "Kairali Hospitality" is still current | Corporate and stationery copy |

### Absent for this door in particular

Not gaps in a value, but whole areas neither manual covers for a NABH-accredited hospital-retreat. All `NONE` — **escalate, never extrapolate.**

| Area | What is missing |
| --- | --- |
| Clinical components | Booking calendar, date-range picker, physician profile, programme comparison, intake form, condition filter, patient portal, document upload |
| Facility | Wayfinding, sign hierarchy, room and treatment-room signage, statutory signage, uniform and linen |
| Clinical communication | Condition-description standards, programme naming, testimonial and patient-story policy, consent and anonymisation |
| Health literacy | Reading level, plain-language standard, multilingual policy |
| Regulatory | Medical advertising compliance, NABH communication requirements, disclaimer placement |
| Semantic colour | Success and warning states |

## Production checklist

**Identity**

- [ ] Official artwork used, unaltered — **never regenerated** (no files are published)
- [ ] K-width clear space preserved; tagline gap = horizontal "I"
- [ ] Minimum size met: 2.5 cm / 1.5 cm print, 72 px / 40 px screen — against the Decision 3 ruling
- [ ] Descriptor reads **"The Ayurvedic Healing Village"**, in marigold on the dark ground
- [ ] No rotation outside 0° / 90°, no distortion, no added effects

**Colour**

- [ ] Only published values used; every `WAIT` token left empty and reported
- [ ] Forest carries actions and links; Leaf identifies
- [ ] Marigold is accent only — never body text, once per view
- [ ] Error and information colours used semantically only
- [ ] `#a0b65e` not used pending Decision 4
- [ ] No 2017 colourway reintroduced (no red or indigo logo grounds)

**Typography**

- [ ] Kurale Regular only, **never bold**
- [ ] Botanical names in italic
- [ ] Freefrm721 BT confined to logo artwork
- [ ] Gelasio (heading) + Roboto (body) used only where a distinct KTAHV display voice is called for — and nowhere outside this door

**Photography**

- [ ] Professional photography only; **no AI-generated or stock imagery**
- [ ] Only the three sanctioned treatments used
- [ ] Patient consent and anonymisation cleared with medical administration (Decision 5)

**Voice**

- [ ] Copy written in the **clinical register** — patient, physician, treatment, programme, Panchakarma, consultation
- [ ] **No leisure vocabulary** — no spa, resort, holiday, getaway, escape
- [ ] **No claim of cure**, express or implied; conditions and programmes named specifically
- [ ] No banned filler; no emoji; no exclaiming headings
- [ ] Not brisk or administrative — clinical, but still warm and unhurried
- [ ] **Clinical claims reviewed by qualified counsel**

**Digital**

- [ ] Components taken from the shared library, not recreated
- [ ] Touch targets ≥44 px; visible focus; `prefers-reduced-motion` honoured
- [ ] Form fields labelled; icons never carry meaning alone
- [ ] Clinical-register addendum applied to every surface, not just marketing pages
- [ ] Clinical components flagged as outside the published set

**Before shipping**

- [ ] Every `WAIT` token listed for the brand owner
- [ ] Every `2017`-sourced value flagged as heritage-sourced
- [ ] All six decisions ruled, or the artefact labelled provisional

## Governance

The **Kairali Ayurvedic Group Brand Manual, 2026 Edition, rev. 2** (chapters 01–11) is the sole authority. The **2017 edition** is a superseded document used here only to close gaps, and never in the six areas the 2026 edition explicitly changed. This document is derived from both. It adds no rules and resolves no ambiguity on its own account — with one exception, recorded openly: the `#8d9c34` / `#26265F` indigo label, where the 2017 manual's own RGB build settles its own hex typo.

Brand-owner approval is required to change: logo artwork and construction · colour anchors and semantic assignments · the typeface mapping including the Gelasio + Roboto pairing · minimum sizes and clear space · sanctioned production finishes · **the KTAHV voice compliance rule** · the KTAHV descriptor and card · any item in the decisions or outstanding-values registers.

Review on any manual revision, or on any ruling recorded above.

---

*"Health through ayurveda — a promise kept daily since 1908."* — Kairali Ayurvedic Group

`kairali-ktahv-design-md · v3.0.0 · 2026-07-31`
