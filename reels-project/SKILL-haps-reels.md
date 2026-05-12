---
name: haps-reels
description: The only skill in this project. Use it on every request. It defines the end-to-end process for turning Haps Club website picks or newsletter content into an 8-slide Instagram reel deck, a PNG downloader page, and a caption. Triggers on "make a reel," "reel for this week," "reel from the newsletter," "reel about [topic]," or any variant. The process is proven — the canonical template is `html/reel-2026-05-11.html` in `Hilex2030/haps-club-assets`. Do not redesign from scratch.
---

# Haps Reels Skill

This is the single playbook for this project. Every conversation that asks for a reel follows it.

## The proven flow (do this every time)

```
1. Determine source        → site / newsletter / topic
2. Pull picks              → GitHub get_file_contents OR Gmail search
3. Verify (dates + links)  → web_search if needed
4. Pick 4 or 5 strongest   → editorial judgment, see rules below
5. Fork the template       → read html/reel-2026-05-11.html, copy it
6. Edit slides 3–6 (and 7) → swap illustrations, eyebrows, headlines, meta lines
7. Push deck HTML          → html/reel-YYYY-MM-DD.html
8. Push standalone SVGs    → images/reel-YYYY-MM-DD/01-open.svg ... 08-close.svg
9. Push downloader HTML    → html/download-reel-YYYY-MM-DD.html
10. Write caption          → hook + picks + CTA + 12–15 hashtags below dot break
11. Report three URLs + caption
```

Total time target: 10 minutes once picks are locked.

## 8-slide structure (never deviate without a reason)

| # | Purpose | Background | What goes on it |
|---|---------|------------|----|
| 01 | **Open** | Cream `#FAFAF7` with subtle navy/coral wash | Real Haps Club logo (navy variant) + "THIS WEEK IN LA" eyebrow + date range + tagline |
| 02 | **Hook** | Solid navy `#292f71` with coral radial glow lower-right | "5 picks. One city." or equivalent + brand promise ("Hand-picked. No filler. No sponcon.") |
| 03 | **Featured pick** | Themed to the venue (e.g. coral sunset for rooftop, navy night for Bowl show) | Hand-coded SVG illustration + eyebrow with date/time/price + big serif headline + neighborhood meta |
| 04 | **Pick 2** | Themed | Same shape as 03 |
| 05 | **Pick 3** | Themed | Same shape as 03 |
| 06 | **Pick 4** | Themed | Same shape as 03 |
| 07 | **CTA** | Solid coral `#FF6B47` with gradient overlay | "Plus N more picks" eyebrow + "The full list is online" big serif + navy URL pill "haps.club" |
| 08 | **Close** | Deep navy `#1a1f4d` with radial spotlight | Real Haps Club logo (white variant) + hairline accent + tagline + "@THEHAPSCLUB · HAPS.CLUB" |

For 5 picks instead of 4, combine two related picks on one slide (e.g. Friday doubleheader: salsa + jazz on one slide). Never go past 8 slides total — engagement drops.

## The real logo — always, never fabricated

Navy (light backgrounds, slide 01):
`https://cdn.jsdelivr.net/gh/Hilex2030/haps-club-assets@main/images/haps-club-logo.svg`

White (dark backgrounds, slide 08):
`https://cdn.jsdelivr.net/gh/Hilex2030/haps-club-assets@main/images/haps-club-logo-white.svg`

Embed inline as `<symbol>` definitions at the top of the deck HTML, then `<use href="#hc-logo-navy">` (or `#hc-logo-white`). The May 11 template already has both symbols defined — copy them as-is.

**Never create an "HC" monogram, circular badge, or any substitute mark.** This mistake has happened before. The wordmark is the wordmark.

## Illustration approach (hand-coded SVG only)

Each pick slide gets a geometric, editorial illustration that **evokes** the venue without faking it. Proven examples from May 11:

- **Rooftop restaurant** → coral sunset gradient sky, layered Hollywood Hills silhouettes, retractable dome arch with slats, palm tree, small cocktail glass
- **Free outdoor music** → split background, floating coral music notes, white saxophone silhouette, navy stylized dancers with one coral skirt swirl
- **Museum talk** → cream gradient background, navy classical pediment with fluted Doric columns, coral bead row, steps
- **Concert at Hollywood Bowl** → deep navy night gradient, scattered stars, crescent moon, Bowl shell as nested white arches with coral innermost arch, coral stage lights

