# Changelog

## v1.1 — public distribution

Assets extracted from the live application source, unchanged in content from v1.0 apart from the
items below.

**Removed from distribution**

- `03-typography/CourbeSans-Regular_Bold.otf`
- `03-typography/CourbeSans-Regular_Bold.ttf`

Courbe Sans is a licensed commercial typeface — "Courbe Sans" is a trademark of Loukas Nicolaou.
Hosting the binaries in a public repository is redistribution, which the licence does not permit.
The typeface is now **referenced** rather than shipped: [`03-typography/README.md`](03-typography/README.md)
documents the licence position and how to request access for platform use. Every other checksum in
[`MANIFEST.txt`](MANIFEST.txt) is identical to v1.0, so the artwork itself has not been touched.

**Added**

- `LICENSE` — usage permission for the assets, excluding the typeface.
- `.gitattributes` — binary handling for images/video, diffable text for SVG/CSS/JSON.
- `CHANGELOG.md` — this file.

**Edited**

- `README.md` — typography section now links to the reference doc instead of listing font files.
- `BRAND-GUIDELINES.md` §3.1 — same, plus the rights holder.

## v1.0 — internal hand-off bundle

Initial kit: logo set, palette, typography, OG template, Kick overlay suite, 14 VIP badges, Telegram
sticker pack, campaign art, brand guidelines and manifest.
