# Quiet Warm — Style Guide

A minimal, intentional, cozy design system for AI models to follow when producing UI, documents, or visuals.
Light theme. Three accents only: **red, green, yellow**.

Inspired by the light theme of Primary for Obsidian: warm paper-cream surfaces, deep brown ink, soft shapes, and a little play inside serious work.

## How to use this guide (for the AI)

1. Read **Quick Reference** first. If it is all you have, it is enough.
2. Use the variables in **Appendix: Tokens**. Never invent hex values.
3. Read the numbered sections only when the task touches that area.
4. Run **Review Checklist** before you deliver.

## Contents

| Section | Answers |
|---|---|
| Quick Reference | What are the rules in one page? |
| 1. Philosophy | Why does it look this way? |
| 2. Color | Which colors, and where? |
| 3. Typography | Which fonts, sizes, weights? |
| 4. Spacing and Layout | How is space organized? |
| 5. Shape and Elevation | Corners, borders, shadows? |
| 6. Motion | How does it move? |
| 7. Components | How do buttons, inputs, and so on look? |
| 8. Voice | How does the copy sound? |
| 9. Review Checklist | Is it done and correct? |
| Appendix: Tokens | The actual CSS values |

**Precedence.** When sections disagree: Tokens > Color > any component rule. When a rule is missing, return to Philosophy and choose the quieter option.

---

## Quick Reference

Paste this section alone into a system prompt if you need the short version.

You design in the **Quiet Warm** style: minimal, intentional, cozy, light theme.

**Surfaces.** Warm cream, never pure white. Page `#F8F4EE`, raised `#FCFAF6` for cards, `#EEE7DD` for sunken areas. Text is deep brown `#3F2E1C`, secondary `#83796D`. Never use pure black or pure white.

**Accents.** Exactly three: red `#DF483D`, green `#72CEA6`, yellow `#EBB421`. Yellow is the primary accent (focus, selection, active, primary action). Green means done, success, growth. Red means danger, error, emphasis that needs attention. Everything else is neutral. No blue, no purple, no gradients.

**Rule of three.** At most one accent dominates a screen. Accents cover under 10% of the surface. If in doubt, remove the color.

**Type.** One sans family. Four sizes in regular use. Weights 400 and 600 only. Generous line height (1.6 body).

**Space.** 4px base unit. Be generous. Group by proximity, not by lines or boxes.

**Shape.** Soft corners (10px default, 999px for pills). 1px warm borders. Shadows are faint and warm, used rarely.

**Motion.** Gentle and quick: 120 / 200 / 320 ms, ease-out. Only `opacity` and `transform`. A small lift on hover, a small settle on press. Nothing loops, bounces for long, or demands attention. Respect `prefers-reduced-motion`.

**Voice.** Plain, warm, short. No exclamation marks, no jargon.

**Decide by subtraction.** Remove before you add. Ask: what is the quietest version that still works?

---

## 1. Philosophy

### The feeling
Soft, calm, comforting. Like a warm desk lamp over paper. Serious work with a small amount of play.

### Four principles

#### 1. Minimal
Every element must earn its place. If removing it changes nothing, remove it. Prefer space over lines, and lines over boxes.

#### 2. Intentional
Every choice has a reason you can state in one sentence. No decoration for its own sake. A color, a shadow, or a motion exists because it tells the user something.

#### 3. Cozy
Warm neutrals, rounded shapes, unhurried motion. Nothing sharp, glaring, or sudden. Contrast is comfortable, not harsh.

#### 4. Playful, but quiet
Play lives in small moments: a checkbox that settles, a button that lifts a pixel, a yellow highlight. Never in noise, mascots, or constant movement.

### Decision rules

1. **Subtract first.** Try the version with less before adding anything.
2. **Neutral by default.** Color is a signal, not a theme. Start grayscale-brown, then add one accent only where meaning demands it.
3. **One focal point per view.** One primary action, one accent area.
4. **Meaning over ornament.** Red = attention or danger. Green = complete or good. Yellow = focus or selected. Never swap these.
5. **Consistency beats novelty.** Reuse a token before creating one.
6. **Comfort over contrast tricks.** Keep AA contrast, but avoid pure black on white.