Rules for illustrations:
1. Only brand colors — fading layers use `opacity` on navy/coral, never a different hue
2. Geometric, editorial — think Apple News graphics, NYT illustrations, not Disney
3. Anchor in the upper 50–55% of the slide — lower 45% is reserved for type
4. Never illustrate real people, real venue logos, real album covers, or copyrighted IP

If an illustration is hard to design, fall back to a giant serif numeral or typographic frame and let the type do the work.

## Brand discipline (lives in BRAND-reference.md, summarized here)

- Colors: only `#292f71` navy, `#1a1f4d` navy-deep, `#EEF0F8` navy-tint, `#FF6B47` coral, `#E54D2B` coral-deep, `#FFF1ED` coral-tint, `#FAFAF7` cream, `#0F1117` ink, `#6B6F7A` ink-muted. Never a third color.
- Fonts: Inter (sans, 400–800) + Instrument Serif (regular and italic). Never a third font.
- Voice: conversational, neighborhood-anchored, no exclamation marks in slide bodies or captions, no banned words (cancellation, monetize, democratize, streamline, unleash, leverage, ecosystem, journey, curated)

## Picking the picks

When sourcing from the live site:
1. Fetch `https://raw.githubusercontent.com/Hilex2030/haps-club/main/index.html`
2. Featured pick (slide 03) defaults to the site's Editor's Pick from "Today · The Pick"
3. Picks 2–4 from "This week" — prioritize dated events in the next 7 days
4. Optional 5th from "Mark your calendar" — a major upcoming thing worth flagging

When sourcing from the newsletter:
1. Search Gmail for the most recent newsletter draft or sent message
2. Use the lead pick as the featured slide
3. Pull the 3–4 next-strongest picks from the body

When sourcing from a topic:
1. Search Gmail and the live site for matches
2. Pick the 4–5 strongest verified picks on the topic
3. Bias toward currently-happening or this-week things over evergreens

## File naming

For a reel dated `YYYY-MM-DD` (Monday of the week, or current date for themed reels):

```
Hilex2030/haps-club-assets/
├── html/
│   ├── reel-YYYY-MM-DD.html              ← deck preview
│   └── download-reel-YYYY-MM-DD.html     ← one-click PNG export
└── images/
    └── reel-YYYY-MM-DD/
        ├── 01-open.svg
        ├── 02-hook.svg
        ├── 03-<topic-slug>.svg
        ├── 04-<topic-slug>.svg
        ├── 05-<topic-slug>.svg
        ├── 06-<topic-slug>.svg
        ├── 07-cta.svg
        └── 08-close.svg
```

Topic slug: kebab-case venue or event name (e.g. `sushisamba`, `bright-eyes`, `getty-villa`).

## How to build (the actual steps)

### Step A: Fork the deck template

1. `GitHub:get_file_contents` on `Hilex2030/haps-club-assets/html/reel-2026-05-11.html`
2. Save the entire file content as the starting point for your new deck
3. Keep byte-identical:
   - Entire `<head>` (meta, fonts, all CSS)
   - Both `<symbol>` definitions for the logos at top of `<body>`
   - Toolbar div
   - Slide 8 (close) — never changes structurally
4. Replace:
   - Slide 1: date range and tagline
   - Slide 2: "5 picks" number if different
   - Slides 3–6: full content (illustration + type)
   - Slide 7: "Plus N more picks" number

### Step B: Build standalone SVGs

