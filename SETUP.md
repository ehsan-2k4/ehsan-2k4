# 🛠️ SETUP — Deploying SPEC OS to your GitHub profile

Everything is built. This is the 5-minute deploy.

---

## 1. Create the profile repo

Your GitHub profile README lives in a repo **named exactly like your username**:

```
github.com/ehsah-2k4/ehsah-2k4
```

- New repository → name: `ehsah-2k4`
- ✅ Public · ✅ Add a README
- Create.

> ⚠️ Repo name must match your handle **character for character**, or the README won't show on your profile.

---

## 2. Push the files

```bash
git clone https://github.com/ehsah-2k4/ehsah-2k4.git
cd ehsah-2k4

# copy everything from spec-os/ into this folder
# (README.md, all *.md, assets/, themes/, .github/)

git add .
git commit -m "feat: SPEC OS v1.0 — spec-driven profile system"
git push origin main
```

---

## 3. Two things to personalize

### a) Your real photo in the hero

`assets/hero.svg` currently uses the initials **ME** as an avatar placeholder.
To use your photo:

1. Add your square photo as `assets/avatar.jpg` (recommended 400×400).
2. In `assets/hero.svg`, find this block:

```xml
<g clip-path="url(#hero-avatar-clip)">
  <rect x="897" y="112" width="176" height="176" fill="#1C2128"/>
  <text ...>ME</text>
</g>
```

3. Replace it with:

```xml
<g clip-path="url(#hero-avatar-clip)">
  <image href="avatar.jpg" x="897" y="112" width="176" height="176"
         preserveAspectRatio="xMidYMid slice"/>
</g>
```

> GitHub allows **relative** image refs inside SVG in the same repo. Keep `avatar.jpg`
> in `assets/` next to `hero.svg`. If it doesn't render, base64-embed it instead:
> `href="data:image/jpeg;base64,...."`

### b) Your links

In `README.md`, fill in the LinkedIn and email badge URLs:

```markdown
[![LinkedIn](...)](https://linkedin.com/in/YOUR-HANDLE)
[![Email](...)](mailto:you@example.com)
```

Also confirm the featured repo URL: `https://github.com/ehsah-2k4/portfolio`.

---

## 4. Verify

| Check | How |
|-------|-----|
| Hero animates | Open your profile — the tagline should cycle every 4s |
| Stats load | github-readme-stats needs a few seconds on first render |
| Easter egg | Click the `unlock` details block |
| CI passes | Actions tab → `spec-check` should be green |

> **Note on animation:** GitHub sanitizes SVG but **allows inline CSS animations** in
> SVGs referenced via `<img>` in Markdown. All assets here are built for that path.
> If a viewer strips animation, the reduced-motion fallback shows a clean static frame.

---

## 5. Local preview

Open `preview.html` in any browser to see every asset animating together before you push.

```bash
python3 -m http.server 8080
# → http://localhost:8080/preview.html
```

---

## File map

```
ehsah-2k4/
├── README.md              ← profile front page
├── DESIGN_SYSTEM.md       ← SPEC-000, the DNA
├── ABOUT.md  MANIFESTO.md  SPECS.md
├── PROJECTS.md  ROADMAP.md  COMMANDS.md  CHANGELOG.md
├── SETUP.md               ← this file (optional to keep)
├── preview.html           ← local asset preview (optional to keep)
├── assets/
│   ├── logo.svg  hero.svg  boot.svg  dashboard.svg  terminal.svg
│   └── icons/  (10 line icons)
├── themes/
│   ├── spec-os.json       ← portable design tokens
│   └── spec-os.css        ← drop-in CSS variables
└── .github/workflows/
    └── spec-check.yml     ← palette + budget + a11y + link CI
```

---

`🟢 SYSTEM ONLINE` · SPEC OS v1.0
