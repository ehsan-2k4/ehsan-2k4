<div align="center">

# 🎨 SPEC OS — DESIGN SYSTEM

**Version 1.0** · Status: ✅ Approved · Owner: Muhammad Ehsan (`ehsah-2k4`)

`GitHub Dark × Cyberpunk × Apple Clean`

</div>

---

> **SPEC-000 — Design System**
> This document is the DNA of SPEC OS. No asset, banner, card, or SVG is created
> unless it can be traced back to a rule written here. Spec first. Always.

---

## 📑 Table of Contents

| # | Section |
|---|---------|
| 01 | [Design Principles](#01--design-principles) |
| 02 | [Color System](#02--color-system) |
| 03 | [Typography](#03--typography) |
| 04 | [Spacing & Sizing](#04--spacing--sizing) |
| 05 | [Layout Grid](#05--layout-grid) |
| 06 | [Elevation, Glow & Radius](#06--elevation-glow--radius) |
| 07 | [Iconography](#07--iconography) |
| 08 | [Components](#08--components) |
| 09 | [Cards](#09--cards) |
| 10 | [Animation System](#10--animation-system) |
| 11 | [SVG Rules](#11--svg-rules) |
| 12 | [Branding Rules](#12--branding-rules) |
| 13 | [Accessibility](#13--accessibility) |
| 14 | [Design Tokens (JSON)](#14--design-tokens) |

---

## 01 · Design Principles

| # | Principle | Meaning |
|---|-----------|---------|
| 1 | **Spec before pixel** | Every visual decision exists as a written rule first. |
| 2 | **Dark by default** | There is no light theme. The void is the canvas. |
| 3 | **Glow, don't shout** | Neon is an accent, never a background. Max 2 glow sources per view. |
| 4 | **Breathing room** | Whitespace is a feature. Density is a bug. |
| 5 | **Predictable motion** | Motion communicates state, never decorates emptiness. |
| 6 | **One accent family** | Purple owns the brand. Green speaks only for status. |
| 7 | **Vector only** | Every asset ships as SVG. No PNG in the repo root. |

---

## 02 · Color System

### 2.1 Core Palette (locked 🔒)

| Token | Hex | Preview | Role |
|-------|-----|---------|------|
| `--bg` | `#0D1117` | ![](https://readme-swatches.vercel.app/0D1117?style=round) | Page background / canvas |
| `--card` | `#161B22` | ![](https://readme-swatches.vercel.app/161B22?style=round) | Surfaces, cards, panels |
| `--primary` | `#A855F7` | ![](https://readme-swatches.vercel.app/A855F7?style=round) | Primary glow, brand, links |
| `--secondary` | `#7C3AED` | ![](https://readme-swatches.vercel.app/7C3AED?style=round) | Secondary glow, gradients |
| `--accent` | `#C084FC` | ![](https://readme-swatches.vercel.app/C084FC?style=round) | Highlights, hover, headings |
| `--success` | `#22C55E` | ![](https://readme-swatches.vercel.app/22C55E?style=round) | SYSTEM ONLINE, passing states |
| `--text` | `#F8FAFC` | ![](https://readme-swatches.vercel.app/F8FAFC?style=round) | Primary text |

### 2.2 Extended Palette (derived — do not invent new hues)

| Token | Hex | Role |
|-------|-----|------|
| `--border` | `#30363D` | 1px hairlines, card outlines |
| `--muted` | `#8B949E` | Secondary text, captions, timestamps |
| `--dim` | `#484F58` | Disabled, grid lines, blueprint strokes |
| `--surface-2` | `#1C2128` | Nested cards, code blocks, terminal body |
| `--warn` | `#F59E0B` | In-progress / WIP badges |
| `--danger` | `#EF4444` | Deprecated / failed builds |

### 2.3 Gradients

```css
--grad-brand:  linear-gradient(135deg, #7C3AED 0%, #A855F7 50%, #C084FC 100%);
--grad-surface:linear-gradient(180deg, #161B22 0%, #0D1117 100%);
--grad-glow:   radial-gradient(circle, rgba(168,85,247,.35) 0%, rgba(13,17,23,0) 70%);
--grad-line:   linear-gradient(90deg, transparent, #A855F7, transparent);
```

### 2.4 Usage Ratio — the 60/30/10 rule

```
60%  ██████████████████  #0D1117 + #161B22   (surfaces)
30%  █████████           #F8FAFC + #8B949E   (text)
10%  ███                 #A855F7 / #C084FC   (glow + accent)
 ‹1% ▌                   #22C55E             (status only)
```

> ❌ Never use `--success` for decoration. Green = a system is alive.

---

## 03 · Typography

### 3.1 Families

| Role | Font | Fallback stack |
|------|------|----------------|
| **Display / Headings** | `Space Grotesk` | `Inter, "Segoe UI", system-ui, sans-serif` |
| **Body / UI** | `Inter` | `system-ui, -apple-system, sans-serif` |
| **Mono / Terminal / Code** | `JetBrains Mono` | `"Fira Code", "SF Mono", Consolas, monospace` |

> In SVG assets, always ship the full fallback stack — GitHub does not load webfonts inside SVG.
> Canonical SVG stack: `font-family="JetBrains Mono, Fira Code, Consolas, monospace"`.

### 3.2 Type Scale (1.250 — Major Third)

| Token | Size | Line-height | Weight | Tracking | Use |
|-------|------|-------------|--------|----------|-----|
| `display` | 48px | 1.1 | 700 | -0.02em | Hero name |
| `h1` | 38px | 1.15 | 700 | -0.02em | Page titles |
| `h2` | 30px | 1.2 | 600 | -0.01em | Section titles |
| `h3` | 24px | 1.3 | 600 | 0 | Card titles |
| `h4` | 20px | 1.4 | 600 | 0 | Sub-headings |
| `body` | 16px | 1.6 | 400 | 0 | Paragraphs |
| `small` | 14px | 1.5 | 400 | 0 | Captions, meta |
| `micro` | 12px | 1.4 | 500 | **+0.18em** | Labels, badges, `SPEC OS v1.0` |
| `code` | 14px | 1.5 | 400 | 0 | Terminal, code |

### 3.3 Rules

- Uppercase + `+0.18em` tracking is reserved for **labels and system text** only.
- Never more than **3 type sizes** in one card.
- Body copy max width: **72ch**.
- Numbers in stats: mono, `font-variant-numeric: tabular-nums`.

---

## 04 · Spacing & Sizing

Base unit **`4px`**. Everything is a multiple. No exceptions.

| Token | px | Typical use |
|-------|----|-------------|
| `space-1` | 4 | Icon ↔ label gap |
| `space-2` | 8 | Inline padding, badge padding |
| `space-3` | 12 | Tight stacks |
| `space-4` | 16 | Default gap, card inner padding (small) |
| `space-6` | 24 | Card padding (default) |
| `space-8` | 32 | Section inner spacing |
| `space-12` | 48 | Between major blocks |
| `space-16` | 64 | Section separation |
| `space-24` | 96 | Hero vertical rhythm |

**Sizing rules**

- Card min-height: `120px` · Card max-width: `440px`
- Badge height: `28px` · Button height: `40px`
- Icon sizes: `16 / 20 / 24 / 32 / 48`
- Hairline: exactly `1px` at `--border`

---

## 05 · Layout Grid

### 5.1 README Canvas

| Property | Value |
|----------|-------|
| Design width | **1200px** (GitHub README safe width ≈ 880px rendered) |
| Columns | 12 |
| Gutter | 24px |
| Margin | 48px |
| Baseline | 8px |

### 5.2 Standard Compositions

```
HERO          ┌──────────────────────────────────────┐
              │  text block (7 col)  │  avatar (5)   │
              └──────────────────────────────────────┘

DASHBOARD     ┌────────┬────────┬────────┬────────┐
              │ stat   │ stat   │ stat   │ stat   │   4 × 3col
              └────────┴────────┴────────┴────────┘

PROJECTS      ┌──────────────┬──────────────┐
              │  card 6col   │  card 6col   │
              └──────────────┴──────────────┘

TERMINAL      ┌──────────────────────────────────────┐
              │  full bleed 12col                    │
              └──────────────────────────────────────┘
```

### 5.3 Breakpoints (for web port of SPEC OS)

| Name | Width | Grid |
|------|-------|------|
| `sm` | < 640 | 4 col |
| `md` | 640–1024 | 8 col |
| `lg` | > 1024 | 12 col |

---

## 06 · Elevation, Glow & Radius

### 6.1 Radius

| Token | Value | Use |
|-------|-------|-----|
| `r-sm` | 6px | Badges, chips |
| `r-md` | 10px | Buttons, inputs |
| `r-lg` | 14px | Cards, panels |
| `r-xl` | 20px | Hero container, terminal window |
| `r-full` | 9999px | Avatar ring, status dots |

### 6.2 Elevation Layers

| Level | Definition | Use |
|-------|------------|-----|
| `e0` | flat `--bg` | Page |
| `e1` | `--card` + 1px `--border` | Default card |
| `e2` | `e1` + `0 8px 24px rgba(0,0,0,.45)` | Hover / modal |
| `e3` | `e2` + purple glow | Featured / active |

### 6.3 Glow Recipes

```css
--glow-sm: 0 0 8px  rgba(168,85,247,.35);
--glow-md: 0 0 18px rgba(168,85,247,.45);
--glow-lg: 0 0 42px rgba(124,58,237,.55);
--glow-ok: 0 0 12px rgba(34,197,94,.55);
```

SVG equivalent (always define once per file, id-prefixed):

```xml
<filter id="specGlow" x="-50%" y="-50%" width="200%" height="200%">
  <feGaussianBlur stdDeviation="4" result="b"/>
  <feMerge><feMergeNode in="b"/><feMergeNode in="SourceGraphic"/></feMerge>
</filter>
```

> 🔒 **Rule:** maximum **two** glow sources per composition. A third kills the mood.

---

## 07 · Iconography

| Property | Spec |
|----------|------|
| Library | Lucide (line) — or hand-drawn matching its geometry |
| Grid | 24 × 24 |
| Stroke | **1.75px**, `round` cap, `round` join |
| Color | `--muted` default · `--accent` active · `--success` status |
| Fill | None (line icons only) |
| Padding | 2px optical inside the 24 grid |

**Approved icon set for SPEC OS**

`terminal` · `cpu` · `layers` · `git-branch` · `zap` · `shield-check` · `activity`
`box` · `code-2` · `rocket` · `sparkles` · `lock` · `radio` · `file-code`

> ❌ No emoji inside SVG assets. ✅ Emoji allowed in Markdown headings only.

---

## 08 · Components

### 8.1 Badge / Chip

```
height 28 · radius 6 · padding 0 10 · micro type · uppercase · +0.18em
bg #161B22 · border 1px #30363D · text #C084FC
active → border #A855F7 + glow-sm
```

### 8.2 Status Pill

```
🟢 SYSTEM ONLINE
dot 8px #22C55E + glow-ok + pulse 2s · label micro uppercase #F8FAFC
```

### 8.3 Button

| State | Spec |
|-------|------|
| Default | bg `--grad-brand`, text `#F8FAFC`, radius 10, height 40, padding 0 20 |
| Hover | `translateY(-1px)` + `--glow-md` |
| Ghost | transparent, 1px `--border`, text `--accent` |
| Disabled | bg `--surface-2`, text `--dim`, no glow |

### 8.4 Progress / Loader Bar

```
track  height 8  radius full  bg #1C2128
fill   --grad-brand + glow-sm
boot   animated 0 → 100% over 2.4s ease-out
```

### 8.5 Divider

```
1px line, --grad-line, opacity .6, margin 48px 0
```

### 8.6 Terminal Window

```
frame     radius 20 · bg #0D1117 · border 1px #30363D · glow-md
titlebar  height 36 · bg #161B22 · 3 dots (#EF4444 #F59E0B #22C55E) 10px
prompt    visitor@spec-os:~$   →  user #22C55E · host #A855F7 · path #8B949E
caret     4×16 block #C084FC · blink 1s step-end infinite
body      JetBrains Mono 14 · line-height 1.7 · padding 20
```

### 8.7 Stat Tile

```
label  micro uppercase --muted
value  h2 mono tabular --text
trend  small --success / --danger
card   e1 · radius 14 · padding 24 · hover → e3
```

---

## 09 · Cards

### 9.1 Anatomy

```
┌─ 1px #30363D ─────────────────────────────┐
│  [icon 24]  TITLE (h3)          [badge]   │  ← 24 padding
│                                           │
│  description — small, --muted, max 2 lines│
│                                           │
│  ▸ tech chips                    ▸ links  │
└───────────────────────────────────────────┘
   bg #161B22 · radius 14 · e1
```

### 9.2 Variants

| Variant | Difference |
|---------|-----------|
| **Default** | as above |
| **Featured** | 1px `--primary` border + `--glow-md` + top gradient hairline |
| **Spec Card** | left 3px `--accent` rail, mono title, `SPEC-XXX` prefix |
| **Ghost** | transparent bg, dashed `--dim` border — used for "coming soon" |

### 9.3 Rules

- Title max **32 chars**, description max **90 chars**.
- Exactly **one** badge per card.
- Tech chips: max 4, then `+N`.
- Hover lift: `-2px`, 180ms `ease-out`.

---

## 10 · Animation System

### 10.1 Motion Tokens

| Token | Value | Use |
|-------|-------|-----|
| `dur-fast` | 150ms | Hover, chips |
| `dur-base` | 240ms | Cards, buttons |
| `dur-slow` | 480ms | Panels, reveals |
| `dur-cine` | 2400ms | Boot sequence |
| `ease-out` | `cubic-bezier(.16,1,.3,1)` | Enter |
| `ease-in-out` | `cubic-bezier(.65,0,.35,1)` | Loops |
| `ease-step` | `steps(N)` | Typing, caret |

### 10.2 Named Animations

| Name | Spec |
|------|------|
| `type-in` | `steps(chars)` reveal, ~55ms per char |
| `fade-cycle` | in 600ms → hold 2600ms → out 600ms |
| `pulse-dot` | scale 1→1.25→1, opacity .6→1→.6, 2s infinite |
| `caret-blink` | opacity 1↔0, 1s `steps(1)` infinite |
| `float-particle` | translateY ±10px + opacity .2→.7, 6–11s, staggered |
| `blueprint-drift` | grid translate 0→40px, 18s linear infinite |
| `scanline` | vertical sweep, 4s linear infinite, opacity .06 |
| `glow-breathe` | stdDeviation 3↔6, 3.5s ease-in-out infinite |

### 10.3 Hero Typing Sequence 🔒

Total loop: **12s**, three phrases × 4s, infinite.

```
0.0s   ▸ type   "Engineering software with specifications first."
3.4s   ▸ fade out
4.0s   ▸ type   "Where every feature begins with a specification."
7.4s   ▸ fade out
8.0s   ▸ type   "Predictable systems. Intentional architecture."
11.4s  ▸ fade out
12.0s  ▸ loop
```

Background during loop: animated purple **blueprint lines** (`blueprint-drift`) + soft **particle glow** (`float-particle`, 6–10 particles, opacity ≤ .5).

### 10.4 Rules

- Never animate `width`/`height`/`top`/`left` — only `transform` and `opacity`.
- Max **3 concurrent** animation groups per asset.
- Always honor:

```css
@media (prefers-reduced-motion: reduce) {
  * { animation: none !important; transition: none !important; }
}
```

---

## 11 · SVG Rules

| # | Rule |
|---|------|
| 1 | **viewBox mandatory**, no fixed `width`/`height` attributes on root when embedding responsively. |
| 2 | Canonical sizes — banner `1200×400`, boot `1200×500`, dashboard `1200×360`, terminal `1200×420`, logo `256×256`, icon `24×24`. |
| 3 | All animation via **inline `<style>` CSS** — SMIL only where CSS can't (path morph). |
| 4 | **Prefix every `id`** with the asset name (`hero-glow`, `boot-grad`) — GitHub inlines multiple SVGs and ids collide. |
| 5 | Fonts: full fallback stack, mono-first. Never `@import` a webfont. |
| 6 | Colors: only tokens from §02. No raw hex outside the palette. |
| 7 | Optimize: no editor metadata, 2-decimal precision, `<title>` + `<desc>` for a11y. |
| 8 | File size budget: banner ≤ 60KB, icon ≤ 4KB. |
| 9 | No external references (`xlink:href` to remote, remote images) — GitHub strips them. |
| 10 | Test rendered on **both** GitHub dark and light chrome — asset must carry its own `--bg` rect. |

---

## 12 · Branding Rules

### 12.1 Logo

- Mark: hexagonal **`⬡`** spec-chip containing a mono `S` / terminal caret.
- Clear space: **≥ 0.5 ×** logo height on all sides.
- Min size: 32px (mark only), 120px (lockup).
- Approved on: `--bg`, `--card`, pure black. ❌ Never on white, never on photos.

### 12.2 Naming

| Correct | Wrong |
|---------|-------|
| `SPEC OS` | ~~Spec OS~~, ~~SpecOS~~, ~~SPEC-OS~~ |
| `SPEC OS v1.0` | ~~SPEC OS V1~~ |
| `SPEC-001` (spec ids) | ~~spec001~~ |

### 12.3 Voice

- Declarative, engineering-grade, calm. Short sentences.
- System messages are **UPPERCASE + tracked**: `SYSTEM ONLINE`, `ACCESS GRANTED`.
- Taglines are lowercase-sentence-case, ending in a period.
- Never exclamation marks in system copy.

### 12.4 Do / Don't

| ✅ Do | ❌ Don't |
|------|---------|
| One accent purple family | Mix blue/pink neon |
| Dark canvas always | Light-mode variants |
| SVG assets | PNG screenshots as banners |
| Green for status | Green for decoration |
| 4px spacing multiples | Arbitrary 13px, 27px |

---

## 13 · Accessibility

| Check | Requirement |
|-------|-------------|
| Body text contrast | `#F8FAFC` on `#0D1117` = **17.4:1** ✅ AAA |
| Muted text | `#8B949E` on `#0D1117` = **6.3:1** ✅ AA |
| Accent text | `#C084FC` on `#0D1117` = **8.1:1** ✅ AAA |
| Primary on card | `#A855F7` on `#161B22` = **5.6:1** ✅ AA |
| Non-text (borders) | ≥ 3:1 for interactive outlines |
| Motion | `prefers-reduced-motion` respected in every asset |
| Alt text | Every README image has a descriptive `alt` |
| Meaning | Never encode meaning in color alone — pair with label/icon |

---

## 14 · Design Tokens

`themes/spec-os.json`

```json
{
  "name": "SPEC OS",
  "version": "1.0",
  "color": {
    "bg": "#0D1117", "card": "#161B22", "surface2": "#1C2128",
    "primary": "#A855F7", "secondary": "#7C3AED", "accent": "#C084FC",
    "success": "#22C55E", "warn": "#F59E0B", "danger": "#EF4444",
    "text": "#F8FAFC", "muted": "#8B949E", "dim": "#484F58", "border": "#30363D"
  },
  "radius": { "sm": 6, "md": 10, "lg": 14, "xl": 20, "full": 9999 },
  "space":  { "1": 4, "2": 8, "3": 12, "4": 16, "6": 24, "8": 32, "12": 48, "16": 64, "24": 96 },
  "font": {
    "display": "Space Grotesk",
    "body": "Inter",
    "mono": "JetBrains Mono"
  },
  "motion": { "fast": 150, "base": 240, "slow": 480, "cine": 2400 }
}
```

---

<div align="center">

**SPEC-000 · Locked 🔒**

`Every feature begins with a specification.`

</div>
