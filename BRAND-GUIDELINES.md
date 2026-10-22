# JXR Gaming — Brand Guidelines & Asset Production Blueprint

**Version:** 1.0
**Audience:** Marketing, design, video production, and streamer-partnership teams
**Status:** Authoritative for all off-platform assets

---

## 0. How to use this document

This is a **production manual**, not a mood board. Every colour, font, size, radius, and file path in
this document was read out of the live application source. Section 13 lists the exact file and line
each value came from so you can re-verify anything here.

Rules of engagement:

1. **Never sample colours from a screenshot.** Screenshots are compressed and colour-managed by
   whatever tool produced them. Copy the hex values from Section 2.
2. **Never invent a shade.** If a job needs a colour that is not in Section 2, use the nearest token
   and flag it to brand owner for a decision. Do not "eyeball" a new orange.
3. **Never invent a font.** There are exactly two brand typefaces (Section 3). A third typeface is a
   brand breach, not a creative choice.
4. **Open platform gaps are marked.** Anything labelled `⚠ OPEN` is a genuine gap in the shipped
   product — a decision still needs to be made before that asset type goes into production. Do not
   quietly fill the gap.
5. **Overlays are new work.** Section 8 specifies a streamer overlay suite that **does not currently
   exist in the codebase**. It is a specification to be built, not a description of existing assets.

---

## 1. Brand architecture and naming

The brand operates at three levels. Using the wrong level in the wrong place is the single most
common error, so the ladder is fixed:

| Level | Name | Where it appears |
|---|---|---|
| House / platform | **JXR Gaming** | Page title, token metadata, legal and compliance copy, press |
| Product wordmark | **Juicer** | In-app sidebar wordmark, above the "Crypto Casino" descriptor |
| Descriptor | **Crypto Casino** | Directly under the Juicer wordmark, 10px, tertiary grey |
| Token | **JXR** | Token symbol, price chip label "JXR Token" |
| Domain | **juicer.games** | Every link, every share card footer, every overlay, all creative |
| Token name (not a domain) | **JXR Gaming** / **JXR** | Token metadata `name` / `symbol` |

### 1.1 The one-domain rule — read this before writing any URL

**`juicer.games` is the only brand domain.** It is the canonical referral and share origin: the
referral builder hard-codes `https://juicer.games/?ref=CODE` as the origin precisely so that a link
copied from a staging or `workers.dev` host is still correct when pasted anywhere else.

Use it in exactly this shape:

| Context | Form |
|---|---|
| Clickable link, chat, social post, description | `https://juicer.games/?ref=CODE` |
| Overlay, video, card footer, print | `juicer.games` (no scheme) |

> ⚠ **DEFECT — do not copy from these files.** `jxr.gg` still appears in the repo, and it is
> **wrong**. It is present in:
>
> - `public/jxr-token-metadata.json` — `image`, `external_url`, and `properties.files[0].uri`
> - `.scripts/jxr-metadata.mjs` and `.scripts/set-jxr-metadata.mjs`
> - `HOUSE-FOUNDER-AFFILIATE.md` and `HOUSE-FOUNDER-AFFILIATE-TG.md` (as `jxr.gg/r/XXXXXX`, which is
>   also the wrong link *shape* — the canonical form is `?ref=CODE`, not a `/r/` path)
>
> **No marketing asset may display `jxr.gg`.** If you need a URL in creative, it is `juicer.games`.
> The token metadata strings must be corrected at source before any token-registry update ships,
> because whatever is on chain cannot be edited later.
>
> Note the link *shape* error separately from the domain error: `jxr.gg/r/XXXXXX` is doubly wrong.
> `/r/<id>` is the shared-bet landing route, not a referral route — a referral code belongs in the
> `?ref=` query parameter.

---

## 2. Colour system

There are **two co-existing palettes** in the product. This is intentional and must be understood,
not "corrected":

- **Brand gold (`#f0a342`)** — the core brand colour. Semantic `--primary`, the `themeColor` that
  tints browser chrome, the ring colour, the logo glow family, the chart series base.
- **v2.0 orange (`#f97316`)** — the *action* accent used by the v2.0 reference UI: primary buttons,
  sidebar active state, game-card accents, OG card accent, share-card avatar gradient.

Rule of thumb: **gold is identity, orange is interaction.** A logo, a page background wash, or a
brand-identity lockup uses gold. A "Deposit", "Bet", "Play" or "Claim" style call to action uses
orange. Never place gold and orange adjacent as a two-tone gradient — that reads as a rendering
error.

### 2.1 Core semantic tokens

| Token | Hex | Use |
|---|---|---|
| `--background` | `#0d1017` | App base background |
| `--card` | `#0b0e14` | Card / panel surface |
| `--popover` | `#0f131a` | Floating surface, menus |
| `--foreground` | `#bfbdb6` | Default body text |
| `--primary` | `#f0a342` | **Brand gold** — identity, focus ring, `themeColor` |
| `--primary-foreground` | `#734d00` | Text *on* gold fills |
| `--secondary` | `#0b0e14` | Secondary surface |
| `--muted` | `#131721` | Muted surface, hover background |
| `--muted-foreground` | `#565b66` | De-emphasised text |
| `--accent` | `#0f131a` | Accent surface |
| `--destructive` | `#f26d78` | Destructive actions, errors |
| `--border` | `#1e232b` | Default border |
| `--input` | `#2a2f3a` | Input field background |
| `--ring` | `#f0a342` | Focus ring |

### 2.2 Brand gold ramp (Radix-style 1→12)

Use low steps for tinted surfaces, step 9 for the brand colour itself, 10 for hover, 11 for
emphasis text, 12 for light-on-gold text.

| Step | Hex | Step | Hex |
|---|---|---|---|
| `--accent-1` | `#0d0a02` | `--accent-7` | `#6d5317` |
| `--accent-2` | `#171106` | `--accent-8` | `#8c6c1f` |
| `--accent-3` | `#241b07` | `--accent-9` | `#f0a342` |
| `--accent-4` | `#332609` | `--accent-10` | `#e9973c` |
| `--accent-5` | `#42320d` | `--accent-11` | `#ffca62` |
| `--accent-6` | `#554010` | `--accent-12` | `#fdeecb` |

