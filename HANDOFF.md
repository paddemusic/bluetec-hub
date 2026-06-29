# BlueTec Brand Hub — Handoff

**Sist oppdatert:** 2026-06-25
**Status:** Ferdig bygget, i aktiv iterasjon

---

## Hva er dette

En intern, selvbetjent merkevare-hub for BlueTec AS. Ansatte henter logoer i riktig format, kopierer fargekoder, laster ned fonter og fargeprofiler, og genererer e-postsignatur — uten å måtte spørre marketing.

Bygget som én statisk HTML-side med vanilla JS. Ingen rammeverk, ingen byggsteg, ingen avhengigheter utenom fflate (CDN, for multi-select zip).

---

## Filstruktur

```
/Users/padde/Documents/Bluetec/marketing-hub/
├── CLAUDE.md                    — prosjektkontekst for Claude
├── HANDOFF.md                   — denne filen
├── index.html                   — hele huben (én fil)
├── web-motion-guidelines.html   — separat side for Web & Motion-retningslinjer
├── branding-hub-assets/         — alle merkevareressurser
│   ├── logo/
│   │   ├── emblem/svg+png/      — 4 farger × 4 størrelser (128/256/512/1024)
│   │   ├── wordmark/svg+png/    — 4 farger
│   │   └── lockup/svg+png+jpg/  — horizontal + stacked × alle varianter
│   ├── fonts/                   — BlueTec Geometric, 9 vekter (.woff + .ttf)
│   │   └── fonts.css            — @font-face stack, last inn via link-tag
│   ├── favicon/                 — 16/32/180/512px
│   ├── app-icons/               — 180 + 1024px (fylt tile, ikke transparent)
│   ├── swatches/                — BlueTec.ase / .gpl / .thmx
│   ├── tokens/                  — colors.json + colors.css
│   ├── brand-rules/             — color-usage.md
│   ├── email-signature/         — signature-template.html (kilde for byggeren)
│   └── Bluetec.zip              — alle logoer samlet, brukes av "Last ned alle"
```

Originalkilde for assets:
`/Users/padde/Downloads/Bluetec_onedrive/Bluetec_Rebrand/Bluetec_rebrand_final/branding-hub-assets/`

---

## Kjøre lokalt

```bash
cd "/Users/padde/Documents/Bluetec/marketing-hub"
python3 -m http.server 3437
# Åpne: http://localhost:3437
```

Port 3437 er valgt for å ikke kollidere med andre prosjekter:
- 3434 = nettsiden (/website/)
- 3435 = presentasjonen (/bluetec-presentation/)
- 3436 = logo-exploration (/brand-audit/logo-exploration/)
- **3437 = marketing hub (dette prosjektet)**

---

## Hva er bygget (seksjon for seksjon)

### 1. Overview / hero
Marineblå bakgrunn. Emblem + "Brand Hub"-tittel. Snarveier til alle seksjoner.

### 2. Logoer og lockups
- Bakgrunnsvelger: Lys / Mørk / Blå — bytter preview-bakgrunn på alle kort simultant
- **Pinnede kort:** Navy-, Sort- og Hvit-varianter av emblem og ordmerke er pinnet til sin naturlige bakgrunn med `data-surface-fixed`-attributt, slik at de aldri blir usynlige ved overflatebytte. Blå-variantene følger det globale byttet fritt.
- Emblem: blå / navy / hvit / sort — SVG + PNG 1024/512/256/128 per variant
- Ordmerke: blå / navy / hvit / sort — SVG + PNG
- Horizontal lockup: lys / mørk / + tagline / mono navy / mono hvit — SVG + PNG + JPG
- Stacked lockup: samme matrise
- Per kort: nedlastingsknapper (SVG, PNG-størrelser, evt. JPG) + "Kopier SVG"-knapp
- Multi-select tray: kryss av på flere kort → flytende tray → "Last ned som ZIP" via fflate (CDN). Fallback: sekvensiell nedlasting hvis offline.
- "Last ned alle logoer (ZIP)" → lenker direkte til Bluetec.zip

### 3. Farger
- 7 fargeswatch-kort: Brand Blue, Dark Navy, White, Ink, Muted, Hairline, Paper
- Klikk på kort = kopier HEX til utklippstavle, toast-bekreftelse
- Viser HEX / RGB / CMYK (Brand Blue viser også Pantone 3005 C)
- Live kontrast-eksempler + ett tydelig merket FEIL-eksempel

### 4. Typografi
- 9-vekts ramp (Thin → Black) med live tekst i BlueTec Geometric
- Live typeskala: Display/H1 → Caption
- "Last ned fonter (ZIP)" → Bluetec.zip

### 5. E-postsignatur
- Live bygger: skjema til venstre, forhåndsvisning til høyre
- Påkrevd: Fullt navn, Stilling, E-post
- Valgfritt (avmerkingsbokser): Telefon, Avdeling, Kontorlokasjon, LinkedIn
- Egendefinerte felt: label + verdi, ubegrenset antall
- "Kopier signatur (HTML)" → ClipboardItem med text/html type → limer direkte inn som formatert signatur i Outlook/Gmail (ikke HTML-kode)
- "Last ned .htm" → laster ned som fil

**Signaturen bruker:**
- Base64-kodet PNG-emblem (128px, blå variant) — embedded i HTML, ingen hosting nødvendig, virker i Outlook
- Arial (e-postklienter støtter ikke egendefinerte fonter)
- 2-rad tabell-layout: identitetsrad (logo + navn/rolle) + kontaktrad (separert med padding, ikke linje)
- Kontaktinfo grupperes: e-post · telefon på én linje, avdeling · lokasjon på én linje, nettside · LinkedIn på én linje