### Anti-goals
- Glassmorphism, neon, heavy gradients, dark patterns
- Dense dashboards with borders everywhere
- Looping or attention-seeking animation
- More than three accent hues


## 2. Color

Warm neutrals do 90% of the work. Three accents do the rest.

### Neutrals (warm paper and ink)

| Token | Hex | Use |
|---|---|---|
| `--bg` | `#F8F4EE` | Page background |
| `--bg-raised` | `#FCFAF6` | Cards, popovers, inputs |
| `--bg-sunken` | `#EEE7DD` | Sidebars, wells, code blocks |
| `--bg-hover` | `#E4DCD0` | Hover and pressed fills |
| `--line` | `#E9E3DA` | Hairline borders, dividers |
| `--line-strong` | `#D7CBB9` | Input borders, emphasized edges |
| `--ink` | `#3F2E1C` | Primary text |
| `--ink-soft` | `#83796D` | Secondary text, labels |
| `--ink-faint` | `#CFC2AF` | Placeholders, disabled |

Never use `#000` or `#FFF`.

### Accents (exactly three)

| Role | Fill | Text-safe ink | Soft tint (backgrounds) |
|---|---|---|---|
| **Yellow** (primary) | `#EBB421` | `#8A6508` | `#F7E7B4` |
| **Green** (success) | `#72CEA6` | `#2F7D5C` | `#D8F0E5` |
| **Red** (danger) | `#DF483D` | `#B93A30` | `#F6D5D1` |

Soft tints and ink variants are shades of the same three hues. They do not count as extra colors.

### Meaning

- **Yellow**: focus ring, selection, active tab, primary button, highlights, progress in motion.
- **Green**: success, completed, saved, positive change.
- **Red**: error, destructive action, overdue, critical attention.

Never use an accent for pure decoration. Never mix two accents in one small component.

### Usage rules

1. Accents cover under 10% of any screen.
2. One accent dominates a view. A second may appear only if its meaning is needed.
3. **Text on accent fills is `--ink`** (dark brown), never white.
4. **Accent as text** uses the ink variant, never the fill. Yellow fill (`#EBB421`) as text on cream fails contrast.
5. Status is never color-only. Pair with an icon or a word.
6. No gradients. Flat fills only.
7. Borders stay neutral unless the state requires an accent (focus, error).

### Contrast targets
- Body text: ink on bg ≥ 7:1 (achieved).
- Secondary text: ≥ 4.5:1 for anything under 18px. If `--ink-soft` falls short on a tinted surface, use `--ink`.
- Accent text (ink variants): ≥ 4.5:1 on `--bg`.


## 3. Typography

One family, few sizes, two weights. Hierarchy comes from size and color before weight.

### Families

```
--font-sans: "Inter", ui-sans-serif, system-ui, -apple-system, "Segoe UI", sans-serif;
--font-mono: ui-monospace, "SF Mono", "JetBrains Mono", Menlo, monospace;
```

A rounded or humanist sans is welcome if provided, but never mix two sans families. Mono is only for code.

### Scale (1.25 ratio, rounded)

| Token | Size | Line height | Use |
|---|---|---|---|
| `--text-xs` | 12px | 1.5 | Captions, meta |
| `--text-sm` | 14px | 1.55 | Labels, secondary UI |
| `--text-base` | 16px | 1.6 | Body |
| `--text-lg` | 20px | 1.4 | Subheads |
| `--text-xl` | 28px | 1.25 | Titles |
| `--text-2xl` | 36px | 1.2 | Page headline (rare) |

### Weights
- **400** body and most UI.
- **600** titles, labels that need emphasis, buttons.
- No 300, no 700+, no italics for emphasis in UI. Italics only for quoted or foreign text.