### 2.3 Brand tokens

| Token | Value |
|---|---|
| `--jxr-primary` | `#f0a342` |
| `--jxr-primary-hover` | `#e9973c` |
| `--jxr-primary-muted` | `rgba(240, 163, 66, 0.12)` |
| `--jxr-primary-glow` | `rgba(240, 163, 66, 0.3)` |
| `--jxr-secondary` | `#f9af4f` |
| `--jxr-gradient` | `linear-gradient(135deg, #f0a342, #f9af4f)` |

### 2.4 v2.0 orange (action accent)

| Token | Value | Use |
|---|---|---|
| `--jxr-accent-orange` | `#f97316` | Primary CTA fill, active nav, game accent |
| `--jxr-accent-orange-hover` | `#fb8c2a` | CTA hover |
| `--jxr-accent-orange-glow` | `rgba(249, 115, 22, 0.55)` | CTA glow, logo glow |
| `--jxr-accent-orange-bg` | `#2a1808` | Orange-tinted inset surface |
| `--jxr-accent-orange-bright` | `#ff8a2b` | Bright highlight |

### 2.5 Deep surfaces, borders, text

| Token | Hex | Use |
|---|---|---|
| `--jxr-bg-app` | `#0a0a10` | Deepest app background |
| `--jxr-bg-panel` | `#0e0e16` | Standard panel |
| `--jxr-bg-panel-2` | `#12121c` | Raised / secondary panel |
| `--jxr-bg-deeper` | `#07080e` | Recessed well |
| `--jxr-bg-input` | `#161620` | Input surface |
| `--jxr-border-subtle` | `#20202c` | Hairline border |
| `--jxr-border-strong` | `#2c2c3a` | Emphasised border |
| `--jxr-text-primary` | `#f2f2f7` | Headlines, primary values |
| `--jxr-text-secondary` | `#8e8e9a` | Supporting copy |
| `--jxr-text-tertiary` | `#5a5a66` | Meta / labels |

### 2.6 Semantic status

| Role | Hex |
|---|---|
| Success | `#7fd962` |
| Warning | `#ffb454` |
| Danger / error (not an outcome colour) | `#f26d78` |
| Info | `#90e1c6` |
| Accent cyan | `#4dffd1` |
| Result green | `#22c55e` |
| Result red | `#ff4d6a` |

**Win/loss convention:** result surfaces use `#22c55e` for a win and `#ff4d6a` for a loss. The older
`#7fd962` / `#f26d78` pair belongs to the app's semantic status tokens (toasts, form errors). Do not
mix the two pairs inside one asset — pick the result pair for outcome badges, the status pair for
system messages.

Win/loss chip filled backgrounds (used on share cards):

| State | Background | Text |
|---|---|---|
| Win | `#0a1f12` | `#22c55e` |
| Loss | `#2b1018` | `#ff4d6a` |

### 2.7 Chart series

`#f0a342` · `#f9af4f` · `#7fd962` · `#90e1c6` · `#d2a6ff`

### 2.8 Game accent colours

These are the accents the live lobby uses per game tile:

| Game | Accent | Game | Accent |
|---|---|---|---|
| Crash | `#f97316` | Limbo | `#f9af4f` |
| Plinko | `#f97316` | Keno | `#f9af4f` |
| Dice | `#f97316` | Blackjack | `#f07178` |
| Roulette | `#f97316` | HiLo | `#ffb454` |
| Flip | `#f97316` | Wheel | `#f9af4f` |
| Slots | `#f97316` | Mines | `#ff4d6a` |
| Jackpot | `#f97316` | | |

> ⚠ OPEN — A **second, older** game-accent set exists in CSS (`--game-*`), and it disagrees with the
> live lobby. For example the CSS token for Dice is `#f0a342` while the lobby renders Dice as
> `#f97316`; Limbo is `#f29668` in CSS but `#f9af4f` in the lobby. **Treat the table above as
> correct** and treat the `--game-*` CSS block as legacy until it is reconciled. Do not produce
> collateral from the legacy block.

### 2.9 VIP tier colours

Exactly 14 tiers. These are fixed — a tier colour is a player-facing status signal.

| Tier | Hex | Tier | Hex |
|---|---|---|---|
| Wood | `#b08150` | Ruby | `#e5484d` |
| Bronze | `#cd7f32` | Diamond | `#8dd8f8` |
| Silver | `#c0c0c0` | Opal | `#9fe6e0` |
| Gold | `#ffd700` | Dragon | `#ff6b6b` |
| Platinum | `#e5e4e2` | Mythic | `#ffd700` |
| Jade | `#3ecf8e` | Dark | `#6b7280` |
| Sapphire | `#4a9dff` | Legend | `#fbbf24` |

Note that Gold and Mythic intentionally share `#ffd700`; distinguish them by **badge artwork**, never
by recolouring either one.

### 2.10 Colour accessibility

Minimum contrast for text on the dark surfaces above:

- Body text: `#f2f2f7` or `#bfbdb6` on `#0a0a10`–`#12121c`.
- Secondary text: `#8e8e9a` — acceptable at 10px and above; do not go lighter-weight *and* smaller
  at the same time.
- Tertiary text `#5a5a66` is **decorative only** below 10px. Never use it for anything a viewer must
  read.
- On orange `#f97316` fills, use `#0a0a10` or `#ffffff` text — never gold `#f0a342` text, which
  fails contrast badly.

---

## 3. Typography

Two typefaces. That is the entire system.

### 3.1 CourbeSans — everything that is read

Self-hosted, weights **400** and **700** only. There is no 500, no 600, no 900. If a design calls for
a weight that does not exist, the browser will synthesise it — which looks wrong. Use 700 for
emphasis and increase size instead of synthesising weight.

