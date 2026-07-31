<div align="center">

# 🕓 CHANGELOG

All notable changes to SPEC OS.
Format follows [Keep a Changelog](https://keepachangelog.com/) · versioning follows [SemVer](https://semver.org/).

</div>

---

## [1.0.0] — 2026-07-31

### 🎉 Initial system boot

**Added — Specifications**
- `SPEC-000` Design System — colors, typography, spacing, grid, motion, SVG rules, branding, a11y, tokens
- `SPEC-001` Identity — owner, handle, role, stack, theme locked
- `SPEC-002` Hero Banner — 12s three-phrase tagline loop
- `SPEC-003` Boot Screen — staggered `[ OK ]` module load + progress bar
- `SPEC-004` Mission Control — four stat tiles + commit sparkline
- `SPEC-005` Terminal & Easter Egg — `unlock` hidden room
- `SPEC-006` Automation — drafted for Sprint 4

**Added — Documents**
- `README.md`, `DESIGN_SYSTEM.md`, `ABOUT.md`, `MANIFESTO.md`
- `SPECS.md`, `PROJECTS.md`, `ROADMAP.md`, `COMMANDS.md`, `CHANGELOG.md`

**Added — Assets**
- `assets/logo.svg` — hexagonal spec chip, breathing halo, orbiting dashed hex
- `assets/hero.svg` — 1200×400 banner, blueprint grid, particles, avatar ring
- `assets/boot.svg` — 1200×500 boot sequence
- `assets/dashboard.svg` — 1200×360 mission control
- `assets/terminal.svg` — 1200×420 terminal with easter egg

**Added — System**
- `themes/spec-os.json` — portable design tokens
- `.github/workflows/spec-check.yml` — palette + budget + link validation

**Locked 🔒**
- Core palette: `#0D1117` `#161B22` `#A855F7` `#7C3AED` `#C084FC` `#22C55E` `#F8FAFC`
- Product string: `SPEC OS v1.0`
- Tagline loop order and timing
- Easter egg copy

---

## [Unreleased]

### Planned — v1.1
- Alternate accent theme packs in `themes/` (dark-only)
- Live metrics wiring for the dashboard
- Second easter egg

### Planned — v1.2
- SPEC OS web port (Next.js) with a real interactive terminal

---

## Versioning Policy

| Bump | Trigger |
|------|---------|
| **MAJOR** | Palette, identity or branding rules change |
| **MINOR** | New spec approved or new asset shipped |
| **PATCH** | Copy fixes, size optimization, doc corrections |

> One sprint = one version bump = one entry. No silent changes.

---

<div align="center">

[← Back to README](./README.md)

</div>