### Rules
1. Body line length 55–70 characters (`max-width: 65ch`).
2. Headlines: tighter tracking (`-0.01em`). Small caps or uppercase labels: loose tracking (`0.04em`), 12px, weight 600, `--ink-soft`. Use sparingly.
3. Left-align almost everything. Center only short, single-line content.
4. Text color: `--ink` for primary, `--ink-soft` for secondary. Never lighter than `--ink-soft` for readable text.
5. Links: `--ink` with a 2px yellow underline (`text-decoration-color`), offset 3px. On hover the underline fills to a yellow highlight at 30% opacity.
6. Emphasis in running text: weight 600. Highlight (`<mark>`) uses `--yellow-soft`.
7. Numbers in tables and counters use `font-variant-numeric: tabular-nums`.


## 4. Spacing and Layout

Generous, calm, predictable.

### Scale (4px base)

| Token | Value |
|---|---|
| `--space-1` | 4px |
| `--space-2` | 8px |
| `--space-3` | 12px |
| `--space-4` | 16px |
| `--space-5` | 24px |
| `--space-6` | 32px |
| `--space-7` | 48px |
| `--space-8` | 64px |

Use only these. No arbitrary values such as 13px or 22px.

### Rules

1. **Proximity groups, lines separate only when necessary.** Related items sit 8–12px apart. Unrelated groups sit 32px or more apart.
2. Component padding: 12–16px (compact), 24px (cards), 32–48px (page sections).
3. Page gutters: 16px (mobile), 32px (tablet), 48px+ (desktop).
4. Content max-width: 680px for reading, 1040px for app layouts, 1200px absolute ceiling.
5. Prefer a single column. Add a second column only if the content is truly parallel.
6. Align to a simple grid: 4 columns (mobile), 8 (tablet), 12 (desktop), 24px gutters.
7. Vertical rhythm: section gap is at least twice the gap inside a section.
8. When it feels crowded, add space before reducing font size.

### Layout patterns

- **Reading page**: single 680px column, 64px top padding.
- **App shell**: 240px sunken sidebar (`--bg-sunken`), main area `--bg`, no heavy dividing line. A single `--line` hairline at most.
- **Card grid**: auto-fill, min 260px, 24px gap.


## 5. Shape and Elevation

Soft edges, faint depth.

### Radius

| Token | Value | Use |
|---|---|---|
| `--radius-sm` | 6px | Tags, small chips, inline code |
| `--radius-md` | 10px | Buttons, inputs, default |
| `--radius-lg` | 16px | Cards, modals |
| `--radius-pill` | 999px | Pills, toggles, badges |

Nested radii: inner = outer minus padding. Never mix sharp and round corners in one view.

### Borders
- 1px, `--line` by default. `--line-strong` for inputs and anything that must read as interactive.
- Borders are optional. Prefer a background step (`--bg` to `--bg-sunken`) over a border.
- Never use 2px+ borders, except the 2px yellow focus ring.

### Elevation
Depth is quiet and warm-tinted. Never a black shadow.

| Token | Value | Use |
|---|---|---|
| `--shadow-0` | none | Default |
| `--shadow-1` | `0 1px 2px rgba(63,46,28,.06)` | Cards at rest |
| `--shadow-2` | `0 4px 16px rgba(63,46,28,.08)` | Hover lift, popovers |
| `--shadow-3` | `0 12px 32px rgba(63,46,28,.12)` | Modals only |

Rules: at most two elevation levels visible at once. A flat surface with a hairline border is often better than a shadow.

### Icons
Outline style, 1.5px stroke, rounded caps and joins, 16 or 20px. Color is `--ink-soft`, `--ink` on hover or active. Accent color only when the icon carries a status.


## 6. Motion

Motion should feel like something settling into place on a soft surface. Easy, cozy, quick, never showy.

### Principles
1. **Quiet.** Motion confirms an action; it never performs.
2. **Short.** Most transitions finish in 200ms or less.
3. **Soft landing.** Ease-out. Things decelerate into rest.
4. **Cheap.** Animate only `opacity` and `transform`. Never width, height, top, left, or box-shadow blur on large areas.
5. **One thing at a time.** No simultaneous animations competing for attention.
6. **Nothing loops** except a loading indicator, and it is slow and subtle.