| Property | Value |
|---|---|
| Family name | `CourbeSans` |
| Weights | 400 (regular), 700 (bold) |
| Rights holder | Loukas Nicolaou — trademark "Courbe Sans" |
| Included in this repo | **No** — licensed, reference only. See [`03-typography/README.md`](03-typography/README.md) |
| App OpenType path | `public/CourbeSans/CourbeSans.otf.otf` |
| App TrueType path | `public/CourbeSans/CourbeSans.ttf.ttf` |
| Web path | `/CourbeSans/CourbeSans.otf.otf`, `/CourbeSans/CourbeSans.ttf.ttf` |
| Fallback stack | `'CourbeSans', 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif` |

**The font binaries are not distributed with this guide.** Courbe Sans is licensed commercial type;
the files are issued per project for use on the JXR Gaming platform and its sanctioned channels, not
for redistribution. Request access via the steps in [`03-typography/README.md`](03-typography/README.md).

The double extension (`.otf.otf`, `.ttf.ttf`) is the real filename in the application source — it is
not a typo in this document. Preserve it.

### 3.2 Display / wordmark face — `.font-gothic`

A **system-only** stack used for the "Juicer" wordmark and heavy display numbers. It is deliberately
not a webfont, so it never triggers a network fetch.

| Property | Value |
|---|---|
| Stack | `'Arial Black', 'Impact', 'Franklin Gothic Heavy', 'Haettenschweiler', system-ui, sans-serif` |
| Weight | 900 |
| Letter spacing | `0.02em` |
| Transform | Uppercase (applied by the class) |

**Use for:** the wordmark, big multiplier figures, "BUST"/"WIN" stamps.
**Do not use for:** body copy, buttons, table data, codes, or anything above ~8 words. It is a
display face and it becomes unreadable quickly. Because it is a system stack, it renders differently
on macOS vs Windows vs Linux — so **never use it for an asset where exact glyph metrics matter**
(video lower-thirds with tight kerning, animated typography). For those, set the wordmark as vector
art or use CourbeSans 700.

### 3.3 Monospace

`ui-monospace, SFMono-Regular, Menlo, monospace`

Used for: multipliers on share cards, currency amounts, hashes and seed values. Any number that a
player might screenshot should be monospace so digits align.

### 3.4 Type scale

The app runs a deliberately compact scale. **Do not scale these up for print or video — scale the
whole layout instead.**

| Token | px | Rem | Use |
|---|---|---|---|
| `--jxr-text-2xs` | 8 | 0.5rem | Micro labels, card descriptions |
| `--jxr-text-xs` | 10 | 0.625rem | Small labels, meta |
| `--jxr-text-sm` | 11 | 0.6875rem | Base input text, card titles |
| `--jxr-text-md` | 13 | 0.8125rem | Button text |
| `--jxr-text-lg` | 15 | 0.9375rem | Display text, wordmark |

For overlay and video work, the scale above is the *reference proportion*. Section 8 gives absolute
pixel sizes for 1080p.

### 3.5 Text treatment rules

- Headings are set in `--jxr-text-primary` `#f2f2f7`. Supporting copy in `#8e8e9a`. Meta in
  `#5a5a66`.
- Maximum two type sizes per card. Three is a hierarchy failure.
- No drop shadows on text except the display multiplier on video/overlay assets.
- No coloured body text. Colour belongs to accents, values, and state — not paragraphs.

---

## 4. Logo and mascot

### 4.1 The mascot

The brand mark is the **Juicebox sticker** — a sticker-style character, not a flat geometric logo.
It is supplied as a `.webp` and is the only approved primary mark.

| Asset | Path | Notes |
|---|---|---|
| Primary mascot | `public/juicebox_sticker.webp` | Favicon, app icon, OG image, sidebar mark |

**Live usage in production:** 34×34 in the sidebar wordmark lockup, 44×44 on the OG card,
and as the favicon + apple-touch icon + Open Graph image.

### 4.2 Clear space and minimum size

- **Minimum size:** 24×24 px on screen, 12 mm in print.
- **Clear space:** at least 25% of the mark's width on all sides, free of text, borders, and other
  graphics. The sticker has an irregular outline — clear space is measured from its bounding box,
  not its silhouette.
- **Never** crop the sticker, stretch it, recolour it, add an outline, or place it on a busy photo
  without a scrim.

### 4.3 Wordmark lockup

```
[sticker 34px]   Juicer          ← .font-gothic, 15px, uppercase, #f2f2f7
                 Crypto Casino   ← 10px, CourbeSans 400, #5a5a66
```

Horizontal lockup, mark left, text block right. The measured gap is **10.8px**, not the 12px a
`gap-3` class would normally produce: `globals.css` overrides `--spacing` to `0.225rem`, so every
Tailwind spacing utility renders at **90%** of its default value (`gap-3` = 0.675rem = 10.8px). The
descriptor is *part of the lockup* and sits on the second line — never inline, never omitted from a
first-use placement.

### 4.4 Logo animation

The live sidebar applies a combined float + glow. This is the only sanctioned logo animation.

| Property | Value |
|---|---|
| `logo-float` | 3s ease-in-out infinite, `translateY(0)` → `translateY(-4px)` → `translateY(0)` |
| `logo-glow` | 3s ease-in-out infinite; at rest `drop-shadow(0 0 6px rgba(249,115,22,0.4))`; at peak `drop-shadow(0 0 20px rgba(249,115,22,0.75)) drop-shadow(0 0 40px rgba(249,115,22,0.25))` |
| Combined class | `.logo-float-glow` |

For video, replicate exactly: ±4px float, 3-second cycle, orange glow at 40%→75% opacity. Do not
speed it up to "add energy" — the 3s cadence matches the in-app mark.

### 4.5 Token mark

| Asset | Path | Live usage |
|---|---|---|
| JXR token icon | `public/jxr_token.png` | 16×16 in the sidebar price chip, rounded-full; 192px source embedded in the OG renderer |

The token mark is **not** a second logo. It never replaces the Juicebox sticker in a brand lockup.
It appears only where a token/currency is being named.

### 4.6 Asset inventory

All verified present in `public/`:

