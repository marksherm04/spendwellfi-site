# SpendWellFi brand system

## The brand identity

**Bespoke wordmark + coin mark.** Two pieces that share one signature element.

The **wordmark** is `SpendWell·Fi` — the brand name set in heavy Plus Jakarta
Sans 800 with the middle joined by a sage-green dot. That dot is the brand's
singular visual element: it acts as punctuation in the wordmark (separating
the action *Spend Well* from the financial designation *Fi*) and as the
source from which the standalone icon mark is built.

The **coin mark** is the sage dot scaled up to circle size, carrying a bold
white `S` inside. It's what goes anywhere the full wordmark can't — favicon,
app icon, small UI badges.

Why bespoke wordmark over a symbolic icon:
- The wordmark *is* the merchandise. Patagonia, Supreme, Stüssy, Carhartt:
  the strongest small brands are recognized by their wordmark, not a separate
  icon. A heavy custom-set "SpendWell·Fi" embroidered on a hat front carries
  the brand the way no spiral or letterform could.
- One memorable element. The sage dot/coin is what repetition trains into
  visual recognition. The same element appears in every brand surface.
- The icon problem solves itself. When someone needs an icon-only version,
  the dot scales up into the coin mark. No second design system to maintain,
  no semantic compromise.

## Brand name in copy

The wordmark style (`SpendWell·Fi` with sage dot) is the visual identity —
used for logos, headers, footers, merchandise.

In running copy, page titles, button text, and email subject lines, write
the brand as one word: **SpendWellFi**. Patagonia uses its custom wordmark
on shirts and writes "Patagonia" in body text. Same idea here.

## Files

| File                         | Purpose                                           |
|------------------------------|---------------------------------------------------|
| `mark.svg`                   | Bare logomark, uses `currentColor` (inherit)      |
| `favicon.svg`                | Self-contained favicon (sage tile + white mark)   |
| `logo-horizontal.svg`        | Mark + "SpendWellFi" wordmark on one line         |
| `appicon-source.svg`         | 1024×1024 source for the desktop app icons        |

## Colors

| Token         | Hex       | Use                                  |
|---------------|-----------|--------------------------------------|
| Sage          | `#5B8A72` | Primary brand color, mark background |
| Sage deep     | `#2F5C42` | Hover states, dark sections          |
| Sage light    | `#EEF5EE` | Tinted backgrounds                   |
| Ink           | `#1C1917` | Wordmark, body text                  |
| Cream         | `#F7F5F2` | Page background                      |

## Wordmark

- Typeface: **Plus Jakarta Sans 800** (extra bold)
- Letter spacing: `-0.025em` (tight)
- Case: as-written — `SpendWellFi` (no all-caps treatment)
- Don't reflow as `Spend Well Fi` or `SpendWellFi.` etc. The camel case
  carries meaning: *Spend*, *Well*, *Fi(nance)*.

## Don'ts

- Don't rotate, skew, or outline the mark.
- Don't recolor it in non-brand colors (gold, blue, etc.) — that breaks the
  calm/trustworthy register the rest of the brand depends on.
- Don't shrink the mark below 16×16. Below that, use the favicon variant.
- Don't add drop shadows or glow effects. The mark relies on its silhouette.

## Generating the desktop app icons

Tauri ships every Windows/macOS icon size from a single high-res PNG:

```bash
# 1. Export icons/appicon-source.svg to a 1024×1024 PNG
#    (Inkscape, Figma, Affinity Designer, or `rsvg-convert`)

# 2. Hand it to Tauri's icon generator
cd offlinefinance/src-tauri
cargo tauri icon ../../spendwellfi-site/icons/appicon-source.png
```

This writes `32x32.png`, `128x128.png`, `128x128@2x.png`, `icon.icns`
(macOS) and `icon.ico` (Windows) into `src-tauri/icons/` — exactly the
files `tauri.conf.json` already references.
