# Haps Club Brand Reference

Single source of truth for everything brand-related. This file lives in this project's knowledge so brand drift is impossible.

## Colors (only these)

```
--navy:         #292f71    Primary brand. From the logo.
--navy-deep:    #1a1f4d    Deep backgrounds, slide 08 close
--navy-tint:    #EEF0F8    Soft backgrounds, slide 05 Getty gradient top
--accent:       #FF6B47    Warm coral. Single accent.
--accent-deep:  #E54D2B    Coral hover, sometimes used for eyebrows
--accent-tint:  #FFF1ED    Sunset sky top in slide 03 SUSHISAMBA
--bg:           #FAFAF7    Warm off-white. Slide 01 background.
--ink:          #0F1117    Body text
--ink-3:        #6B6F7A    Muted text, captions
```

Never introduce a third color. Visual interest comes from gradient layering or illustration detail, not new hues.

## Typography (only these)

| Family | Use | Weights |
|---|---|---|
| Inter | UI, eyebrows, meta lines, captions | 400, 500, 600, 700, 800 |
| Instrument Serif | Headlines, hero greeting, italic emphasis | 400, italic 400 |

Google Fonts link (must be in every deck):

```html
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&family=Instrument+Serif:ital@0;1&display=swap" rel="stylesheet">
```

Never introduce a third font.

## Logo (real wordmark, always)

The Haps Club logo is the hand-lettered "Haps Club" wordmark — a flowing italic "Haps" connected to a bold "CLUB." Two color variants:

| Variant | When | URL |
|---|---|---|
| Navy | Slide 01 (cream background) | `https://cdn.jsdelivr.net/gh/Hilex2030/haps-club-assets@main/images/haps-club-logo.svg` |
| White | Slide 08 (deep navy background) | `https://cdn.jsdelivr.net/gh/Hilex2030/haps-club-assets@main/images/haps-club-logo-white.svg` |

ViewBox: navy is `0 0 1100 1100`, white is `0 0 900 900`.

In the deck HTML, embed both as `<symbol>` defs at the top of `<body>`, then `<use href="#hc-logo-navy">` and `<use href="#hc-logo-white">`. The May 11 template has the full path data embedded already — copy it.

**Never substitute a fabricated mark.** No "HC" monogram, no circular badge, no simplified version. The wordmark is the wordmark.

## Voice

A real person who lives in LA and reads books — not a startup writing copy.

**Do:**
- Conversational headlines ("SUSHISAMBA's rooftop is the most fun room in LA right now")
- Always name the neighborhood (West Hollywood, Highland Park, Echo Park, etc.)
- Natural time phrasing ("Doors 7:15, film 8:30")
- Em dashes for parentheticals — they work

**Don't:**
- Exclamation marks in slide bodies or captions, ever
- These banned words: cancellation, monetize, democratize, streamline, unleash, leverage, ecosystem, journey, curated
- Promotional voice ("can't miss," "the best," "must-see," "don't sleep on")
- Stack of marketing taglines

## Defaults

| What | Default |
|---|---|
| City | Los Angeles |
| Newsletter cadence | Tuesday mornings |
| Caption CTA | "Full list, every Tuesday — link in bio." |
| Subscribe headline | "One email, every Tuesday morning." |
| Reel dimensions | 1080 × 1920 (9:16 vertical) |
| Slide count | 8 |
| Hashtag count | 12–15 |

## Live URLs to remember

- Website: https://haps.club
- Live `index.html` raw: https://raw.githubusercontent.com/Hilex2030/haps-club/main/index.html
- Assets repo: https://github.com/Hilex2030/haps-club-assets
- Assets via jsDelivr CDN: https://cdn.jsdelivr.net/gh/Hilex2030/haps-club-assets@main/
- Asset index: https://github.com/Hilex2030/haps-club-assets/blob/main/images/INDEX.md
- Canonical reel template: https://hilex2030.github.io/haps-club-assets/html/reel-2026-05-11.html
- Canonical downloader: https://hilex2030.github.io/haps-club-assets/html/download-reel-2026-05-11.html

## Repository write boundaries

- **`Hilex2030/haps-club`:** website repo. Don't push reel assets here.
- **`Hilex2030/haps-club-assets`:** assets repo. All reel work goes here.
- **`.github/workflows/` in either repo:** GitHub MCP returns 403. Must be edited by the user directly.

## Cost discipline

The entire reel pipeline costs $0 to run — SVG + browser-side Canvas, no AI image generation, no third-party rendering services. Keep it that way. If a feature would add monthly cost, surface it before adding.
