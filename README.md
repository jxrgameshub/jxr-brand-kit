# JXR Gaming — Brand Kit

Hand-off bundle for marketing, design, video and streamer partnerships.
Read [`BRAND-GUIDELINES.md`](BRAND-GUIDELINES.md) first — this folder is the *assets*; the guide is
the *rules*.

**Version:** 1.0 · **Source:** verified against `src/app/globals.css` and the live UI

---

## What's in here

```
brand-kit/
├── README.md                          ← you are here
├── BRAND-GUIDELINES.md                ← the rules (13 sections)
├── MANIFEST.txt                       ← file list + checksums
│
├── 01-logo/                           ← primary mascot + token mark
├── 02-colour/                         ← palette.css + palette.json
├── 03-typography/                     ← CourbeSans — reference only, files on request
├── 04-social-templates/               ← editable OG card
├── 05-overlays/                       ← Kick.com overlay suite (6 SVGs)
├── 06-badges/                         ← 14 VIP tier badges
├── 07-stickers/                       ← Telegram sticker pack
└── 08-campaign/                       ← banners and hero art
```

---

## Start here: the 60-second version

1. **Two fonts only.** CourbeSans 400/700 — see [`03-typography/README.md`](03-typography/README.md);
   the binaries are licensed and are **not** in this repo. A heavy system display stack is used for
   the wordmark and big numbers.
2. **Gold is identity, orange is action.** Gold `#f0a342` for brand identity. Orange `#f97316` for
   calls to action. Never gradient one into the other.
3. **Sharp corners.** 3px buttons/chips, 2px small items, 10px cards. No pills.
4. **One domain.** `juicer.games`. Never `jxr.gg` — it is a retired defect (guide §1.1).
5. **Overlays are CourbeSans.** Never the display stack — it renders differently per OS.
6. **18+ and responsible gaming** on every ad and every full-frame scene.

---

## 01-logo — the mascot and token mark

| File | Size | Use |
|---|---|---|
| `juicebox-sticker-master.webp` | 512×512 | **Source of truth.** Never upscale beyond this |
| `juicebox-sticker-512.png` | 512×512 | Print, large digital |
| `juicebox-sticker-256.png` | 256×256 | App icon, OG cards |
| `juicebox-sticker-128.png` | 128×128 | Overlays, share cards |
| `juicebox-sticker-64.png` | 64×64 | Small UI |
| `juicebox-sticker-32.png` | 32×32 | Favicon |
| `jxr-token-master.png` | 1024×1024 | Token mark source |
| `jxr-token-192.png` | 192×192 | OG renderer size |
| `jxr-token-32.png` | 32×32 | Chip icon |

The PNGs were exported from the WebP master at 512px. **Do not upscale** — the master is 512×512, so
anything larger will soften.

**Rules:** clear space = 25% of width on all sides. Never crop, stretch, recolour, outline, or place
on a photo without a scrim. The token mark is not a logo and never replaces the mascot in a lockup.

---

## 02-colour — importable palette

| File | Use |
|---|---|
| `palette.css` | Drop into any web asset; CSS custom properties |
| `palette.json` | Design-token JSON for Figma plugins / Style Dictionary / scripting |

Covers core semantic tokens, the 12-step gold ramp, brand tokens, v2.0 orange, deep surfaces, text,
status, result pairs, chart series, 13 game accents, 14 VIP tier colours, radii, shadows, type scale
and font stacks.

Every value is a verified extraction from `src/app/globals.css`. **Do not add colours to these
files.** If a job needs something not present, flag it — do not eyeball a new shade.

---

## 03-typography — reference only

**The font files are not distributed in this repository.** Courbe Sans is a licensed commercial
typeface (trademark of Loukas Nicolaou) and this repo is public — shipping the OTF/TTF here would be
redistribution.

[`03-typography/README.md`](03-typography/README.md) explains the licence position and how to request
access for platform use. Access is granted per project, for use on the JXR Gaming platform and its
sanctioned channels — not for redistribution, resale, or upload to public font libraries and CDNs.

Only **400** and **700** exist. There is no 500, no 600, no 900 — a design tool will synthesise them
and it will look wrong. Increase size or use 700 instead.

Until access is granted, use the documented fallback stack (`'CourbeSans', 'Inter', -apple-system,
BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif`) and mark drafts as drafts.

Display stack (wordmark + big numbers only):

```
'Arial Black', 'Impact', 'Franklin Gothic Heavy', 'Haettenschweiler', system-ui, sans-serif
```

Because that is a **system** stack, it renders differently on macOS, Windows and Linux. **Never use it
on an overlay or in video**, where you need predictable metrics.

---

## 04-social-templates

| File | Canvas | Use |
|---|---|---|
| `og-bet-card-1200x630.svg` | 1200×630 | Bet share / Open Graph card |

Editable SVG. Replace five placeholders: `[PLAYER]`, `[GAME]`, `[RESULT]`, `[PAYOUT]`, `[BET]`.
Spec in guide §7.1.

