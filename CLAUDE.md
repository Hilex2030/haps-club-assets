# Haps Club Assets — Claude Custom Connection

This file defines how Claude connects to the `haps-club-assets` repository.

## ⚠️ Two repos — read this first

There are two related repositories. Don't confuse them:

| Repo | Purpose | Live? |
|------|---------|-------|
| **`Hilex2030/haps-club`** | The **website**. `index.html` at the root is the daily-recommendations homepage served at https://hilex2030.github.io/haps-club/. Updated weekly with new picks. Maintained via the `haps-club-website` skill. | Yes — GitHub Pages |
| **`Hilex2030/haps-club-assets`** (this repo) | **Brand-asset store.** Images, HTML fragments, generated artifacts, and this `CLAUDE.md`. Not the website. Referenced by other projects (newsletter logo URLs, brand assets, misc storage). | Files accessible via raw URLs and a static gallery at https://hilex2030.github.io/haps-club-assets/ |

**Rule:** If the user says "push to the site" or "update Haps Club" or "add this week's picks," that's `Hilex2030/haps-club`. If they say "drop this image somewhere I can hotlink it" or "save this artifact," that's `haps-club-assets`.

## Repository Identity (this repo)

- **Repo:** `Hilex2030/haps-club-assets`
- **Purpose:** Asset storage for Haps Club — images, HTML pages, and artifacts
- **Visibility:** Public
- **Branch:** `main`

## Base URLs

```
RAW:  https://raw.githubusercontent.com/Hilex2030/haps-club-assets/main
API:  https://api.github.com/repos/Hilex2030/haps-club-assets/contents
PAGE: https://hilex2030.github.io/haps-club-assets
```

## Folder Structure

| Folder      | Contents                        | Raw URL prefix                                                                    |
|-------------|---------------------------------|-----------------------------------------------------------------------------------|
| `images/`   | PNG, JPG, SVG, GIF assets       | `https://raw.githubusercontent.com/Hilex2030/haps-club-assets/main/images/`      |
| `html/`     | HTML pages & generated artifacts| `https://raw.githubusercontent.com/Hilex2030/haps-club-assets/main/html/`        |
| `artifacts/`| PDFs, JSON, exports, misc files | `https://raw.githubusercontent.com/Hilex2030/haps-club-assets/main/artifacts/`   |

## How to Access Files

### Fetch a specific file (raw content)
```
https://raw.githubusercontent.com/Hilex2030/haps-club-assets/main/<folder>/<filename>
```

### List files in a folder (GitHub API — no auth required for public repo)
```
https://api.github.com/repos/Hilex2030/haps-club-assets/contents/<folder>
```

### Check if a file exists
Navigate to the raw URL. A 200 response means it exists; 404 means it does not.

## Claude Integration Notes

- All files are publicly accessible — no token needed for read access.
- To list available assets, Claude should call the GitHub Contents API endpoint above.
- To read a file, Claude should fetch the raw URL directly.
- This repository's `index.html` is a static **asset gallery**, not the Haps Club homepage. The actual homepage lives in `Hilex2030/haps-club`.
- When Claude says "not found", it usually means the file hasn't been uploaded yet OR the filename/folder path is wrong. Use the API listing endpoint to verify what files actually exist before attempting to fetch them.

## Uploading New Assets

### Via GitHub Web UI
1. Navigate to the target folder in this repo.
2. Click **Add file → Upload files**.
3. Drag & drop your file, then commit to `main`.

### Via git CLI
```bash
git clone https://github.com/Hilex2030/haps-club-assets.git
cd haps-club-assets
cp ~/path/to/file images/   # or html/ or artifacts/
git add .
git commit -m "Add <filename>"
git push
```

## Troubleshooting "Not Found" Errors

1. **Verify the file exists** — call the API listing endpoint for the target folder.
2. **Check exact filename** — filenames are case-sensitive on GitHub.
3. **Check the folder** — make sure you're looking in `images/`, `html/`, or `artifacts/`.
4. **Check the repo** — homepage updates belong in `Hilex2030/haps-club`, not here.
5. **Wait for propagation** — raw.githubusercontent.com can take ~30 seconds to reflect new commits.
6. **Use the API URL** instead of raw URL as a fallback:
   `https://api.github.com/repos/Hilex2030/haps-club-assets/contents/<folder>/<filename>`

## Quick Reference — Copy-Paste URLs

```
Website repo:        https://github.com/Hilex2030/haps-club
Website live URL:    https://hilex2030.github.io/haps-club/

This repo (assets):  https://github.com/Hilex2030/haps-club-assets
Assets gallery:      https://hilex2030.github.io/haps-club-assets/

List images:    https://api.github.com/repos/Hilex2030/haps-club-assets/contents/images
List html:      https://api.github.com/repos/Hilex2030/haps-club-assets/contents/html
List artifacts: https://api.github.com/repos/Hilex2030/haps-club-assets/contents/artifacts

This file (raw): https://raw.githubusercontent.com/Hilex2030/haps-club-assets/main/CLAUDE.md
```