**Brand / campaign**
- `juicebox_sticker.webp` — primary mascot
- `jxr_token.png` — token mark
- `juicer-banner.jpg` — wide banner
- `tails-jxr.jpeg` — campaign image
- `images/juicer-hero-banner.png` — hero banner
- `images/jxr.gg_r_xxxxxx.png` — legacy share-preview image. **Filename carries the retired `jxr.gg`
  domain — do not use this asset in new work**, and do not recreate its naming pattern. Kept here
  only so nobody mistakes it for an approved asset when they find it in the folder.

**VIP tier badges** (14, all `public/images/`)

| Tier | File |
|---|---|
| Wood | `wood-log-badge.png` |
| Bronze | `bronze-badge.png` |
| Silver | `silver-badge.png` |
| Gold | `gold-badge.png` |
| Platinum | `plat-badge.png` |
| Jade | `jade-badge.png` |
| Sapphire | `sapphire-badge.png` |
| Ruby | `ruby-badge.png` |
| Diamond | `diamond-badge.png` |
| Opal | `opal-badge.png` |
| Dragon | `dragon-badge.png` |
| Mythic | `mythic-badge.png` |
| Dark | `dark-badge.png` |
| Legend | `legend-badge.png` |

Two filenames are irregular and must not be "tidied": **Wood** is `wood-log-badge.png` and
**Platinum** is `plat-badge.png`. The rest follow `<key>-badge.png`.

**Telegram sticker pack** (`public/telegram-emoji/`)
- `juicebox-100.png`, `juicebox-512.png` — static, 100px and 512px
- `juicebox-floating-100.webm`, `juicebox-floating-512.webm` — animated

**Line icon set** (`public/icons/`) — **65 SVG icons**, Lucide-derived. Categories present: game
(dice-2 through dice-6, dices, blackjack, roulette, slots, playing-card, playing-cards,
playing-cards-fan, cherry, clover, gem, skull, casino, original, table-games), navigation (home,
menu, search, chevron, arrow-big-up-dash, arrow-big-down-dash), UI (wallet, token, coins, gift,
star, medal, vip, promotions, challenge, flame, rocket, sprout, shovel, eye, radar, scan-box,
refresh-ccw-dot, square-sparkles, galaxy), and support (live-support, headset, headphones,
headphone-off, users-collaboration, lock-keyhole, lock-keyhole-open, book-copy, book-bookmark,
flask-conical, flask-conical-off, flask-round, gamepad, gamepad-directional, game-popup, ghost,
provider, affiliate), plus supporting UI glyphs.

These are **UI icons, not brand illustrations.** They never appear in a logo lockup, a hero, or a
social post as decoration. Decorative iconography is a brand breach; if a layout needs ornament, use
the grid texture (Section 6.3) or the brand gradient.

> ⚠ OPEN — The icon set is **not internally consistent**, so it must not be lifted wholesale into
> marketing collateral. Three different treatments ship side by side:
>
> | Treatment | Count | Detail |
> |---|---|---|
> | Fixed orange, thin | 43 | `stroke="#ff8647"`, `stroke-width="1"` |
> | Themed | 18 | `stroke="currentColor"`, `stroke-width="2"` — inherits surrounding colour |
> | Brand orange, thin | 3 | `stroke="#f97316"`, `stroke-width="0.75"` — `dices`, `refresh-ccw-dot`, `wallet` |
>
> **`#ff8647` is not a brand token.** It appears in these files and nowhere else in the product —
> it is an unratified orange and must not be reproduced in any new asset. Until the set is
> normalised, do not use these icons in marketing work; commission the specific glyph you need, or
> use the UI screens (Section 7) as the icon reference.
>
> Also note: SVG icons rendered at 20px with `stroke-width="1"` will look hairline-thin and break up
> when scaled to overlay or video sizes. Never scale a 20px UI icon up for a 1080p overlay.

---

## 5. Asset usage rules — quick reference

| Allowed | Not allowed |
|---|---|
| Mascot on flat dark surface or brand gradient | Mascot on a photo without a scrim |
| Gold for identity, orange for action | Gold and orange as a two-stop gradient |
| VIP badge at its native aspect ratio | Recoloured or outlined VIP badge |
| `juicer.games` in every link and overlay | `jxr.gg` in any asset (retired domain — see 1.1) |
| CourbeSans at 400/700 | CourbeSans at a synthesised 600/900 |
| `.font-gothic` for wordmark and big numbers | `.font-gothic` for paragraphs, buttons or codes |
| Line icons as functional UI affordances | Line icons as decorative art in campaign creative |
| Result green `#22c55e` / red `#ff4d6a` for outcomes | Status green `#7fd962` / red `#f26d78` used as outcome colours |

---

## 6. Geometry, depth and motion

### 6.1 Corner radii

The brand is **sharp**, not soft. This is a defining characteristic.

| Token | Value | Use |
|---|---|---|
| `--jxr-radius-sharp` | `3px` | Buttons, chips, badges, inputs |
| `--jxr-radius-item` | `2px` | Small list items, tags |
| — | `10px` | Large cards (lobby tiles), brand icon in OG card |
| — | `4px` | Sidebar panels |
| `--radius` (root) | `0.375rem` (6px) | Radix/shadcn primitives |
| — | `9999px` / `rounded-full` | Avatars and the token chip only |

Do not round a button to a pill. Do not use the `10px` card radius on a small element — the contrast
between sharp chrome and generously rounded cards is the system.

### 6.2 Depth

| Token | Value |
|---|---|
| `--jxr-shadow-1` | `0 1px 2px rgba(0,0,0,0.85)` |
| `--jxr-shadow-frame` | `0 1px 3px rgba(0,0,0,0.9), 0 12px 32px rgba(0,0,0,0.8)` |
| Modal shadow | `0 16px 40px rgba(0,0,0,0.95)` |
| Hairline "border" | `box-shadow: 0 0 0 1px #20202c` (preferred over a real border for crisper 1px at any DPI) |

Depth is achieved by **contrast between surfaces** (`#07080e` → `#0a0a10` → `#0e0e16` → `#12121c`),
not by heavy shadows. A card floating on a lighter panel should still read as raised.

### 6.3 Grid texture

The signature lobby-tile texture is a two-axis 1px grid:

