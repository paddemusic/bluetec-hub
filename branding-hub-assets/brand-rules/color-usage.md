# BlueTec — Colour usage

Source of truth: **Pantone 3005 C**. Everything converts from it. There is **one** brand blue: `#0077C8` (the legacy `#0075C9` is retired).

## The palette

| Token | Hex | RGB | Use |
|---|---|---|---|
| **Brand Blue** | `#0077C8` | 0 119 200 | Primary. Emblem, links, key accents. Pantone 3005 C · CMYK 100/31/0/0 |
| **Dark Navy** | `#0A1628` | 10 22 40 | Dark grounds, footers |
| **White** | `#FFFFFF` | 255 255 255 | Light grounds, reversed marks |
| Ink | `#15151A` | 21 21 26 | Body text |
| Muted | `#86867F` | 134 134 127 | Captions, secondary text |
| Hairline | `#E6E6E1` | 230 230 225 | Rules, light fills |
| Paper | `#F4F4F2` | 244 244 242 | Soft off-white background |
| Foil *(folie)* | `XE6080` | — | Signage / vehicle wrap. Match a physical sample; never approximate on screen. |

## Type-on-surface pairings (the contrast rule)

- **White background → near-black type** (`#15151A`).
- **Navy background (`#0A1628`) → white type** (`#FFFFFF`).
- **Blue background (`#0077C8`) → white type** (`#FFFFFF`).

The emblem carries the blue; the wordmark stays a single solid colour (navy on light, white on dark/blue). Never split the wordmark into two tones, never tint it outside this palette.

## Do / Don't

**Do**
- Keep the emblem holes transparent — the white in the `b` is negative space, not a fill.
- Reverse to white on dark and on blue.
- Hold clear space equal to the emblem height around any lockup.

**Don't**
- Don't put the emblem on a grey or opaque box.
- Don't stretch, rotate, recolour, or add effects to the mark.
- Don't introduce any colour outside the locked palette (no neon teal).
- Don't set the wordmark in any font other than **BlueTec Geometric**.