### Tokens

| Token | Value | Use |
|---|---|---|
| `--dur-fast` | 120ms | Hover, color, press |
| `--dur-base` | 200ms | Most transitions, menus |
| `--dur-slow` | 320ms | Panels, modals, page entrance |
| `--ease-out` | `cubic-bezier(0.22, 1, 0.36, 1)` | Default |
| `--ease-settle` | `cubic-bezier(0.34, 1.3, 0.64, 1)` | Tiny overshoot, only checkboxes, toggles, toasts |
| `--ease-in` | `cubic-bezier(0.4, 0, 1, 1)` | Exits only |

Exits are about 70% as long as entrances.

### The signature moves

#### Lift (hover on cards, buttons)
`translateY(-1px)` plus `--shadow-2`, 120ms, ease-out.

#### Press
`translateY(0) scale(0.98)`, 120ms. Release returns with ease-settle.

#### Rise-in (entrance)
From `opacity: 0; translateY(6px)` to rest, 320ms, ease-out. Lists stagger by 40ms per item, capped at 6 items, the rest appear together.

#### Settle (check, toggle)
Scale 0.9 to 1.0 with ease-settle, 200ms. The fill changes to green (check) or yellow (toggle on) at the same time.

#### Highlight sweep (links, selection)
Yellow underline or mark grows from left to right with `transform: scaleX`, 200ms, `transform-origin: left`.

#### Focus
A 2px yellow ring fades in over 120ms. Never animate the ring's size.

#### Loading
Three soft yellow dots fading 0.4 to 1.0 opacity, 1.2s cycle, 150ms offset. Or a thin yellow bar sliding slowly. No spinners that spin fast.

### Reference CSS

```css
:root {
  --dur-fast: 120ms; --dur-base: 200ms; --dur-slow: 320ms;
  --ease-out: cubic-bezier(0.22, 1, 0.36, 1);
  --ease-settle: cubic-bezier(0.34, 1.3, 0.64, 1);
}

.card { transition: transform var(--dur-fast) var(--ease-out), box-shadow var(--dur-fast) var(--ease-out); }
.card:hover { transform: translateY(-1px); box-shadow: var(--shadow-2); }
.btn:active { transform: scale(0.98); }

@keyframes rise-in { from { opacity: 0; transform: translateY(6px); } to { opacity: 1; transform: none; } }
.rise-in { animation: rise-in var(--dur-slow) var(--ease-out) both; }

@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { animation-duration: 1ms !important; transition-duration: 1ms !important; }
}
```

### Reduced motion
Always honor `prefers-reduced-motion`. Remove translation and scale; keep simple opacity or color changes at 1ms to 120ms.


## 7. Components

All values come from the Tokens appendix. Each component lists rest, hover, active, focus, and disabled.

### Button

| Variant | Rest | Hover | Use |
|---|---|---|---|
| **Primary** | `--yellow` fill, `--ink` text, 600 | Lift 1px, `--yellow-hover` | One per view |
| **Secondary** | `--bg-raised`, 1px `--line-strong`, `--ink` | `--bg-hover` fill | Default |
| **Quiet** | Transparent, `--ink-soft` | `--bg-hover` fill | Toolbars |
| **Danger** | `--bg-raised`, 1px `--red`, `--red-ink` text | `--red-soft` fill | Destructive |

Height 36px (default), 44px (touch). Padding 0 16px. Radius `--radius-md`. Press: scale 0.98. Focus: 2px yellow ring, 2px offset. Disabled: `--ink-faint` text, no shadow, no hover.

### Input
Fill `--bg-raised`, 1px `--line-strong`, radius `--radius-md`, height 40px, padding 0 12px. Placeholder `--ink-faint`. Focus: border `--yellow`, 2px yellow ring at 40% opacity. Error: border `--red`, message below in `--red-ink` with an icon. Label above in `--text-sm`, 600.

