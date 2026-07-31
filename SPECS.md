<div align="center">

# 🧾 SPEC REGISTRY

Every artifact in SPEC OS traces back to a numbered specification.

</div>

---

## Index

| ID | Title | Status | Sprint | Owner |
|----|-------|--------|--------|-------|
| [SPEC-000](#spec-000--design-system) | Design System | ✅ Approved | 1 | ehsah-2k4 |
| [SPEC-001](#spec-001--identity) | Identity Specification | ✅ Approved | 1 | ehsah-2k4 |
| [SPEC-002](#spec-002--hero-banner) | Hero Banner | ✅ Approved | 1 | ehsah-2k4 |
| [SPEC-003](#spec-003--boot-screen) | Boot Screen | ✅ Approved | 1 | ehsah-2k4 |
| [SPEC-004](#spec-004--mission-control) | Mission Control Dashboard | ✅ Approved | 2 | ehsah-2k4 |
| [SPEC-005](#spec-005--terminal--easter-egg) | Terminal & Easter Egg | ✅ Approved | 3 | ehsah-2k4 |
| [SPEC-006](#spec-006--automation) | GitHub Actions Automation | 🟡 Draft | 4 | ehsah-2k4 |

**Status legend:** ✅ Approved · 🟡 Draft · 🔵 In Review · ⚪ Proposed · 🔴 Deprecated

---

## SPEC-000 · Design System

**Status:** ✅ Approved · **Version:** 1.0

**Goal** — A single source of truth for color, type, spacing, motion and SVG rules
so every asset is reproducible without taste-based debate.

**Requirements**
- Locked 7-color core palette; extended colors derived only.
- 4px spacing base, 1.250 type scale, 12-column / 1200px canvas.
- Motion tokens + `prefers-reduced-motion` in every animated asset.
- SVG rules: viewBox, prefixed ids, mono font fallback stack, size budgets.

**Out of scope** — Light theme. Any second accent hue.

**Deliverable** — [`DESIGN_SYSTEM.md`](./DESIGN_SYSTEM.md), [`themes/spec-os.json`](./themes/spec-os.json)

---

## SPEC-001 · Identity

**Status:** ✅ Approved · **Version:** 1.0

**Goal** — Define the canonical identity surfaced across all SPEC OS artifacts.

```yaml
owner:     Muhammad Ehsan
username:  ehsah-2k4
role:      Full Stack Developer
location:  Pakistan
languages: [JavaScript, TypeScript, Python]
stack:     [Next.js, Node.js]
theme:     Purple Neon
featured:  Portfolio
```

**Rules** — Name always renders as `MUHAMMAD EHSAN` in the hero. Product string is
exactly `SPEC OS v1.0`. Never `SpecOS`, never `SPEC-OS`.

**Deliverable** — [`ABOUT.md`](./ABOUT.md)

---

## SPEC-002 · Hero Banner

**Status:** ✅ Approved · **Version:** 1.0

**Goal** — One animated SVG that establishes identity in under two seconds.

**Requirements**
- Canvas `1200×400`, radius 20, self-contained `#0D1117` background.
- Left column: `SPEC OS v1.0` label → name → role → rule → status pill → tagline → chips.
- Right column: circular avatar, 4px `--grad-brand` ring + glow, dashed orbit ring, `@ehsah-2k4`.
- Background: drifting blueprint grid (18s) + 6–10 floating particles (opacity ≤ .5) + scanline (opacity .06).
- Status pill: 🟢 `SYSTEM ONLINE`, pulsing dot, 2s.

**Tagline loop (locked)** — 12s total, 3 phrases × 4s, infinite:
1. `Engineering software with specifications first.`
2. `Where every feature begins with a specification.`
3. `Predictable systems. Intentional architecture.`

**Acceptance** — ≤ 60KB · renders on GitHub dark + light · reduced-motion shows phrase 1 static.

**Deliverable** — [`assets/hero.svg`](./assets/hero.svg)

---

## SPEC-003 · Boot Screen

**Status:** ✅ Approved · **Version:** 1.0

**Goal** — Frame the profile as an operating system starting up.

**Requirements**
- Canvas `1200×500`, terminal chrome with 3 traffic-light dots.
- Prompt: `visitor@spec-os:~$ boot --profile ehsah-2k4`.
- Sequential `[ OK ]` lines (350ms stagger) for identity, design system, theme, runtime, registry.
- One `[ ** ]` line teasing the hidden `unlock` command.
- Progress bar 0→100% over 2.6s `ease-out`, `--grad-brand` + glow.
- Ends on 🟢 `SYSTEM ONLINE` and a blinking caret.

**Deliverable** — [`assets/boot.svg`](./assets/boot.svg)

---

## SPEC-004 · Mission Control

**Status:** ✅ Approved · **Version:** 1.0

**Goal** — Communicate activity at a glance without lying about numbers.

**Requirements**
- Canvas `1200×360`. Four stat tiles on the 12-col grid (3 col each, 24 gutter).
- Tiles: Specs Written · Active Projects (featured variant) · Stack Modules · Uptime.
- Tile = label (micro, tracked) + value (display, tabular) + trend (small).
- Staggered entrance 100ms; commit sparkline draws over 2.4s.
- Exactly one featured tile (purple border + glow) per view.

**Deliverable** — [`assets/dashboard.svg`](./assets/dashboard.svg)

---

## SPEC-005 · Terminal & Easter Egg

**Status:** ✅ Approved · **Version:** 1.0

**Goal** — An interactive-feeling terminal plus one memorable hidden reward.

**Requirements**
- Prompt format: `visitor@spec-os:~$` — user `#22C55E`, host `#A855F7`, `$` `#8B949E`.
- `help` lists: `whoami`, `stack`, `projects`, `specs`, `contact`.
- Hidden command `unlock` is **not** listed in help.

**Easter egg output (locked)**
```
ACCESS GRANTED

Welcome, curious developer.

You found the hidden room.

:)
```

- In README, delivered via a `<details>` block so it's genuinely clickable.
- `ACCESS GRANTED` renders in `--success` with glow, tracked uppercase.

**Deliverable** — [`assets/terminal.svg`](./assets/terminal.svg), README `<details>` block

---

## SPEC-006 · Automation

**Status:** 🟡 Draft · **Target:** Sprint 4

**Goal** — Keep the profile alive without manual edits.

**Proposed**
- `spec-check.yml` — validate SVG budgets, palette compliance, dead links on PR.
- `metrics.yml` — refresh dashboard stats on a daily cron.
- `changelog.yml` — enforce a CHANGELOG entry on every version bump.

**Open questions** — Commit generated SVGs back to `main`, or render at request time?

**Deliverable** — [`.github/workflows/`](./.github/workflows/)

---

## Writing a New Spec

```markdown
## SPEC-XXX · Title
**Status:** ⚪ Proposed · **Version:** 0.1 · **Sprint:** N
**Goal** — one sentence.
**Requirements** — numbered, testable.
**Out of scope** — explicit non-goals.
**Acceptance** — how we know it's done.
**Deliverable** — file path.
```

Rules: ids are sequential and never reused · every spec declares out-of-scope ·
a spec is Approved only when acceptance criteria are testable.

---

<div align="center">

`Every feature begins with a specification.`

[← Back to README](./README.md)

</div>