- Cell size: **18px**
- Line colour: the tile's accent at ~8% alpha (`${accentHex}14`)
- Overall layer opacity: **20%**
- Tile background: `linear-gradient(145deg, ${accentHex}1a 0%, #0e0e16 60%, #12121c 100%)`

For production in a design tool: accent at 8% alpha over the gradient above, grid at 18px, layer
opacity 20%. It should be *faint*. If you can read the grid from a metre away, it is too strong.

### 6.4 Motion

| Name | Spec | Use |
|---|---|---|
| `logo-float` | 3s, `translateY(0 → -4px → 0)`, ease-in-out, infinite | Logo |
| `logo-glow` | 3s, orange drop-shadow 6px@40% → 20px@75% + 40px@25% | Logo |
| `juicer-glow` | 2s, gold box-shadow 20px@20% → 40px@40% | Prominent containers |
| `fade-in` | 0.3s ease-out, `translateY(8px)` → `translateY(0)`, opacity 0→1 | Content entrance |
| `jxr-toast-in` | `translateX(-12px) scale(0.98)` → `translateX(0) scale(1)`, opacity 0→1 | Notifications |
| `edge-shimmer` | 2.6s, gold border 14%→38% alpha | Subtle emphasis frame |
| `shimmer` | 1.8s, background-position 200% → -200% | Loading skeleton |

For video: entrance moves are **8px maximum**. The brand does not do large fly-ins, spins, or
bounces, with one exception — game result moments (crash multiplier, wheel, dice) use their own
per-game easing and are out of scope for marketing motion.

### 6.5 The 90% spacing scale — measure, don't assume

`globals.css` sets `@theme { --spacing: 0.225rem }`. That overrides Tailwind's default spacing unit
from `0.25rem` (4px) to `0.225rem` (**3.6px**), so **every spacing utility renders at 90% of its
nominal value**. A `gap-3` is 10.8px, not 12px. A `p-2.5` is 9px, not 10px.

| Class | Nominal | Actual |
|---|---|---|
| `gap-2` | 8px | **7.2px** |
| `gap-3` | 12px | **10.8px** |
| `p-2.5` | 10px | **9px** |
| `px-1.5` | 6px | **5.4px** |
| `py-0.5` | 2px | **1.8px** |
| `p-3` | 12px | **10.8px** |

Practical consequences when reproducing a template:

- If you rebuild a card in Figma from the class names, you will end up **10% too large in every
  spacing dimension**. Do not work from class names alone.
- Type sizes are **not** affected — they are set in explicit `px` (`text-[11px]`), not in spacing
  units. Only geometry moves.
- The Radix `--space-1…--space-9` tokens use the same `0.9` scaling factor explicitly
  (`--space-1: calc(4px * var(--scaling))` = 3.6px … `--space-9` = 57.6px).

This is why Section 7 quotes measured pixel values rather than Tailwind class names wherever the
value matters.

---

## 7. Ready-made templates

Three templates already exist in production. Reproduce them exactly rather than designing new ones.

### 7.1 Bet share card — Open Graph, 1200×630

The canonical social/OG image. Source: the OG route renderer.

| Property | Value |
|---|---|
| Canvas | **1200 × 630** |
| Background | `linear-gradient(135deg, #0b0b12 0%, #14141e 100%)` |
| Padding | **64px** on all sides |
| Layout | vertical, `space-between` (header / result / footer) |
| Typeface | CourbeSans; falls back to system sans if unavailable |

**Element specs**

| Element | Spec |
|---|---|
| Avatar / badge | 44×44, `object-fit: contain` |
| Avatar fallback | 44×44 circle, `linear-gradient(135deg, #f97316, #f9af4f)`, white initial at 24px/800 |
| Player name | 30px, weight 800, `#f2f2f7` |
| Game line | 20px, `#8e8e9a`, format `"<Game> · Juicer.games"` |
| Multiplier / result | 150px, weight 900, line-height 1; win `#22c55e`, loss `#ff4d6a` |
| Result label | `"<n>.<nn>x"` when a win with multiplier > 0; `"WIN"` for a zero-multiplier win; `"BUST"` for a loss |
| Payout | 56px, weight 700, `#22c55e` when win else `#8e8e9a`, prefixed `+` |
| Footer bet line | 26px, `#c2c2cc`, format `"Bet <amount>"` |
| Brand icon | 40×40, radius 10px |
| Footer domain | 26px, weight 700, `#f97316`, text `juicer.games` |

`#c2c2cc` is a one-off value that appears only in this OG footer. It is approved **only for that
slot**; do not promote it into a general palette.

### 7.2 Lobby game tile — 180×135

| Property | Value |
|---|---|
| Size | **180 × 135** |
| Radius | 10px |
| Background | `linear-gradient(145deg, <accent>1a 0%, #0e0e16 60%, #12121c 100%)` |
| Grid | 18px cells, `<accent>14` lines, layer opacity 20% |
| Icon glow | 80×80 circle, `radial-gradient(circle, <accent>33 0%, transparent 70%)`, centred at 52% vertical |
| Title | 11px, weight 700, uppercase, `letter-spacing: 0.06em`, colour = accent |
| Description | 8px, `rgba(255,255,255,0.38)`, single line, truncated |
| Interaction | 3D tilt container with an orange / cyan / green ring variant |

Accent selection comes from Section 2.8.

### 7.3 In-app bet share card — 248px wide

| Property | Value |
|---|---|
| Width | **248px** (max 100% of container) |
| Background | `#12121c` |
| Outline | `0 0 0 1px #20202c` |
| Padding | `10.8px` (0.675rem — `p-3` at the 90% scale) |
| Avatar | 32×32 circle, `linear-gradient(135deg, #f97316, #f9af4f)`, VIP badge image at `object-fit: contain` |
| Player name | 11px, weight 700, `#f2f2f7` |
| Meta line | 9px, `#5a5a66`, format `"<Game> · Bet <amount>"` |
| Multiplier chip | radius 3px, padding **5.4px × 1.8px** (`px-1.5 py-0.5` at the 90% scale), monospace 10px weight 700 |
| Win chip | bg `#0a1f12`, text `#22c55e` |
| Loss chip | bg `#2b1018`, text `#ff4d6a` |
| Payout | 10px monospace weight 700, `#22c55e` on win else `#5a5a66` |
| CTA | 9px weight 600, `#f97316`, text `"View result →"` |