### Checkbox and toggle
- Checkbox: 18px, radius 6px, 1px `--line-strong`. Checked: green fill, ink tick, settle animation.
- Toggle: 36x20 pill. Off: `--bg-hover`. On: `--yellow`. Knob `--bg-raised`, settles with ease-settle.

### Card
`--bg-raised`, 1px `--line`, radius `--radius-lg`, padding 24px, `--shadow-1`. If interactive: lift on hover. No colored left borders or heavy headers.

### Tag and badge
Pill, 12px text, weight 600, padding 2px 10px. Default: `--bg-sunken` with `--ink-soft`. Status: soft tint fill with ink variant text (yellow = pending, green = done, red = overdue), and always a word or icon.

### Callout and alert
Soft tint background (`--yellow-soft` info or notice, `--green-soft` success, `--red-soft` error), radius `--radius-md`, padding 16px, icon plus text in `--ink`. No border, or a 1px border in the same hue at 40% opacity.

### Navigation
Quiet. Items `--ink-soft`, 36px high, radius `--radius-md`. Active item: `--bg-hover` fill, `--ink` text, a small 4px yellow dot or a 2px yellow bar. Never a full-width colored block.

### Tabs
Text tabs with a 2px yellow underline that slides between tabs (transform, 200ms). Inactive `--ink-soft`.

### Table
No vertical lines. 1px `--line` between rows only. Header: 12px uppercase, `--ink-soft`, 600. Row hover `--bg-sunken`. Numeric columns right-aligned, tabular figures.

### Modal and popover
`--bg-raised`, radius `--radius-lg`, `--shadow-3` (modal) or `--shadow-2` (popover). Backdrop: `rgba(63,46,28,.28)`, no blur. Enter: rise-in, 200ms. Exit: fade, 140ms.

### Toast
Bottom-center, `--bg-raised`, `--shadow-2`, radius pill or `--radius-md`. A small colored dot (green, red, or yellow) signals status. Enter with ease-settle, auto-dismiss in 4s.

### Progress
Track `--bg-hover`, 6px, pill. Fill: yellow while in progress, green when complete. Width changes use `transform: scaleX`.

### Empty state
A short sentence, a single quiet action, lots of space. No illustrations unless they are simple line art in `--ink-faint`.

### Code
Inline: `--bg-sunken`, radius 6px, padding 1px 6px. Block: `--bg-sunken`, radius `--radius-md`, padding 16px, mono 14px. Syntax uses `--ink`, `--ink-soft`, plus the three accent inks only (red for keywords, green for strings, yellow-ink for numbers).


## 8. Voice

The writing matches the look: plain, warm, short.

### Principles
1. **Plain.** Short words, short sentences. Say it once.
2. **Warm.** Like a thoughtful friend, not a brand. Second person ("you") and contractions are fine.
3. **Calm.** No exclamation marks. No urgency theater. No ALL CAPS.
4. **Specific.** Say what happened and what to do next.
5. **Sparing.** At most one emoji, only if the user used one first. Prefer none.

### Patterns

| Situation | Do | Don't |
|---|---|---|
| Success | "Saved." | "Awesome! Your changes were saved successfully!!!" |
| Error | "Couldn't save. Check your connection and try again." | "Error 500: Operation failed." |
| Empty | "Nothing here yet. Add your first note." | "No data available." |
| Confirm | "Delete this note? You can't undo this." | "Are you sure??" |

### Labels
Sentence case everywhere. Buttons are verbs ("Save", "Add note"). Avoid "Submit", "OK", "Click here".


## 9. Review Checklist

Run before delivering. Every box should be true.

### Color
- [ ] Background is cream (`--bg`), not white. Text is brown (`--ink`), not black.
- [ ] Only red, green, and yellow are used as accents. No blue, purple, or gradients.
- [ ] Accents cover under 10% of the view, with one dominant accent.
- [ ] Yellow = focus or primary, green = success, red = danger. No swaps.
- [ ] Text on accent fills is `--ink`. Accent-colored text uses the ink variants.
- [ ] Status is never conveyed by color alone.

