# Perplexity AI Brand & Design System

> **Version:** 1.0.0 | **Status:** Internal Reference | **Maintainers:** Design Systems, Frontend Engineering
> **Last updated:** May 2026 | **Created by:** Smith & Diction (Philadelphia, USA), 2023

---

## Table of Contents

1. [Brand Philosophy](#brand-philosophy)
2. [Design Principles](#design-principles)
3. [Design Tokens — Typography](#design-tokens--typography)
4. [Design Tokens — Color](#design-tokens--color)
5. [Design Tokens — Spacing & Layout](#design-tokens--spacing--layout)
6. [Design Tokens — Elevation & Shadow](#design-tokens--elevation--shadow)
7. [Design Tokens — Border Radius](#design-tokens--border-radius)
8. [Component Guidelines — Left Rail](#component-guidelines--left-rail)
9. [Component Guidelines — Search Bar](#component-guidelines--search-bar)
10. [Component Guidelines — Citation Cards](#component-guidelines--citation-cards)
11. [Interaction Patterns — Streaming](#interaction-patterns--streaming)
12. [Interaction Patterns — Schema Validation](#interaction-patterns--schema-validation)
13. [Interaction Patterns — Information Density](#interaction-patterns--information-density)
14. [Accessibility Standards](#accessibility-standards)
15. [Implementation Notes](#implementation-notes)

---

## Brand Philosophy

### The Invisible AI Principle

Perplexity is designed around one governing idea: **the interface should disappear, leaving only knowledge**. Inspired by the best traditions of Scandinavian utility design — where objects earn their right to exist only through function — every UI element on Perplexity must actively justify its presence. Decoration that does not serve comprehension is removed. Chrome that does not aid navigation is eliminated. The product's aesthetic goal is to be the most invisible layer between a human and the world's information.

This philosophy is captured in the brand's core positioning statements:

- **"Perplexity is where knowledge begins"** — the product is the starting line, not the destination.
- **"Ask questions and trust the answers"** — radical transparency is a design requirement, not a UX nicety.
- **"Know it all"** — the brand invites aspiration without arrogance; utility without condescension.

### Scandinavian Subway Aesthetic

The "Scandinavian subway" metaphor governs spatial decisions. Like the Copenhagen Metro or Stockholm Tunnelbana, Perplexity's UI is:

- **Wayfinding-first:** Every screen resolves to a single primary action. Users never wonder where they are or what to do next.
- **Typographically driven:** Information architecture is communicated through type hierarchy, not decorative elements.
- **Purposefully sparse:** Negative space is treated as a primary design element — not wasted space.
- **Systemically consistent:** Repeated use of the same tokens (radius, shadow, spacing) creates a felt coherence the user can predict.

### Brand Essence

| Attribute | Expression |
|-----------|------------|
| Tone of voice | Minimal, specific, confident, direct — never robotic |
| Visual mood | Curiosity-driven; vintage-futuristic; intellectual warmth |
| Imagery inspiration | 1980s–90s Apple ads; natural landscape photography; classic textbooks; collage |
| Brand differentiation | Transparency via citations; cited answers over opaque generation |

---

## Design Principles

These five principles cascade from the brand philosophy into every design and engineering decision:

**1. Visibility of System Status**
The AI must always communicate what it is doing. Phrases like "Considering 8 sources" or "Researched and summarized" are required UI affordances, not optional polish. Users who can see the work trust the result.

**2. Match Between System and Real World**
Use conversational prompts over jargon. "Ask follow-up…" not "Submit a subsequent query." Interaction language should mirror the natural cadence of human dialogue.

**3. User Control and Freedom**
Users must be able to edit prior prompts, delete follow-up threads, and modify the search scope. Control prevents the feeling of being trapped by the AI's choices.

**4. Consistency and Standards**
Established web conventions are the baseline. Novel patterns are introduced only when they provide a measurable usability advantage. When novelty is required, explain it with tooltips or progressive disclosure — never assume familiarity.

**5. Aesthetic and Minimalist Design**
Every element on-screen competes for cognitive attention. Remove before you add. A cluttered UI is a trust problem, not just an aesthetic one.

---

## Design Tokens — Typography

### Font Stack

```css
--font-primary: 'pplxSans', ui-sans-serif, system-ui, -apple-system, sans-serif;
```

`pplxSans` is Perplexity's proprietary typeface. It pairs the mechanical precision of FK Grotesk-style grotesques with subtle warmth — communicating intellectual authority without clinical coldness. The fallback chain (`ui-sans-serif → system-ui`) ensures graceful degradation on constrained environments.

### Type Scale

| Role | Size | Line Height | Weight | CSS Variable |
|------|------|-------------|--------|--------------|
| Hero / Display | 32px | 1.2 | 600 | `--text-hero` |
| H1 | 24px | 1.3 | 600 | `--text-h1` |
| H2 | 20px | 1.35 | 500 | `--text-h2` |
| H3 | 17px | 1.4 | 500 | `--text-h3` |
| Body (default) | 16px | 1.6 | 400 | `--text-body` |
| Body Small | 14px | 1.55 | 400 | `--text-body-sm` |
| Caption / Meta | 12px | 1.5 | 400 | `--text-caption` |
| Button Label | 16px | 1.0 | 500 | `--text-button` |
| Citation Label | 11px | 1.4 | 500 | `--text-citation` |

> **Note:** The Dembrandt-extracted CSS shows hero, body, and button all rendered at `16px / 400` in production. The expanded scale above represents the full system including editorial and marketing contexts. For product UI, body at 16px is the baseline from which all other roles are derived.

### Typography Rules

- **Never set body copy below 14px** in product UI. Information density must not compromise legibility.
- **Line length (measure):** 60–75 characters for prose blocks (answer body). Do not allow streaming text to reflow across the full viewport width.
- **Letter-spacing:** Default (`0`) for body; use `–0.01em` for display headings to improve optical tightness.
- **Streaming context:** During answer generation, font rendering must remain stable. Do not trigger layout shifts by changing line-height mid-stream.

---

## Design Tokens — Color

### Brand Primitive Palette

These are the raw hex values from which all semantic tokens are derived.

| Token Name | Hex | Description |
|------------|-----|-------------|
| `--color-offblack` | `#0a0a0a` | Near-black; primary surface in dark mode |
| `--color-true-black` | `#000000` | Pure black; used for button fills and hard borders |
| `--color-warm-dark` | `#271a00` | Warm brown-black accent; signals warmth in dark UI |
| `--color-paper-white` | `#f5f0e8` | Off-white cream; primary surface in light/cream mode |
| `--color-true-white` | `#ffffff` | Pure white; button text, hard highlights |
| `--color-turquoise` | `#20b2aa` | True Turquoise; primary brand accent / interactive |
| `--color-turquoise-light` | `#3dd6cc` | Lighter interactive state / hover |
| `--color-turquoise-dark` | `#178a84` | Pressed / active state |
| `--color-ink-100` | `#1a1a1a` | Primary text on light surfaces |
| `--color-ink-60` | `#666666` | Secondary text / meta |
| `--color-ink-40` | `#999999` | Placeholder / disabled |
| `--color-ink-20` | `#cccccc` | Dividers on light surfaces |
| `--color-ink-10` | `#e5e5e5` | Subtle borders on light surfaces |

### Dark Mode Semantic Tokens

Applied when `[data-theme="dark"]` or `@media (prefers-color-scheme: dark)`.

```css
[data-theme="dark"] {
  /* Surfaces */
  --surface-base:       #0a0a0a;
  --surface-raised:     #141414;
  --surface-overlay:    #1e1e1e;
  --surface-sunken:     #060606;

  /* Text */
  --text-primary:       #f0f0f0;
  --text-secondary:     #a0a0a0;
  --text-muted:         #666666;
  --text-on-accent:     #000000;

  /* Interactive */
  --interactive-accent: #20b2aa;
  --interactive-hover:  #3dd6cc;
  --interactive-active: #178a84;
  --interactive-focus:  rgba(32, 178, 170, 0.4);

  /* Borders */
  --border-default:     rgba(255, 255, 255, 0.08);
  --border-strong:      rgba(255, 255, 255, 0.16);
  --border-accent:      #20b2aa;

  /* States */
  --state-error:        #ff6b6b;
  --state-warning:      #ffd166;
  --state-success:      #06d6a0;
}
```

### Cream / Light Mode Semantic Tokens

Perplexity's light theme uses a warm, paper-like cream rather than pure white — this reduces optical strain during extended reading and aligns with the brand's intellectual, analogue warmth.

```css
[data-theme="light"] {
  /* Surfaces */
  --surface-base:       #f5f0e8;   /* Paper White — the defining cream tone */
  --surface-raised:     #ffffff;
  --surface-overlay:    #faf8f4;
  --surface-sunken:     #ede8df;

  /* Text */
  --text-primary:       #1a1a1a;
  --text-secondary:     #555555;
  --text-muted:         #888888;
  --text-on-accent:     #ffffff;

  /* Interactive */
  --interactive-accent: #178a84;   /* Darker turquoise for contrast on light */
  --interactive-hover:  #20b2aa;
  --interactive-active: #0f6b66;
  --interactive-focus:  rgba(23, 138, 132, 0.25);

  /* Borders */
  --border-default:     rgba(0, 0, 0, 0.08);
  --border-strong:      rgba(0, 0, 0, 0.16);
  --border-accent:      #178a84;

  /* States */
  --state-error:        #c0392b;
  --state-warning:      #e67e22;
  --state-success:      #27ae60;
}
```

### Color Usage Rules

- **Never use `--color-true-black` on `--surface-base` in dark mode** — the contrast is excessive and creates visual harshness. Use `--color-offblack` as the surface.
- **Turquoise is reserved for interactive elements only.** Do not use it for decorative borders, backgrounds, or status indicators that are not tappable/clickable.
- **The `--color-warm-dark` (#271a00) token** serves as the warm undercurrent in dark mode — apply to hover states on navigation items to introduce subtle warmth without a full color shift.
- **Cream mode is the "focused reading" mode.** When a user is deep in a long answer, the cream surface reduces eye fatigue far better than stark white.

---

## Design Tokens — Spacing & Layout

### Base Spacing Scale

Derived from a 4px base unit. All spacing values must be multiples of 4.

| Token | Value | Use Case |
|-------|-------|----------|
| `--space-1` | 4px | Icon padding, fine-grained gaps |
| `--space-2` | 8px | Compact element padding |
| `--space-3` | 12px | Default button padding (vertical) |
| `--space-4` | 16px | Component internal padding (standard) |
| `--space-5` | 20px | Card padding |
| `--space-6` | 24px | Section gaps |
| `--space-8` | 32px | Module separation |
| `--space-10` | 40px | Page-level vertical rhythm |
| `--space-12` | 48px | Hero breathing room |
| `--space-16` | 64px | Large section breaks |

> The Dembrandt-extracted CSS confirms 1px, 2px, 4px, 8px, 12px, and 16px as the root observed spacing values in the production codebase. The extended scale above covers the full product surface area.

### Layout Grid

```css
/* Main content area */
--layout-max-width:         768px;   /* Answer prose column */
--layout-sidebar-width:     240px;   /* Left rail */
--layout-sidebar-collapsed: 60px;    /* Left rail — icon-only */
--layout-gutter:            24px;    /* Horizontal page margin */
--layout-content-gap:       16px;    /* Gap between content blocks */
```

### Button Padding (production-confirmed)

```css
.btn {
  padding:       0px 12px;     /* Horizontal: 12px — confirmed from CSS extraction */
  border-radius: 9999px;       /* Fully rounded pill shape */
}
```

---

## Design Tokens — Elevation & Shadow

Perplexity uses shadows sparingly. The design philosophy treats unnecessary elevation as visual noise. Shadows communicate interactivity and separation — nothing more.

```css
/* Shadow scale */
--shadow-sm:   rgba(0, 0, 0, 0.05) 0px 1px 2px 0px;   /* Cards, subtle lift */
--shadow-md:   rgba(0, 0, 0, 0.10) 0px 4px 8px 0px;   /* Dropdowns, popovers */
--shadow-lg:   rgba(0, 0, 0, 0.15) 0px 8px 24px 0px;  /* Modals, search overlays */
--shadow-none: none;                                    /* Default / flat state */
```

> `--shadow-sm` is the only confirmed extracted shadow from production CSS. `--shadow-md` and `--shadow-lg` are inferred from the system's elevation hierarchy.

**Shadow Usage Rules:**

- Use `--shadow-sm` on citation cards and answer panels to create gentle separation without heavy depth.
- Use `--shadow-md` on dropdown menus, source previews, and floating toolbars.
- Use `--shadow-lg` exclusively on modal dialogs and full-screen overlays.
- **Never apply shadows to interactive elements in dark mode.** In dark environments, use border tokens (`--border-default`, `--border-strong`) to denote depth instead.

---

## Design Tokens — Border Radius

Perplexity's corner language is **purposefully mixed** — some elements are pill-shaped (high softness = approachable), others are modestly rounded (moderate softness = structural).

| Token | Value | Applied To |
|-------|-------|------------|
| `--radius-sm` | 6px | Tags, badges, small chips |
| `--radius-md` | 8px | Input fields, small cards |
| `--radius-lg` | 12px | Content cards, answer panels |
| `--radius-xl` | 16px | Modals, large sheet panels |
| `--radius-full` | 9999px | Buttons, avatar chips, pill badges |

> All five values (6, 8, 12, 16, 9999px) are confirmed from Dembrandt CSS extraction of the production `perplexity.ai` codebase.

**Corner Language Principles:**

- **Pill (`9999px`) = action.** If an element invites a click or tap, it should be a pill. This creates a consistent visual grammar: rounded = do something.
- **`12px` = information container.** Answers, cards, and source panels use this radius to feel sturdy but not clinical.
- **Never use `0px` (sharp corners)** in the product UI. Perplexity's brand warmth depends on rounded corners system-wide.

---

## Component Guidelines — Left Rail

The left rail is Perplexity's primary navigation surface. It follows the Scandinavian subway principle most rigidly: every item must earn its place.

### Anatomy

```
┌─────────────────────┐
│  Logo / Wordmark    │  ← 48px height lockup; collapses to icon at <240px
├─────────────────────┤
│  [ New Thread ]     │  ← Primary CTA; pill button; --interactive-accent fill
├─────────────────────┤
│  Nav Items          │  ← Icon + label; 40px row height; 12px horizontal padding
│  › Home             │
│  › Discover         │
│  › Library          │
│  › Spaces           │
├─────────────────────┤
│  [  Spacer  ]       │  ← flex-grow: 1; pushes account to bottom
├─────────────────────┤
│  Account / Settings │  ← Avatar + username; 40px row height
└─────────────────────┘
```

### Token Application

```css
.left-rail {
  width:            var(--layout-sidebar-width);      /* 240px */
  background:       var(--surface-raised);
  border-right:     1px solid var(--border-default);
  padding:          var(--space-4);                   /* 16px */
  gap:              var(--space-2);                   /* 8px between nav items */
  font-family:      var(--font-primary);
  font-size:        var(--text-body-sm);              /* 14px */
}

.left-rail--collapsed {
  width:            var(--layout-sidebar-collapsed);  /* 60px */
}

.nav-item {
  border-radius:    var(--radius-md);                 /* 8px */
  padding:          var(--space-2) var(--space-3);    /* 8px 12px */
  color:            var(--text-secondary);
  transition:       background 150ms ease, color 150ms ease;
}

.nav-item:hover {
  background:       rgba(255, 255, 255, 0.05);        /* Dark mode */
  color:            var(--text-primary);
}

.nav-item--active {
  background:       rgba(32, 178, 170, 0.12);
  color:            var(--interactive-accent);
  font-weight:      500;
}
```

### Behavior Rules

- **Collapse trigger:** Viewport < 900px OR explicit user toggle. Store preference in `localStorage`.
- **Collapsed state:** Show icons only. Tooltip on hover reveals label text (300ms delay, `--shadow-md`).
- **New Thread button:** Always visible in both expanded and collapsed states. Icon-only in collapsed state with the same `--interactive-accent` fill.
- **Active state:** Only one item is ever active. Active item uses a 12% opacity turquoise background — not a solid fill. This maintains the minimal character of the rail.

---

## Component Guidelines — Search Bar

The search bar is the product. All visual weight flows toward it. It is the single most important UI component in the system.

### Anatomy

```
┌──────────────────────────────────────────────────────────┐
│  [Icon]  Ask anything...                    [@ ] [⏎ ]  │
│─────────────────────────────────────────────────────────│
│  [ Web ▾ ]  [ Focus: All ▾ ]                            │
└──────────────────────────────────────────────────────────┘
```

### Token Application

```css
.search-bar {
  background:       var(--surface-overlay);
  border:           1px solid var(--border-default);
  border-radius:    var(--radius-lg);           /* 12px */
  padding:          var(--space-4);             /* 16px */
  box-shadow:       var(--shadow-sm);
  font-family:      var(--font-primary);
  font-size:        var(--text-body);           /* 16px */
  color:            var(--text-primary);
  width:            100%;
  max-width:        var(--layout-max-width);    /* 768px */
  transition:       border-color 150ms ease, box-shadow 150ms ease;
}

.search-bar:focus-within {
  border-color:     var(--border-accent);
  box-shadow:       0 0 0 3px var(--interactive-focus);
  outline:          none;
}

.search-bar__placeholder {
  color:            var(--text-muted);
}

.search-bar__submit-btn {
  background:       var(--color-true-black);    /* #000000 confirmed */
  color:            var(--color-true-white);
  border-radius:    var(--radius-full);         /* 9999px */
  padding:          0px var(--space-3);         /* 0px 12px confirmed */
  font-size:        var(--text-button);
  font-weight:      500;
}
```

### Behavior Rules

- **Focus state is the only elevated state.** The bar's border changes to `--border-accent` (turquoise) on focus. No animation beyond this subtle shift.
- **`@` connector trigger:** Typing `@` opens a source/connector popover. Popover uses `--shadow-md` and `--radius-lg`. Closes on `Esc` or outside click.
- **Multiline expansion:** The textarea grows vertically from `min-height: 56px` to `max-height: 200px`. Never horizontally.
- **Attachment affordance:** File/image attachment icon appears on hover or focus. Does not distract during reading.
- **Submit button disabled state:** When input is empty, submit button uses `opacity: 0.4` and `cursor: not-allowed`. Do not change its color.

---

## Component Guidelines — Citation Cards

Citation cards are one of Perplexity's most distinctive UI patterns. They are the product's primary trust mechanism — making the AI's sources visible and actionable.

### Anatomy — Inline Citation Badge

```
[1]  [2]  [3]     ← Superscript-style pill badges within prose
```

### Anatomy — Source Card (expanded)

```
┌────────────────────────────────────┐
│  [favicon]  Source Title           │
│  domain.com · 2 min read           │
│────────────────────────────────────│
│  "Relevant excerpt from the        │
│   source that supports this        │
│   claim in the answer..."          │
└────────────────────────────────────┘
```

### Token Application

```css
/* Inline citation badge */
.citation-badge {
  display:          inline-flex;
  align-items:      center;
  justify-content:  center;
  background:       rgba(32, 178, 170, 0.12);
  color:            var(--interactive-accent);
  border-radius:    var(--radius-sm);           /* 6px */
  font-size:        var(--text-citation);       /* 11px */
  font-weight:      500;
  padding:          1px 5px;
  cursor:           pointer;
  transition:       background 100ms ease;
}

.citation-badge:hover {
  background:       rgba(32, 178, 170, 0.24);
}

/* Source card */
.source-card {
  background:       var(--surface-raised);
  border:           1px solid var(--border-default);
  border-radius:    var(--radius-lg);           /* 12px */
  padding:          var(--space-4);             /* 16px */
  box-shadow:       var(--shadow-sm);
  max-width:        320px;
  font-family:      var(--font-primary);
}

.source-card__title {
  font-size:        var(--text-body-sm);        /* 14px */
  font-weight:      500;
  color:            var(--text-primary);
  white-space:      nowrap;
  overflow:         hidden;
  text-overflow:    ellipsis;
}

.source-card__meta {
  font-size:        var(--text-caption);        /* 12px */
  color:            var(--text-muted);
  margin-top:       var(--space-1);             /* 4px */
}

.source-card__excerpt {
  font-size:        var(--text-caption);        /* 12px */
  color:            var(--text-secondary);
  line-height:      1.55;
  margin-top:       var(--space-2);             /* 8px */
  border-top:       1px solid var(--border-default);
  padding-top:      var(--space-2);
}
```

### Citation Behavior Rules

- **Anchors, not decoration.** Citation badges exist to slow the user down just enough to think. Do not animate them in a way that draws attention away from the prose.
- **Hover → preview.** Hovering a citation badge shows a `source-card` popover with a 200ms delay. Popover appears above the badge if within 200px of viewport bottom; below otherwise.
- **Click → navigate.** Clicking opens the source URL in a new tab. This is non-negotiable — citations are trust anchors and must be directly verifiable.
- **Citation strip below answer:** Render a horizontal scrollable strip of numbered `source-card` thumbnails beneath every answer block. Do not paginate — show all sources at once with `overflow-x: auto`.
- **Maximum displayed inline:** Cap inline citation badge runs at 3 per sentence. If a sentence has >3 citations, group the remainder into a `+N more` badge with the same styling.

---

## Interaction Patterns — Streaming

Streaming answers are Perplexity's defining real-time interaction. The implementation must communicate progress without generating anxiety or distraction.

### Streaming States

| State | Visual Indicator | Description |
|-------|-----------------|-------------|
| `searching` | Animated pill: "Searching X sources" | AI is querying sources. Show source count as it increments. |
| `reading` | Animated pill: "Reading sources" | AI is processing retrieved content |
| `writing` | Blinking cursor appended to text | Answer text is being generated token by token |
| `complete` | Cursor disappears; action bar appears | Full answer rendered; follow-up affordances appear |

### Streaming Implementation Rules

```css
/* Blinking cursor during stream */
.stream-cursor {
  display:          inline-block;
  width:            2px;
  height:           1em;
  background:       var(--text-primary);
  animation:        blink 0.8s step-end infinite;
  vertical-align:   text-bottom;
  margin-left:      1px;
}

@keyframes blink {
  0%, 100% { opacity: 1; }
  50%       { opacity: 0; }
}

/* Source count pill (searching state) */
.stream-status-pill {
  display:          inline-flex;
  align-items:      center;
  gap:              var(--space-1);             /* 4px */
  background:       var(--surface-overlay);
  border:           1px solid var(--border-default);
  border-radius:    var(--radius-full);
  padding:          var(--space-1) var(--space-3); /* 4px 12px */
  font-size:        var(--text-caption);
  color:            var(--text-secondary);
  font-family:      var(--font-primary);
}
```

**Critical rules:**
- **No layout shifts during streaming.** Reserve space for citation strips before content arrives. Use skeleton placeholders with `--surface-overlay` fills at correct heights.
- **Prose must stream in grammatical chunks** (sentence fragments are acceptable; orphaned words are not). Buffer to the next space character before rendering.
- **Do not re-render completed text.** Only append new tokens to the DOM. Re-rendering the full text on each token causes visible flicker.
- **Abort affordance:** Always show a "Stop generating" control during `searching`, `reading`, and `writing` states. Use icon-only on mobile; icon + label on desktop.

---

## Interaction Patterns — Schema Validation

Perplexity uses structured output schemas for certain answer types (tables, code, comparisons, timelines). Validation must be invisible to the user but robust in implementation.

### Answer Type Classification

| Schema Type | Trigger Signal | Component Rendered |
|-------------|---------------|-------------------|
| `prose` | Default | Markdown-rendered text with citation badges |
| `comparison_table` | ≥2 entities + attribute list detected | Responsive `<table>` with sticky header |
| `code_block` | Code fence ` ``` ` detected | Syntax-highlighted block with copy affordance |
| `numbered_list` | Sequential steps detected | Ordered list with `--space-4` row gap |
| `timeline` | Date-ordered events detected | Vertical timeline with accent connector line |
| `math` | LaTeX fences detected | KaTeX-rendered block with fallback to code |

### Validation Rules

- **Graceful degradation:** If schema parsing fails, fall back to `prose` rendering. Never show a schema error to the user.
- **Table overflow:** Comparison tables wider than the `--layout-max-width` (768px) must scroll horizontally. Use `overflow-x: auto` on the table wrapper — do not truncate columns.
- **Code blocks:** Apply a monospace font override (`ui-monospace, 'Cascadia Code', monospace`) within code blocks only. Do not inherit `pplxSans` in code contexts.
- **Citation injection into structured answers:** Citation badges must be injectable into any schema type. In tables, they appear as superscript within cells; in code blocks, they are prohibited (code should never be cited inline).
- **Empty state:** If a schema type is detected but produces zero valid rows/items, do not render the empty structure. Fall back to a prose explanation.

---

## Interaction Patterns — Information Density

Perplexity serves a wide density spectrum — from quick factual lookups to deep research sessions. The UI must adapt without requiring explicit user configuration.

### Density Levels

| Level | Context | Characteristics |
|-------|---------|----------------|
| `compact` | Quick facts, definitions | Single paragraph; ≤3 citations; no follow-up strip |
| `standard` | Most queries | 2–4 paragraphs; citation strip; follow-up questions |
| `detailed` | Research / Pro queries | Full sections with H2/H3; citation strip; related searches; structured schema blocks |

### Density Implementation Principles

**1. Progressive disclosure, not progressive overload.**
Start every answer in `compact` form. Expand to `standard` as soon as a second paragraph is needed. Reveal `detailed` affordances (section headers, related searches) only after the answer body is complete.

**2. Follow-up questions reduce cognitive effort.**
The three suggested follow-up questions below every answer are not decorative. They anticipate the user's next intellectual move, reducing the work of formulating a new query. Style these as `--radius-full` pills with `--surface-overlay` fill and `--text-secondary` color.

**3. The answer column width is fixed.**
`max-width: 768px` is not negotiable for prose. Wider lines actively harm comprehension. Do not expand the answer column on wide viewports — add whitespace to the margins instead.

**4. Source strip density.**
In `compact` mode, show ≤3 source cards horizontally. In `standard`/`detailed`, show all sources in a scrollable horizontal strip. Never paginate citations.

**5. Cognitive anchoring via citation count.**
Surface the source count ("Considering 8 sources") before streaming begins. This single piece of metadata sets the user's trust calibration for the entire answer that follows. Do not suppress it in any density mode.

### Responsive Density Breakpoints

```css
/* Full layout: sidebar + content */
@media (min-width: 1024px) {
  .layout { display: grid; grid-template-columns: var(--layout-sidebar-width) 1fr; }
}

/* Collapsed sidebar + content */
@media (min-width: 768px) and (max-width: 1023px) {
  .layout { display: grid; grid-template-columns: var(--layout-sidebar-collapsed) 1fr; }
}

/* Single column (mobile) */
@media (max-width: 767px) {
  .layout           { display: block; }
  .left-rail        { display: none; }         /* Replaced by bottom nav */
  .content-column   { padding: 0 var(--space-4); }
}
```

---

## Accessibility Standards

- **Contrast ratios:** All text must meet WCAG 2.1 AA minimum (4.5:1 for body text, 3:1 for large text). `--text-primary` on `--surface-base` in both dark and cream modes is pre-validated against these ratios.
- **Focus rings:** All interactive elements must display a visible focus indicator using `--interactive-focus` (the 40% opacity turquoise ring). Never suppress `outline` without replacing it.
- **Citation badges ARIA:** `<button aria-label="Source 1: [Source Title]">1</button>`. Screen readers must announce citation numbers with context.
- **Streaming live region:** The answer container must carry `aria-live="polite"` so streaming text is announced without overwhelming the user.
- **Reduced motion:** Respect `@media (prefers-reduced-motion: reduce)`. Disable the `blink` cursor animation and replace with a static underline cursor in reduced-motion contexts.
- **Keyboard navigation:** `Tab` traverses all interactive elements (citation badges, nav items, follow-up pills) in a logical left-to-right, top-to-bottom order. `Enter`/`Space` activates. `Esc` closes all popovers and modals.

---

## Implementation Notes

### Framework & Tooling

- **CSS framework:** Tailwind CSS (confirmed from Dembrandt extraction). Use the full token system above as a Tailwind theme extension.
- **CSS variables:** All tokens above should be registered as CSS custom properties under `:root` and theme-variant selectors. Token values in `tailwind.config.js` should reference CSS variables, not hardcoded values.
- **Font loading:** `pplxSans` must be loaded with `font-display: swap` to prevent FOIT. Preload the woff2 variant for the 400 and 500 weights.

### Tailwind Config Excerpt

```js
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      fontFamily: {
        sans: ['pplxSans', 'ui-sans-serif', 'system-ui'],
      },
      colors: {
        turquoise: {
          DEFAULT: '#20b2aa',
          light:   '#3dd6cc',
          dark:    '#178a84',
        },
        cream: '#f5f0e8',
        offblack: '#0a0a0a',
        'warm-dark': '#271a00',
      },
      borderRadius: {
        sm:   '6px',
        md:   '8px',
        lg:   '12px',
        xl:   '16px',
        full: '9999px',
      },
      boxShadow: {
        sm: 'rgba(0, 0, 0, 0.05) 0px 1px 2px 0px',
        md: 'rgba(0, 0, 0, 0.10) 0px 4px 8px 0px',
        lg: 'rgba(0, 0, 0, 0.15) 0px 8px 24px 0px',
      },
      spacing: {
        '1':  '4px',
        '2':  '8px',
        '3':  '12px',
        '4':  '16px',
        '5':  '20px',
        '6':  '24px',
        '8':  '32px',
        '10': '40px',
        '12': '48px',
        '16': '64px',
      },
    },
  },
}
```

### Token Provenance

| Token Category | Source |
|----------------|--------|
| Font family | Dembrandt CSS extraction — `pplxSans, ui-sans-serif, system-ui` (confirmed) |
| Base font size | Dembrandt — `16px / 400` for hero, body, button |
| Primary colors | Dembrandt extraction + brandingstyleguides.com (Offblack, Paper White, True Turquoise) |
| Spacing primitives | Dembrandt — `1px, 2px, 4px, 8px, 12px, 16px` (confirmed) |
| Border radius | Dembrandt — `6px, 8px, 12px, 16px, 9999px` (confirmed) |
| Button shape/padding | Dembrandt — `radius: 9999px, padding: 0px 12px` (confirmed) |
| Shadow | Dembrandt — `rgba(0, 0, 0, 0.05) 0px 1px 2px 0px` (confirmed) |
| Dark/cream modes | Brand guidelines + oreateai.com design philosophy analysis |
| Brand identity | Smith & Diction, Philadelphia 2023; designhoops.com analysis |

---

*This document is a living reference. Submit corrections or additions via PR to the design-system repository. Token values marked "confirmed" are extracted from production CSS and should not be modified without cross-team review.*