Loss multiplier label renders `"0x"`, not `"—"`. Zero-payout wins render `"FREE WIN"`.

---

## 8. Kick.com streamer overlay suite — NEW SPECIFICATION

> **Status: to be built.** No streamer overlay asset exists in the repository today. This section is
> the build specification, not documentation of shipped work. Every dimension below is a Juicer
> decision made for legibility and safety — it is **not** a quoted platform requirement. Re-check
> against the live player before each seasonal refresh.

### 8.1 Design intent

The overlay has exactly one job: **make the referral code readable at 480p, in under two seconds,
without covering gameplay.** Everything else is secondary. A beautiful overlay that hides the code
during a win, or that buries the code under chat, has failed.

Non-negotiables:

1. The code is always the **highest-contrast element** on screen.
2. The code is **persistent** — it cannot appear only on alerts or between rounds.
3. The overlay **never covers the bottom-centre** of the frame, where the player's own cursor,
   health bar, or Kick player controls sit.
4. No Kick logo, no Kick wordmark, no imitation of Kick's own UI. Do not imply endorsement.

### 8.2 Canvas and safe areas

| Property | Value |
|---|---|
| Source canvas | **1920 × 1080** |
| Delivery format | PNG with alpha, plus `.webm` (VP9 + alpha) for animated variants |
| Outer margin | **40px** minimum on all edges |
| Bottom exclusion band | **bottom 120px** — keep clear |
| Right exclusion band | **right 340px** — keep clear (docked chat) |
| Top exclusion band | **top 80px** — keep clear (stream chrome, notifications) |
| Design-to-air note | Design at 1920×1080 and preview at **960×540**; if the code is not readable at 960×540, increase it |

The right-hand and bottom exclusions are the two that get violated most often. When chat is docked,
the right 340px is invisible to the viewer — a code placed there is a code nobody sees.

### 8.3 Colour and type for overlays

Overlays sit on top of moving, unpredictable game footage. Two adjustments are mandatory:

| Element | Value | Why |
|---|---|---|
| Base panel fill | `#0e0e16` at **88% opacity** | Full opacity reads as a cut-out; below 80% the text loses contrast against bright game frames |
| Panel hairline | `1px #20202c` at 100% | Separates the panel from bright gameplay |
| Code text | `#f2f2f7` | Maximum contrast |
| Code accent bar / chip | `#f97316` | Action accent — this is a CTA, not identity |
| Supporting line | `#8e8e9a` | Never `#5a5a66` over video |
| Brand mark | Mascot at its native aspect ratio | No recolour |
| Code typeface | CourbeSans **700**, uppercase, `letter-spacing: 0.08em` | Do **not** use `.font-gothic` for codes — its system stack renders differently per OS and its letterforms are hard to parse at speed |
| URL typeface | CourbeSans 400 | Lower visual weight than the code |

Because `.font-gothic` is a system stack, **any overlay text must be CourbeSans** (or vector art
derived from it). Text rendered in `.font-gothic` will look different on the editor's Mac and the
streamer's Windows PC.

### 8.4 Referral code rules (copy, not design)

The code itself is governed by the platform, and marketing must respect the same rules the client
enforces:

| Rule | Value |
|---|---|
| Length | **4–16 characters** |
| Allowed characters | `A-Z`, `0-9`, `-`, `_` |
| Leading/trailing separator | Not allowed |
| Case | Stored and compared **uppercase**; display uppercase always |
| Reserved words | `JXR`, `JUICER`, `GAMES`, `ADMIN`, `HOUSE`, `SYSTEM`, `SUPPORT`, `OFFICIAL`, `VIP`, `PROMO`, `REF`, `REFERRAL`, `LOGIN`, `REGISTER`, `SIGNUP`, `TERMS`, `ABOUT`, `API`, `OPS`, `WWW`, `APP`, `HELP`, `NULL`, `UNDEFINED` |

**Canonical link:** `https://juicer.games/?ref=CODE`

On an overlay, display it as:

```
┌─────────────────────────────┐
│  USE CODE                   │  ← 18px, #8e8e9a, uppercase, 0.10em
│   MIKEx2026                 │  ← 56px, #f2f2f7, 700, 0.08em
│  juicer.games               │  ← 22px, #8e8e9a
└─────────────────────────────┘
```

Never print `https://` on an overlay — it is visual noise at broadcast scale. The domain alone is
sufficient and is what players type. But **anywhere the link is clickable or copy-pasteable**
(chat message, description, social post), use the full canonical `https://juicer.games/?ref=CODE`.

### 8.5 Deliverables

All at 1920×1080 unless stated. Positions given as (x, y) from top-left.

#### A. Code card — lower third, primary

| Property | Spec |
|---|---|
| Size | **420 × 140** |
| Position | x = 40, y = 1080 − 40 − 140 − 120 → **y = 780** |
| Radius | 3px |
| Fill | `#0e0e16` @ 88% |
| Hairline | `1px #20202c` |
| Left accent bar | **4px wide, full height, `#f97316`** |
| Padding | 24px |
| Line 1 | "USE CODE" — 18px, 700, `#8e8e9a`, `0.10em` |
| Line 2 (code) | **56px**, 700, `#f2f2f7`, `0.08em` — this is the hero element |
| Line 3 | `juicer.games` — 22px, 400, `#8e8e9a` |
| Mascot | 56×56, right-aligned, 24px from the right edge |

The 56px code renders at 28px on a 960-wide preview. That is the floor of legibility. Do not reduce.

#### B. Persistent code bug — top-left

| Property | Spec |
|---|---|
| Size | **300 × 72** |
| Position | x = 40, y = 40 |
| Radius | 3px |
| Fill | `#0e0e16` @ 88% |
| Left accent bar | 4px, `#f97316` |
| Content | "CODE" 14px `#8e8e9a` above the code at **34px** 700 `#f2f2f7`, single line |
| Mascot | 40×40, left of the text block, 16px gap |

