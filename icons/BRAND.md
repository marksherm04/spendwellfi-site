# SpendWellFi brand system

## The mark

A geometric **S** with a slim vertical stem running through it. Read primarily
as the brand letter; on second glance the vertical stroke is the visual DNA
of a `$` — a quiet financial signal rather than a literal one.

The IBM-stripes approach: hide the secondary meaning *inside* the primary
form, so the brand can outgrow the category without looking like a fintech app.

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
