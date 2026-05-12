# Haps Club Reels — Claude Project Setup

This folder contains everything needed to spin up a separate Claude project dedicated to creating Haps Club social media reels. The project pulls picks from the website or newsletter, builds 8-slide reel decks as SVG, generates standalone slide files, builds a PNG downloader, and writes the caption — every time.

## What's in here

```
reels-project/
├── README.md                          ← this file
├── SYSTEM-INSTRUCTIONS.md             ← paste this into the new project's instructions field
├── SKILL-haps-reels.md                ← upload to project knowledge
└── BRAND-reference.md                 ← upload to project knowledge
```

## Setup (5 minutes)

1. **claude.ai → New Project.** Name it "Haps Club Reels."
2. **Open `SYSTEM-INSTRUCTIONS.md`** in this folder. Copy the entire contents. Paste into the new project's "Custom instructions" field.
3. **Upload `SKILL-haps-reels.md`** to the project's knowledge files.
4. **Upload `BRAND-reference.md`** to the project's knowledge files.
5. **Connect GitHub MCP** with write access to `Hilex2030/haps-club-assets` (push) and read access to `Hilex2030/haps-club` (pull current site state). If pulling from the newsletter, also connect Gmail MCP authenticated as `newsletter@haps.club`.

That's it. Test by typing "reel for this week."

## What the project does

Given any of these trigger phrases:

- "reel for this week" → pulls latest picks from `haps.club`, builds reel
- "reel from the newsletter" → pulls latest newsletter from Gmail, builds reel
- "reel about [topic]" → builds a themed reel (e.g. "reel about restaurants this week")
- "make a reel" → asks which source to use

The output is always the same shape:

1. A live preview URL where you see all 8 slides on screen
2. A separate download URL where you click once and 8 PNGs save to your computer
3. A caption block ready to copy into Instagram

## Why a separate project rather than putting this in the main Haps Club project

- One job, one focus — the system prompt is laser-tuned for reels only
- The main Haps Club project handles editorial (website refreshes, newsletter drafting). This project handles distribution. Clean separation.
- You can hand this project to a contractor without giving them the rest of the operation

## Updating the project

Whenever the reel format improves, update `SKILL-haps-reels.md` in this folder and re-upload to the project. The skill is the memory.