This is the **always-on** element. It ships in every scene, including "just chatting", the starting
screen, and the ending screen. Everything else in this section is optional; this is not.

#### C. Full-frame starting-soon / BRB / ending

| Property | Spec |
|---|---|
| Size | 1920 × 1080, opaque |
| Background | `#0a0a10` |
| Optional texture | 18px grid, `#f97316` at 8% alpha, layer opacity 20% |
| Mascot | Centred-lockup treatment, 280×280 clear space |
| Headline | CourbeSans 700, 96px, `#f2f2f7` — e.g. "STARTING SOON" |
| Sub-line | CourbeSans 400, 40px, `#8e8e9a` |
| Code block | Centred, code at **120px**, 700, `#f2f2f7`; "USE CODE" above at 32px `#8e8e9a`; `juicer.games` below at 40px |
| CTA rule | A 3px `#f97316` rule, 240px wide, centred, 32px above the code |

#### D. Alert — follow / sub / raid

| Property | Spec |
|---|---|
| Size | **720 × 200**, transparent background |
| Position | x = 40, y = 160 |
| Panel | radius 3px, `#0e0e16` @ 92%, hairline `#2c2c3a` |
| Accent bar | 6px `#f97316`, full height, left edge |
| Title | 44px, 700, `#f2f2f7` — e.g. "NEW FOLLOWER" |
| Body | 28px, 400, `#8e8e9a` — the username |
| Code strip | bottom of the panel: "CODE" 16px `#8e8e9a` + code at 40px 700 `#f97316` |
| Animation | 400ms slide from −24px, ease-out; hold 6s; 400ms fade out |
| Sound | None by default — a streamer may attach their own |

The alert still carries the code. An alert is a spike in attention; wasting it on a name alone is a
missed impression.

#### E. Winning-moment stamp

| Property | Spec |
|---|---|
| Size | 900 × 260, transparent |
| Position | centred horizontally, y = 300 |
| Headline | CourbeSans 700, 96px, `#22c55e` for a win / `#ff4d6a` for a loss |
| Multiplier | 160px, 700, `#22c55e` / `#ff4d6a` |
| Code line | 30px, 700, `#f97316`, bottom-right of the stamp: `CODE · juicer.games` |
| Animation | 200ms scale 0.94 → 1 with opacity 0 → 1; hold 3.5s; 300ms fade |

Do not put the mascot on this stamp. The result colour is the focus.

#### F. Optional webcam frame

| Property | Spec |
|---|---|
| Size | 480 × 360 (4:3) — supports 16:9 by letterboxing |
| Border | 3px `#f97316` on the bottom edge only; 1px `#20202c` elsewhere |
| Corner tag | 160 × 40, bottom-left, `#0e0e16` @ 88%, code at 24px 700 `#f2f2f7` |
| Radius | 3px |

### 8.6 Scene slot naming

Deliver files with a stable, sortable naming convention so an OBS scene collection can be rebuilt
from the folder alone:

```
jxr-kick_{variant}_{scene}_{width}x{height}_{rev}.{ext}
```

Examples:

```
jxr-kick_codecard_ingame_420x140_v1.png
jxr-kick_codebug_all_300x72_v1.png
jxr-kick_starting_brb_1920x1080_v1.png
jxr-kick_alert_follow_720x200_v1.png
jxr-kick_alert_sub_720x200_v1.webm
jxr-kick_stamp_win_900x260_v1.webm
```

Use `{scene}` values: `ingame`, `brb`, `starting`, `ending`, `all`.

### 8.7 Overlay do / don't

| Do | Don't |
|---|---|
| Keep the code bug on screen for 100% of the stream | Fade the code out during gameplay |
| Use 88% panel opacity over gameplay | Use a fully transparent panel with text directly on video |
| Use CourbeSans for all overlay text | Use `.font-gothic` for codes or URLs |
| Keep the bottom 120px and right 340px clear | Place the code where docked chat will cover it |
| Use `#f97316` for the code accent | Introduce a new accent hue for "streamer personalisation" |
| Include the mascot at its native aspect | Recolour or outline the mascot to match an overlay theme |
| Show `juicer.games` under the code | Show `https://` on a broadcast overlay |
| Ship PNG with alpha + WebM with alpha | Ship a baked-in video background |

### 8.8 Streamer hand-off checklist

Give each partner exactly this, and nothing invented:

1. The overlay pack (files from 8.5).
2. Their **canonical** referral link: `https://juicer.games/?ref=<CODE>`.
3. Their code in uppercase, confirmed to be 4–16 characters and not reserved.
4. The correct claim to make — see Section 10. No earnings promises.
5. The 18+ / responsible-gaming line (Section 11) for use in the stream description.

---

## 9. Writing and copy rules

| Rule | Detail |
|---|---|
| Wordmark case | `Juicer` — capital J, never `JUICER` in running copy. Uppercase is for the display lockup only |
| Platform name | `JXR Gaming` — always both words |
| Token | `JXR` — uppercase, no space |
| Domain | lowercase `juicer.games` |
| Code | uppercase, monospace or CourbeSans 700, never lowercase |
| Numbers | Use the shared formatters' output shape: multipliers as `1.93x` (2dp) / `1.2kx` above 1000x; amounts with up to 9 decimals, minimum 2 |
| Multiplication sign | `x`, not `×`, in player-facing numbers (`2.50x`) |
| Arrows | `→` is used for navigation affordances ("View result →") |

**Never state a payout figure that the engine does not produce.** The displayed multiplier for a game
is derived from the settlement function. A 50% dice roll-over pays **1.94x** (not 2x); a 2x limbo
target pays **1.93x** (not 2x). If marketing needs a headline number, take it from the live UI —
never recompute it.

---

## 10. Claims discipline

These are the only performance figures with a source. Quote them verbatim or not at all.

**House Founder Affiliate** — from `HOUSE-FOUNDER-AFFILIATE.md`:

