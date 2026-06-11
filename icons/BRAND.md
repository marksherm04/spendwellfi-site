# SpendWellFi brand system

## The mark

**The Compound Spiral.** A geometric spiral inspired by the golden ratio.
Compound growth — interest on interest, the foundational concept of personal
finance — *is* exponential growth, and exponential growth drawn in 2D is a
spiral. The mark literally embodies what the app helps you do.

Why a spiral over a dollar sign or chart:
- Nothing else in the personal finance category looks like this. The space
  is full of dollar signs, piggy banks, charts, and abstract geometric blobs.
  A spiral immediately stands apart.
- Strong silhouette. Embroiders cleanly, prints in single color, holds up at
  favicon size. The mark earns its place on merchandise, not just a webpage.
- The story is a sentence. *"It's a compound spiral — money working on
  itself."* That's a t-shirt-conversation-starter, not a forgettable mark.

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
