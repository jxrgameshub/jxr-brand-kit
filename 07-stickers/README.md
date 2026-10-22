# Floating Juicebox — Telegram emoji & stickers

Custom profile emoji built from the app's Juicebox logo
(`public/juicebox_sticker.webp`, 512×512, transparent). The animation mirrors the
in-app `.logo-float-glow` (3 s ease-in-out bob + orange `#f97316` glow pulse).

## Files

| File | Format | Size | Use |
|---|---|---|---|
| `juicebox-floating-100.webm` | VP9 WebM, alpha, 100×100, 30 fps, 3.0 s, no audio | ~11 KB | **Custom emoji next to your name** (Premium) |
| `juicebox-100.png` | PNG RGBA, 100×100 | ~17 KB | Static custom-emoji alternative |
| `juicebox-floating-512.webm` | VP9 WebM, alpha, 512×512, 30 fps, 3.0 s, no audio | ~57 KB | Animated **video sticker** (free for everyone) |
| `juicebox-512.png` | PNG RGBA, 512×512 | ~245 KB | Static sticker / general use |

Telegram limits (core.telegram.org/stickers): custom-emoji static images exactly
100×100; custom-emoji video WebM VP9 ≤ 3 s, ≤ 256 KB, no audio, transparency OK;
static stickers one side exactly 512 px, ≤ 512 KB. All four files comply.

## Put it next to your name (custom emoji)

1. Using custom emoji requires **Telegram Premium**.
2. Open **@Stickers** → `/newemoji` → name the pack (e.g. "Floating Juicebox").
3. Upload `juicebox-floating-100.webm` **as a file/document** (a photo upload is
   rejected/lossy).
4. When asked, map the emoji to a standard one (e.g. 🧃).
5. `/publish` → pick the short link → pack lives at `t.me/addemoji/<short>`.
6. Profile → edit name → emoji button → insert 🧃 from your pack into the name.

## Animated sticker route (viewers don't need Premium)

- @Stickers → follow the **video sticker** flow (`/newvideo`) → upload
  `juicebox-floating-512.webm` as document → map an emoji → `/publish`.

## Static sticker route

- @Stickers → `/newpack` → upload `juicebox-512.png` (or the original
  `public/juicebox_sticker.webp`, 47 KB) as document → map → `/publish`.

All files are also served from `/telegram-emoji/<filename>` on the site for easy
download onto a phone.
