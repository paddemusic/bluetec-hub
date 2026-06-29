# BlueTec — Branding hub asset pack

Everything needed to build the self-serve brand hub. Source of truth for rules: the
*BlueTec Wordmark & Lockup System* document. One brand blue: **#0077C8** (Pantone 3005 C).

```
branding-hub-assets/
├── logo/
│   ├── emblem/        the b mark only
│   │   ├── svg/       blue · navy · white · black   (vector masters)
│   │   └── png/       each colour @ 1024 / 512 / 256 / 128  (transparent)
│   ├── wordmark/      "BlueTec" set in BlueTec Geometric ExtraBold
│   │   ├── svg/       navy · white · blue · black   (outlined paths — no font needed)
│   │   └── png/       navy · white · black · blue   (transparent)
│   └── lockup/        emblem + wordmark
│       ├── svg/       horizontal & stacked × on-light / on-dark / mono-white / mono-navy,
│       │              plus tagline versions   (all outlined paths — no font needed)
│       ├── png/       horizontal & stacked × on-light / on-dark / mono-white / mono-navy,
│       │              plus tagline versions   (transparent)
│       └── jpg/       horizontal on white / navy / blue   (solid ground)
├── app-icons/         filled rounded tile @ 1024 (stores) + 180 (apple-touch)
├── favicon/           transparent emblem @ 512 / 180 / 32 / 16
├── fonts/             BlueTecGeometric · .woff (9, ≈56% size) + .ttf (9) + fonts.css (@font-face ready)
├── swatches/          BlueTec.ase (Adobe) · BlueTec.gpl (GIMP) · BlueTec-Office-Theme.thmx · install guide
├── tokens/            colors.json · colors.css   (for the hub build)
├── brand-rules/       color-usage.md   (palette + contrast pairings + do/don't)
└── email-signature/   signature-template.html   (editable, email-safe)
```

## Choosing a format
- **SVG** — the master for logo/wordmark/lockup. Infinitely scalable; use on the web and in vector tools. Wordmark/lockup SVGs are **outlined paths** (text already converted to vector), so they render identically in every viewer and print tool with no font installed.
- **PNG** — transparent raster. Use in PowerPoint/Word/Keynote, on photos, anywhere needing transparency. Pick the colour variant to suit the surface (navy/black on light, white on dark).
- **JPG** — only where transparency isn't possible; always on a solid brand ground.

## Surface → colour
- Light surface → navy wordmark (`on-light`) · Dark surface → white wordmark (`on-dark`)
- `mono-white` (all white) and `mono-navy` (all navy) are for photos / single-colour print.
- App icons are a **filled tile** — never the transparent emblem (stores reject transparency).

## Type
- Family: **BlueTec Geometric**, nine weights (Thin 100 → Black 900). Wordmark locks to **ExtraBold (800)**.
- Web: link `fonts/fonts.css` — it serves **WOFF** (≈56% of TTF) with a TTF fallback. WOFF2 (another ~30% smaller) can be generated locally; see the note in `fonts.css`.

## For the presentation templates
Drop the transparent PNG or SVG lockups into any frame (16:9, 9:16, 4:5) — they scale without
distortion. Use `on-dark` / `mono-white` on dark slides, `on-light` on white slides. Keep clear
space around the lockup equal to the emblem height.

## Not included (optional, generate locally)
- **WOFF2** web fonts — ~30% smaller than the included WOFF, but needs Brotli; one-line `ttf2woff2` command in `fonts.css`.
