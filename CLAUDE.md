# BlueTec Marketing Hub — Project Context

## What this project is

An internal web platform where BlueTec employees find, download, and use brand assets.
Single-page static HTML (index.html) + one companion page (web-motion-guidelines.html).
Served locally at localhost:3437 via `python3 -m http.server 3437`.

This is a **separate build** from the rebranding work in `/bluetec-project 3/`.

---

## What this project is NOT

This project does not define brand rules. It implements them.
All brand decisions (colors, fonts, copy rules, logo, taglines) are locked in:
`/Users/padde/Documents/Bluetec/bluetec-project 3/.claude/CLAUDE.md`

Do not redefine brand rules here. Do not duplicate them. Reference the source.

---

## Brand rules summary (read-only, from source)

- Primary blue: `#0077C8` (Pantone 3005 C) — the ONLY brand blue, `#0075C9` is retired
- Dark navy: `#0A1628`
- Font: BlueTec Geometric exclusively — loaded via `branding-hub-assets/fonts/fonts.css`
- No emojis. No dark nav. No neon teal.
- No unverified % claims in copy.
- Emblem white areas = negative space, never white fill, never rotated or recoloured.
- Wordmark = one solid colour: navy on light, white on dark/blue.

---

## Current build state (as of 2026-06-25)

All 7 sections built and working:
1. Overview / hero
2. Logoer & lockups — surface toggle, PNG 1024/512/256/128, multi-select zip tray
3. Farger — click-to-copy HEX, contrast examples
4. Typografi — weight ramp, type scale, font download
5. E-postsignatur — live builder, base64 PNG logo, ClipboardItem HTML copy
6. Fargeprofiler — .ase / .gpl / .thmx / tokens download
7. Merkevareregler — do/don't list, contrast pairings

Companion page: `web-motion-guidelines.html` (linked from sidenav, not merged into hub).

---

## Active design decision — email signature

The signature is working (logo copies correctly to Outlook, ClipboardItem paste works),
but Patrick is not satisfied with the visual balance of the current 2-row layout.

**Current layout:** identity row (logo + name/role) | blue horizontal separator | contact row.
**Problem:** horizontal separator feels heavy, logo disconnects from contact info.

**Recommended next iteration (not yet built):**
- Return to single-row table: logo left, all text right
- Blue left border (`border-left: 3px solid #0077C8`) on the text cell — spans full height
- Large spacing gap (~16px) between role and first contact line — no separator line
- This is the "vertical stripe" approach that feels premium and is brand-consistent

Do NOT implement this without confirming with Patrick first.

---

## Key technical rules

- **SVG copy (`copySVG`)** uses `fetch()` — only works over HTTP, not `file://`.
- **Surface toggle** respects `data-surface-fixed` on logo preview cards:
  - `"light"` = stays at `#F4F4F2` (navy, black variants)
  - `"dark"` = stays at `#0A1628` (white variants)
  - Cards without the attribute follow the global toggle.
- **Scroll-spy** only watches `.sidenav__link[href="#..."]` — the Web & Motion nav link
  (class `nav-page`) is intentionally excluded.
- **ClipboardItem** for signature copy falls back to `writeText()` on older browsers.
- **Signature logo** is a base64-encoded 128px PNG (blue emblem) — no external hosting needed.

---

## File structure

```
marketing-hub/
├── CLAUDE.md                   — this file
├── HANDOFF.md                  — full technical handoff + changelog
├── index.html                  — entire hub (one file, ~1100 lines)
├── web-motion-guidelines.html  — companion page, separate from hub
├── branding-hub-assets/        — all brand assets served for download
│   ├── logo/emblem/            — SVG + PNG (4 colours × 4 sizes)
│   ├── logo/wordmark/          — SVG + PNG (4 colours)
│   ├── logo/lockup/            — SVG + PNG + JPG (all variants)
│   ├── fonts/                  — BlueTec Geometric 9 weights + fonts.css
│   ├── app-icons/              — 180px + 1024px
│   ├── favicon/                — 16/32/180/512px
│   ├── swatches/               — .ase / .gpl / .thmx
│   ├── tokens/                 — colors.json + colors.css
│   ├── brand-rules/            — color-usage.md
│   ├── email-signature/        — signature-template.html
│   └── Bluetec.zip             — all logos bundled (used by "Last ned alle")
└── src/ tools/ assets/         — reserved, currently empty
```

---

## Build brief (source of truth for all specs)

`/Users/padde/Downloads/Bluetec_onedrive/Bluetec_Rebrand/Claude_instructions_hub_build/BlueTec Brand Hub - Build Brief.md`