For each of slides 1–8, create a standalone SVG file. Each needs:
- Its own `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1080 1920" width="1080" height="1920">` root
- Its own `<defs>` block with gradients used (deck HTML gradients use IDs that aren't in the standalone)
- For slides 01 and 08, embed the logo as a `<symbol>` inside `<defs>` of that standalone file (standalone can't reference the deck's symbols)

Reference: the May 11 standalones at `images/reel-2026-05-11/` are the working examples — copy their pattern.

### Step C: Fork the downloader

1. `GitHub:get_file_contents` on `Hilex2030/haps-club-assets/html/download-reel-2026-05-11.html`
2. Change only the `BASE` constant and the `slides` array in the script
3. Everything else (CSS, button, status text, Canvas render logic) stays byte-identical

BASE format:
```js
const BASE = 'https://cdn.jsdelivr.net/gh/Hilex2030/haps-club-assets@main/images/reel-YYYY-MM-DD/';
const slides = [
  { file: '01-open.svg',          label: '01 · Open' },
  { file: '02-hook.svg',          label: '02 · Hook' },
  { file: '03-<slug>.svg',        label: '03 · <Display name>' },
  { file: '04-<slug>.svg',        label: '04 · <Display name>' },
  { file: '05-<slug>.svg',        label: '05 · <Display name>' },
  { file: '06-<slug>.svg',        label: '06 · <Display name>' },
  { file: '07-cta.svg',           label: '07 · CTA' },
  { file: '08-close.svg',         label: '08 · Close' },
];
```

The downloader injects Google Fonts inline into each SVG before Canvas rasterization — don't strip that, or fonts fall back to generics.

### Step D: Push everything

Use `GitHub:push_files` for one batched commit containing the deck HTML, all 8 standalone SVGs, and the downloader HTML. Commit message: `Reel YYYY-MM-DD: [one-line summary]`.

### Step E: Write the caption

Template:

```
[Hook line — echoes slide 2: "Five picks for the week ahead in LA."]

[Featured pick — 2-3 sentences, neighborhood-anchored, ends with action prompt]

[Pick 2 — one paragraph]

[Pick 3 — one paragraph]

[Pick 4 — one paragraph]

[Optional Pick 5 — usually "mark your calendar" framing]

Full list, every Tuesday — link in bio.

.
.
.

#LosAngeles #ThingsToDoInLA #LALife [+ 4–5 neighborhood tags] [+ 2–3 topic tags] [+ 2–3 venue/event tags] #HapsClub
```

Hashtag formula: 12–15 total tags. Mix of broad LA, neighborhood-specific, topic, and brand.

## Report-back format (always this shape)

```
Done. Three URLs:

Preview deck:
https://hilex2030.github.io/haps-club-assets/html/reel-YYYY-MM-DD.html

Download 8 PNGs:
https://hilex2030.github.io/haps-club-assets/html/download-reel-YYYY-MM-DD.html

What's in it:
01. Open — logo + date
02. Hook — "N picks. One city."
03. [Featured pick name]
04. [Pick 2 name]
05. [Pick 3 name]
06. [Pick 4 name]
07. CTA — haps.club
08. Close — logo + tagline

Caption (copy as one block):

[caption goes here]
```

If the user wants a different pick, edit only the relevant slide and re-push — don't rebuild from scratch.

## Hard rules — these must not be broken

1. **Never fabricate** events, dates, venues, people, prices, or times. Verify or omit.
2. **Never use real photos** of venues, food, people, or events. SVG illustration only.
3. **Never use copyrighted imagery.** No album covers, movie stills, venue press photos, branded IP.
4. **Always use the real Haps Club logo** on slides 1 and 8. Never fabricate alternatives.
5. **Always verify dates** match the correct day-of-week before publishing.
6. **Never introduce a third brand color** or a third font.
7. **Never use exclamation marks** in slide bodies or captions.
8. **Never write to `.github/workflows/`** — MCP returns 403.
9. **Never put files in `Hilex2030/haps-club`** — that's the website repo. Reels go in `Hilex2030/haps-club-assets`.

## Known issues

- **Mobile multi-file downloads:** the download page works best on desktop Chrome or Safari. If the user is on mobile and wants PNGs, suggest they open the URL on a laptop.
- **GitHub MCP write permission:** Claude has write access to everything except `.github/workflows/`. No workaround — those files require manual edit by the user.
- **Cost:** the entire pipeline is $0 — SVG + browser-side Canvas, no AI image generation, no third-party services.
- **First-time GitHub Pages cache:** new files take ~60 seconds to be live at the `hilex2030.github.io/haps-club-assets/...` URL.

## Example session (canonical)

User: "reel for this week"

Claude:
1. Fetches live `index.html` from `Hilex2030/haps-club`
2. Identifies the Editor's Pick + 3–4 strongest This-week picks
3. Fetches `html/reel-2026-05-11.html` from `Hilex2030/haps-club-assets` as the template
4. Builds the new deck HTML, swapping illustrations and type for the new picks
5. Builds 8 standalone SVGs
6. Builds the downloader HTML
7. `push_files` with all 10 files (1 deck + 8 SVGs + 1 downloader) in one commit
8. Writes caption per template
9. Reports the three URLs and the caption

Total time: under 10 minutes.

That's the model. Do this every time.