Win = `#22c55e`. Loss = `#ff4d6a`. Result label is a multiplier (`2.50x`), `WIN`, or `BUST`.

---

## 05-overlays — Kick.com streamer suite

Six editable SVGs, built to the specification in guide §8. Nothing in this folder existed before this
kit — it is the sourced implementation of that spec.

| File | Canvas | Placement (1920×1080) |
|---|---|---|
| `code-bug-300x72.svg` | 300×72 | x=40, y=40 — **always-on** |
| `code-card-420x140.svg` | 420×140 | x=40, y=780 — primary lower third |
| `full-frame-1920x1080.svg` | 1920×1080 | opaque starting / BRB / ending |
| `alert-720x200.svg` | 720×200 | x=40, y=160 |
| `win-stamp-900x260.svg` | 900×260 | centred, y=300 |
| *(webcam frame)* | 480×360 | see guide §8.5 F for the spec |

**Replace `[CODE]` in every file.** Code rules: 4–16 characters, `A-Z 0-9 - _`, uppercase, no
leading/trailing separator, and not one of the reserved words listed in guide §8.4.

**Placement constraints — non-negotiable:**

- Keep the **bottom 120px** clear (player controls).
- Keep the **right 340px** clear (docked chat).
- Keep the **top 80px** clear (stream chrome).
- Panel fills are 88–92% opacity so text survives bright gameplay.

**Font:** all overlay text must be CourbeSans. The display stack is banned here.

**Compliance:** the full-frame scene carries the mandated 18+ / responsible-gaming line. Do not
delete it.

**Naming when you export:**
`jxr-kick_{variant}_{scene}_{w}x{h}_{rev}.{ext}` — e.g. `jxr-kick_codecard_ingame_420x140_v1.png`.

---

## 06-badges — VIP tier artwork

All 14 tiers. Native aspect ratio only — never recolour, never outline, never reorder the ladder.

| Tier | File | Tier | File |
|---|---|---|---|
| Wood | `wood-log-badge.png` | Ruby | `ruby-badge.png` |
| Bronze | `bronze-badge.png` | Diamond | `diamond-badge.png` |
| Silver | `silver-badge.png` | Opal | `opal-badge.png` |
| Gold | `gold-badge.png` | Dragon | `dragon-badge.png` |
| Platinum | `plat-badge.png` | Mythic | `mythic-badge.png` |
| Jade | `jade-badge.png` | Dark | `dark-badge.png` |
| Sapphire | `sapphire-badge.png` | Legend | `legend-badge.png` |

Two filenames are irregular by design: **Wood** is `wood-log-badge.png` and **Platinum** is
`plat-badge.png`. Do not "tidy" them — code depends on these exact names.

Tier colours are in `02-colour/palette.css` as `--vip-*`. Gold and Mythic intentionally share
`#ffd700`; distinguish them by artwork, never by recolouring.

---

## 07-stickers — Telegram pack

| File | Detail |
|---|---|
| `juicebox-100.png` | 100×100 static |
| `juicebox-512.png` | 512×512 static |
| `juicebox-floating-100.webm` | Animated, 100px |
| `juicebox-floating-512.webm` | Animated, 512px |
| `README.md` | Original pack notes |

---

## 08-campaign — existing campaign art

| File | Detail |
|---|---|
| `juicer-banner.jpg` | Wide banner |
| `tails-jxr.jpeg` | Campaign image |
| `juicer-hero-banner.png` | Hero banner |

These are existing assets, included for convenience. They predate this kit; check them against the
guide before reuse.

> **Not included:** `public/images/jxr.gg_r_xxxxxx.png`. Its filename carries the retired `jxr.gg`
> domain and it must not be used in new work (guide §1.1).

---

## What is deliberately NOT in this kit

- **The CourbeSans font binaries.** Licensed commercial type, not redistributable. Referenced in
  [`03-typography/README.md`](03-typography/README.md) and available on request for platform use.

- **The 65 UI line icons.** They are internally inconsistent — 43 hard-code an unratified `#ff8647`,
  18 use `currentColor`, 3 use `#f97316` (guide §4.6). Do not lift them into marketing. Commission
  the specific glyph, or reference the live UI.
- **The design-tool native files.** No Figma / Sketch / Affinity source exists in the repo. The SVGs
  here are the editable masters; import them.
- **Social handles or contact details.** None exist in the codebase, so none are invented here.
- **Any RTP, win-rate or payout percentage.** Take numbers from the live UI, never recompute them
  (guide §9).

---

## Before anything ships

The full checklist is guide §12. The four that get missed:

- [ ] No `jxr.gg` anywhere — `juicer.games` only
- [ ] No paid targeting into the United States (restricted jurisdiction, guide §11.1)
- [ ] Code legible at 50% of delivered size
- [ ] 18+ / responsible-gaming line present