| Fee stream | House retains | Affiliate share | Split |
|---|---|---|---|
| Settlement fee | 5.00% of wager | 2.50% of wager | 50% |
| Juice pool contribution | 0.10% of wager | 0.05% of wager | 50% |
| Combined effective rate | 5.10% | 2.55% | 50% |

Programme constraints, also verbatim: limited to **100 members**, aggregate distribution capped at
**$10,000,000**, bonus computed on the **greater** of referral volume or personal volume, payouts
denominated in SOL and settled on-chain.

**Prohibited claims**

- No "guaranteed profit", "risk-free", "can't lose", "free money".
- No implied certainty from the affiliate structure — "earns regardless" in the founder document
  refers to the bonus accruing on personal play, not to a profit guarantee for players.
- No invented RTP, win-rate, or payout percentages. The games' displayed multipliers are the only
  source.
- No invented social handles, Discord invites, Telegram links, or support emails. **None exist in
  the codebase**, so no asset may display one.

> ⚠ OPEN — Publish the official social/community handles in this document once they exist, so that
> creative never has to guess.

---

## 11. Compliance — mandatory on every asset

Drawn from the published Terms of Service surface (`src/app/terms/page.tsx`).

> ⚠ **The terms are a DRAFT pending legal review** — the page itself says so ("Version 1.0 · Last
> updated 2026-09-30 · Draft pending legal review") and renders operator-registration and
> governing-jurisdiction placeholders as-is. Treat every compliance line below as **the current
> published position**, and have counsel confirm before it is used in a paid campaign. Do not
> paraphrase the eligibility rules into a marketing claim.

| Requirement | Placement |
|---|---|
| **18+** age notice | Every ad, every overlay pack's stream description, every social post |
| Responsible gaming line | Every ad and landing asset |
| Self-exclusion / account-limit availability | Wherever the responsible-gaming line appears |
| Restricted jurisdictions | Any asset with a geographic target |
| No targeting of minors | Absolute; no school, youth, or "student" framing |

### 11.1 Restricted jurisdictions — a targeting constraint, not a footnote

The terms make eligibility explicit: a user must "be at least 18 years old, or the higher age of
majority in your jurisdiction" and must "not be located in, resident in, or a citizen of a Restricted
Jurisdiction". Restricted Jurisdictions are listed **non-exhaustively and include the United States**,
along with jurisdictions subject to sanctions or where crypto gaming is unlawful. Access via VPN or
any other circumvention is prohibited.

Consequences for marketing, which are not optional:

- **Do not run paid targeting into the United States.** The US is named in the restricted list.
- Do not produce creative that invites VPN use, "access from anywhere", or "region-free" framing —
  circumvention is itself a terms violation.
- Any geo-targeted campaign must be checked against §3 of the terms before launch, because the list
  is explicitly non-exhaustive.
- Affiliates and streamers carry the same restriction: a streamer promoting to a US audience is
  marketing a service those viewers cannot lawfully use.

Approved wording shape (**use the substance, keep it short**):

> 18+. Play responsibly. Self-exclusion and account-limit tools are available.

On a 1080p overlay, this line sits at **20px** in `#8e8e9a` at the bottom-left of any full-frame
scene, inside the 40px margin. It is not required on an in-game code bug — it is required on
starting/BRB/ending screens and on every static ad.

---

## 12. Production checklist

Run this before any asset leaves the building.

- [ ] Every hex value appears in Section 2 (or is one of the three approved one-offs: `#0b0b12`,
      `#14141e`, `#c2c2cc`)
- [ ] Type is CourbeSans 400/700, or `.font-gothic` **only** for wordmark / display numbers
- [ ] Nothing reads in `.font-gothic` on an overlay asset
- [ ] Every URL reads `juicer.games` — no `jxr.gg` anywhere (see 1.1)
- [ ] No paid targeting into the United States (restricted jurisdiction — see 11.1)
- [ ] No "VPN", "region-free" or "access from anywhere" framing (circumvention is prohibited)
- [ ] Code is uppercase, 4–16 chars, `A-Z 0-9 - _`, not a reserved word
- [ ] Code is legible at 50% scale of the delivered canvas
- [ ] Bottom 120px and right 340px are clear on every overlay
- [ ] Radii are 3px / 2px / 10px as specified — no pill buttons, no rounded chips at 8px+
- [ ] Win uses `#22c55e`, loss uses `#ff4d6a`
- [ ] No invented socials, handles, emails, RTPs or payout percentages
- [ ] 18+ and responsible-gaming line present where required
- [ ] Mascot is uncropped, unstretched, uncoloured, with 25% clear space
- [ ] File named per Section 8.6

---

## 13. Source index

Every value in this document traces to one of these files.

| Subject | Source |
|---|---|
| Font faces, core tokens, gold ramp, status, brand tokens, v2.0 tokens, surfaces, text, radii, shadows, type scale, motion keyframes, `.font-gothic` | `src/app/globals.css` |
| Page title, favicon/OG image, `themeColor` | `src/app/layout.tsx` |
| Token name, symbol, image URL, `external_url` | `public/jxr-token-metadata.json` |
| Referral domain, canonical link, code rules, reserved words | `src/lib/referral.ts` |
| Game accent colours, pin variants | `src/components/GamingClient.tsx` |
| Logo lockup, mascot size, token chip | `src/components/AppSidebar.tsx` |
| Lobby tile geometry, gradient, grid, glow | `src/components/games/GamePinCard.tsx` |
| Bet share card geometry and win/loss chips | `src/components/game/bet-share-card.tsx` |
| OG card canvas, layout, type sizes, colours | `src/app/api/og/bet/route.tsx` |
| Embedded font + brand icon for OG rendering | `src/app/api/og/bet/brand-assets.ts` |
| VIP tier colours and XP ladder | `src/lib/vip.ts` |
| VIP badge file mapping | `src/lib/badges.ts` |
| Affiliate percentages, cap, cohort size | `HOUSE-FOUNDER-AFFILIATE.md` |
| 18+, responsible gaming, self-exclusion, restricted jurisdictions | `src/app/terms/page.tsx` |

---

*End of document. Section 8 is a new build specification; everything else describes shipped
production values.*
