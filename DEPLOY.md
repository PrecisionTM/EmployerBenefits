# pdf-export — Deployment Checklist

## What This Folder Is
A self-contained, CDN-free version of the Precision Telemed Tirzepatide Employer One-Pager,
built as a responsive web page for Vercel deployment. Content flows naturally — no fixed
page heights or print constraints. Share the Vercel URL directly with employers and brokers.

---

## File Map

```
pdf-export/
├─ index.html                      ← Entry point (all CSS inline, no CDN)
├─ vercel.json                     ← { "cleanUrls": true }
├─ DEPLOY.md                       ← This file
├─ download                        ← Blank file (repo convention)
├─ images/
│  ├─ monj-logo.png                ← Monj Health circular logo
│  ├─ fontawesome.css              ← Font Awesome 6.5.1 CSS (local @font-face → ../webfonts/)
│  └─ google-fonts-local.css       ← Inter + Playfair Display @font-face (local → ../fonts/)
├─ fonts/
│  ├─ inter-300.ttf  inter-400.ttf  inter-500.ttf
│  ├─ inter-600.ttf  inter-700.ttf  inter-800.ttf
│  ├─ playfair-400.ttf  playfair-400-italic.ttf
│  ├─ playfair-500.ttf  playfair-500-italic.ttf
│  ├─ playfair-600.ttf  playfair-700.ttf
└─ webfonts/
   ├─ fa-solid-900.woff2
   ├─ fa-regular-400.woff2
   ├─ fa-brands-400.woff2
   └─ fa-v4compatibility.woff2
```

---

## Pre-Deploy Checklist

- [ ] `index.html` opens in a browser tab — both page cards render fully with no overflow
- [ ] Monj logo renders in the header and in both program-card Monj badges
- [ ] Font Awesome icons visible (checkmarks, flag, route, piggy-bank, etc.)
- [ ] Inter and Playfair Display fonts load correctly
- [ ] No CDN requests in DevTools Network tab — all assets served locally from `images/`, `fonts/`, `webfonts/`
- [ ] Page is responsive — stacks correctly on mobile (≤ 640px)
- [ ] `vercel.json` present with `{ "cleanUrls": true }` — no rewrites

---

## Vercel Deployment Steps

1. Commit the entire `pdf-export/` folder to your GitHub repo.
2. In Vercel → **Add New Project** → import the repo.
3. Set **Root Directory** to `pdf-export` so Vercel serves `index.html` at `/`.
4. Deploy — share the live URL with employers and brokers.

> **Important:** Set Root Directory to `pdf-export`, not the repo root.
> Otherwise Vercel will not find `index.html` at the right path.

---

## Conventions Compliance

| Rule | Status |
|---|---|
| No `vh`/`dvh`/`svh` in section heights | ✅ All heights are content-driven (`auto`) |
| No CDN dependencies | ✅ All fonts and icons are local |
| Relative image paths (no leading `/`) | ✅ `images/monj-logo.png` |
| Images folder named `images/` | ✅ |
| `vercel.json` with `cleanUrls: true`, no rewrites | ✅ |
| Single `index.html` entry point | ✅ |
| Semantic HTML (`article`, `header`, `section`, `footer`) | ✅ |
| Responsive layout with `clamp()` and media queries | ✅ |
| No stale files (`README.txt`, old HTML variants) | ✅ |
| No `public/` folder, no build artifacts | ✅ |

---

*Last updated: May 2026*
