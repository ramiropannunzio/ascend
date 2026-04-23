# Ascend — Brand Assets Index

## Structure

```
Assets/
├── Logo/
│   ├── Wordmark/       ← Full "ascend" wordmark SVG
│   │   ├── Light/      ← White version (for dark BGs: Midnight, Land, Purple)
│   │   ├── Dark/       ← Black/Neutral-0 version (for light BGs: Sky, White, Neutral-95)
│   │   └── Color/      ← Purple version (for white/neutral BGs)
│   └── Icon/           ← Arrow isotipo SVG only
│       ├── Light/      ← White arrow
│       ├── Dark/       ← Black arrow
│       └── Color/      ← Purple arrow
├── Imagery/            ← Brand photography
│   ├── Travel/         ← Aerial, planes, destinations
│   ├── Lifestyle/      ← Executive travelers, business settings
│   └── Product/        ← App screenshots, WhatsApp mockups, dashboard
└── Patterns/           ← Graphic language elements
    ├── FlightPath/     ← Dashed flight-path SVGs (1.5pt stroke)
    └── Window/         ← Rounded window frames, overlays
```

## Usage from Slides/

From `Slides/ascend-deck-template.html`, reference assets via:
```html
<img src="../Assets/Logo/Icon/Light/ascend-arrow-light.svg" alt="Ascend">
<img src="../Assets/Imagery/Travel/aerial-landscape.jpg" alt="">
```

## Usage from other brand outputs

From any file in `Brand Assets/`, use:
```html
<img src="Assets/Logo/Wordmark/Dark/ascend-wordmark-dark.svg" alt="Ascend">
```

## Naming convention

| Type | Pattern | Example |
|---|---|---|
| Logo SVG | `ascend-{type}-{variant}.svg` | `ascend-arrow-light.svg` |
| Photography | `{category}-{description}.jpg` | `travel-aerial-forest.jpg` |
| Patterns | `flight-path-{variant}.svg` | `flight-path-dashed-white.svg` |

## Logo variants needed

| Variant | Icon (arrow) | Wordmark (arrow + "ascend") |
|---|---|---|
| Light (white) | For Midnight, Land, Purple BGs | For Midnight, Land, Purple BGs |
| Dark (black) | For Sky, White, Neutral-95 BGs | For Sky, White, Neutral-95 BGs |
| Color (purple) | For White, Neutral-95 BGs | For White, Neutral-95 BGs |

## Current state

- Fonts: in `../Fonts/` (FT System Trial Grotesk + Mono)
- Logo: inline SVG placeholder in deck template (pending real isotipo export from Figma)
- Imagery: placeholder divs (pending real photography)
- Patterns: inline SVG flight-paths in deck (pending standalone exports)
