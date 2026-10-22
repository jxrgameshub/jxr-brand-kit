# Typography — reference only, font files not distributed

The JXR Gaming platform is set in **Courbe Sans**, weights **400 (regular)** and **700 (bold)** only.
There is no 500, no 600, no 900.

The font binaries are **deliberately not published in this repository.** Courbe Sans is a licensed
commercial typeface and this repo is public — publishing the OTF/TTF here would be redistribution,
which the licence does not allow. Nothing about it is open source or freely redistributable.

---

## Licence status

| Item | Detail |
|---|---|
| Typeface | **Courbe Sans** |
| Designer / rights holder | **Loukas Nicolaou** |
| Trademark | "Courbe Sans" is a trademark of Loukas Nicolaou |
| Weights used | 400, 700 |
| Included in this repo | **No** |
| Redistribution permitted | **No** |

---

## Getting the files (platform use only)

Access to the font files is granted **per project, for use on the JXR Gaming platform and its
sanctioned channels** — not for redistribution, resale, bundling into another product, or uploading
to font libraries, CDNs, or design-tool team libraries that are publicly shared.

To request access, [open an issue](../issues/new) in this repository stating:

1. The organisation and the person who will hold the licence seat.
2. What the assets are for (platform UI, stream overlays, video, print, etc.).
3. Whether the files will be self-hosted on `juicer.games` or installed locally.

Requests are routed to the rights holder. Do not obtain the font from a third-party download site —
those copies are not licensed to you and are frequently out of date.

---

## Filenames (for reference, if you have been granted access)

The files in the application source carry a real double extension. Preserve it — code depends on it.

| Format | Path in the app |
|---|---|
| OpenType (400 + 700) | `public/CourbeSans/CourbeSans.otf.otf` |
| TrueType (400 + 700) | `public/CourbeSans/CourbeSans.ttf.ttf` |

Web paths: `/CourbeSans/CourbeSans.otf.otf`, `/CourbeSans/CourbeSans.ttf.ttf`

---

## Using a substitute until access is granted

If you are producing a draft and do not yet have the font, **do not pick a lookalike and call it
done** — it will not match the live product. Mark the artwork as a draft and substitute with the
documented fallback stack so metrics stay predictable:

```css
font-family: 'CourbeSans', 'Inter', -apple-system, BlinkMacSystemFont,
             'Segoe UI', Roboto, sans-serif;
```

Inter is the closest of the documented fallbacks. Only 400 and 700 are relevant — a design tool will
synthesise 500/600/900 and it will look wrong. Increase size or use 700 instead.

---

## Display / wordmark face

The "Juicer" wordmark and heavy display numbers do **not** use Courbe Sans. They use a system stack
(`.font-gothic`) that ships with the operating system — nothing to license, nothing to install:

```
'Arial Black', 'Impact', 'Franklin Gothic Heavy', 'Haettenschweiler', system-ui, sans-serif
```

Because it is a system stack it renders differently on macOS, Windows and Linux. **Never use it on a
stream overlay or in video**, where glyph metrics have to be predictable — set the wordmark as vector
art or use Courbe Sans 700 there.

Full rules: [`../BRAND-GUIDELINES.md`](../BRAND-GUIDELINES.md) §3.