**OBS — pågående designarbeid:**
Patrick er ikke fornøyd med gjeldende signaturdesign (horisontalt blå separatorlinje skaper ubalanse). Anbefalt neste iterasjon: tilbake til vertikal blå stripe (border-left på tekstkolonnen, full høyde), med romslig spacing (ikke linje) som skiller identitet fra kontaktinfo. Se "Kjente begrensninger" under.

### 6. Fargeprofiler og nedlastinger
- BlueTec.ase / .gpl / .thmx — med installasjonsanvisning per filtype
- colors.json + colors.css — maskinlesbare tokens

### 7. Merkevareregler
- Gjør / Ikke gjør — to kolonner med sjekkliste-stil
- Kontrastpar-blokk på navy bakgrunn

### 8. Web & Motion Guidelines (separat side)
- Ligger i `web-motion-guidelines.html` ved siden av `index.html`
- Lenkes fra sidenav i huben under "Retningslinjer" → "Web & Motion ↗"
- Nav-lenken har klassen `nav-page` (ikke `sidenav__link`) og er **ekskludert fra scroll-spy**
- Siden har "‹ Tilbake til Brand Hub"-lenke som peker til `index.html`
- Innhold: bevegelsesprinsipper, CSS-tokens, interaksjonsregler — ut av scope for huben, men lenket herfra

---

## Viktige tekniske detaljer

### Scroll-spy
Kun seksjoner i `index.html` observeres: `['overview','logos','colours','typography','signature','swatches','rules']`.
Scroll-spy bruker `.sidenav__link[href="#${id}"]` — kan aldri treffe `.nav-page`-lenken.

### Surface toggle og pinnede kort
```javascript
function setSurface(key, btn) {
  // ...
  document.querySelectorAll('.logo-surface').forEach(el => {
    const fixed = el.getAttribute('data-surface-fixed');
    if (!fixed) el.style.background = bg;  // pinnede kort hoppes over
  });
}
```
Kort med `data-surface-fixed="light"` holder alltid `#F4F4F2`.
Kort med `data-surface-fixed="dark"` holder alltid `#0A1628`.

### SVG-kopiering
`copySVG()` bruker `fetch()` — krever HTTP-server. Virker ikke ved `file://`-åpning.

### Signatur — ClipboardItem
```javascript
const blob = new Blob([sigHtml], { type: 'text/html' });
await navigator.clipboard.write([new ClipboardItem({ 'text/html': blob })]);
```
Faller tilbake til `writeText()` på eldre nettlesere.

---

## Ikke-omsettelige regler (fra build brief §2)

- **Én blå:** `#0077C8` — legacy `#0075C9` er pensjonert
- **Kun BlueTec Geometric** — via `branding-hub-assets/fonts/fonts.css`
- **Emblemets hvite flater er negativrom** — aldri hvit fill
- **Ordmerke er én ensfarget farge** — navy på lys, hvit på mørk/blå
- **Kontrastpar:** papir/hvit→`#15151A`, navy→hvit, blå→hvit

---

## Fargetokens

```css
--bt-blue:#0077C8;
--bt-navy:#0A1628;
--bt-white:#FFFFFF;
--bt-ink:#15151A;
--bt-muted:#86867F;
--bt-hairline:#E6E6E1;
--bt-paper:#F4F4F2;
```

---

## Kjente begrensninger og potensielle neste steg

| Emne | Status | Notat |
|---|---|---|
| Signaturdesign — vertikal stripe | **Ikke implementert ennå** | Anbefalt neste iterasjon: fjern horisontal blå linje, bruk `border-left:3px solid #0077C8` på tekstkolonnen (full høyde), stor spacing mellom rolle og kontaktinfo |
| Multi-select zip | Fungerer med CDN (fflate). Offline: sekvensiell fallback | Kan bundel fflate lokalt |
| Kopier SVG | Krever HTTP-server (ikke file://) | Bruk `python3 -m http.server` |
| Dark mode toggle | Ikke bygget (brief: optional) | Kan legges til med `prefers-color-scheme` |
| App icons-seksjon | Ikke eksponert i UI — finnes i `assets/app-icons/` | Kan legges til under Logoer |
| Hosting | Lokal kun per nå | Vercel, Netlify eller SharePoint |

---

## Endringslogg (denne sessionen — 2026-06-25)

- **Web & Motion Guidelines** (`web-motion-guidelines.html`) lagt til og lenket fra sidenav
- **Surface toggle** fikset: navy, hvit og sort logo-varianter er nå pinnet til riktig bakgrunn
- **PNG-størrelser** utvidet: alle emblem-kort viser nå 1024 / 512 / 256 / 128
- **Signaturlogo** erstattet: SVG → base64 PNG (virker i Outlook og ved copy-paste)
- **Kopier signatur** oppgradert: `ClipboardItem({text/html})` → limer inn som formatert HTML
- **Signaturlayout** redesignet: 2-rad tabell (identitetsrad + kontaktrad med horisontal separator)
- **Kontaktinfo gruppert**: maks 3 standardlinjer uavhengig av antall felt som er valgt

---

## Separasjon fra rebranding-prosjektet

Dette prosjektet er **bevisst atskilt** fra `/Users/padde/Documents/Bluetec/bluetec-project 3/`.

- Merkevarereglene er definert i: `bluetec-project 3/.claude/CLAUDE.md`
- Huben **implementerer** disse reglene — definerer dem ikke
- Aldri kryss innhold mellom mappene

---

## Build brief (kilde)

`/Users/padde/Downloads/Bluetec_onedrive/Bluetec_Rebrand/Claude_instructions_hub_build/BlueTec Brand Hub - Build Brief.md`