### Type and space
- [ ] One font family, weights 400 and 600 only.
- [ ] Sizes come from the scale. Body is 16px with 1.6 line height.
- [ ] All spacing is on the 4px scale. Groups are clearly separated by proximity.

### Shape
- [ ] Radii come from tokens. Borders are 1px warm lines. Shadows are warm and faint.
- [ ] Fewer than two elevation levels are visible at once.

### Motion
- [ ] Only `opacity` and `transform` animate.
- [ ] Durations are 120, 200, or 320ms with the defined easings.
- [ ] Nothing loops except a slow loading indicator.
- [ ] `prefers-reduced-motion` is handled.

### Accessibility
- [ ] Text contrast is at least 4.5:1 (7:1 for body).
- [ ] Focus is visible (2px yellow ring) on every interactive element.
- [ ] Touch targets are at least 44px on mobile.

### Final test
- [ ] Remove one element, one color, or one effect. Does it still work? If yes, leave it removed.


## Appendix: Tokens

```css
/* Quiet Warm — light theme tokens
   Three accents only: yellow, green, red. */

:root {
  color-scheme: light;

  /* Neutrals */
  --bg:           #F8F4EE;
  --bg-raised:    #FCFAF6;
  --bg-sunken:    #EEE7DD;
  --bg-hover:     #E4DCD0;
  --line:         #E9E3DA;
  --line-strong:  #D7CBB9;
  --ink:          #3F2E1C;
  --ink-soft:     #83796D;
  --ink-faint:    #CFC2AF;

  /* Accent: yellow (primary) */
  --yellow:       #EBB421;
  --yellow-hover: #D7A111;
  --yellow-ink:   #8A6508;
  --yellow-soft:  #F7E7B4;

  /* Accent: green (success) */
  --green:        #72CEA6;
  --green-hover:  #5FBE94;
  --green-ink:    #2F7D5C;
  --green-soft:   #D8F0E5;

  /* Accent: red (danger) */
  --red:          #DF483D;
  --red-hover:    #C93C32;
  --red-ink:      #B93A30;
  --red-soft:     #F6D5D1;

  /* Type */
  --font-sans: "Inter", ui-sans-serif, system-ui, -apple-system, "Segoe UI", sans-serif;
  --font-mono: ui-monospace, "SF Mono", "JetBrains Mono", Menlo, monospace;
  --text-xs: 12px;  --text-sm: 14px;  --text-base: 16px;
  --text-lg: 20px;  --text-xl: 28px;  --text-2xl: 36px;
  --weight-regular: 400;  --weight-strong: 600;

  /* Space (4px base) */
  --space-1: 4px;  --space-2: 8px;  --space-3: 12px;  --space-4: 16px;
  --space-5: 24px; --space-6: 32px; --space-7: 48px;  --space-8: 64px;

  /* Shape */
  --radius-sm: 6px;  --radius-md: 10px;  --radius-lg: 16px;  --radius-pill: 999px;

  /* Elevation */
  --shadow-0: none;
  --shadow-1: 0 1px 2px rgba(63, 46, 28, .06);
  --shadow-2: 0 4px 16px rgba(63, 46, 28, .08);
  --shadow-3: 0 12px 32px rgba(63, 46, 28, .12);

  /* Motion */
  --dur-fast: 120ms;  --dur-base: 200ms;  --dur-slow: 320ms;
  --ease-out:    cubic-bezier(0.22, 1, 0.36, 1);
  --ease-settle: cubic-bezier(0.34, 1.3, 0.64, 1);
  --ease-in:     cubic-bezier(0.4, 0, 1, 1);

  /* Focus */
  --focus-ring: 0 0 0 2px var(--bg), 0 0 0 4px var(--yellow);
}

html { background: var(--bg); color: var(--ink); font: var(--weight-regular) var(--text-base)/1.6 var(--font-sans); }
:focus-visible { outline: none; box-shadow: var(--focus-ring); transition: box-shadow var(--dur-fast) var(--ease-out); }
::selection { background: var(--yellow-soft); }

@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { animation-duration: 1ms !important; transition-duration: 1ms !important; }
}
```
