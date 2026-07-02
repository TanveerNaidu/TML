# Tanveer Naidu — Photography

Personal photography portfolio. Built as a single-page HTML site with drag-to-explore galleries, a scene index with hover previews, a full-screen lightbox, and a Tweaks panel for live customisation.

---

## Live site

Deployed via [Vercel](https://vercel.com).

---

## Project structure

```
├── index.html          # Main page (hero + scroll-driven About cinema + galleries)
├── Full Gallery.html   # Full-list gallery view
├── styles.css          # All styles + design tokens
├── app.js              # Vanilla JS — nav, galleries, lightbox, cursor, preloader
├── image-slot.js       # Drag-and-drop image placeholder web component
├── gallery-spiral.js   # Full Gallery page logic
├── vercel.json         # Security headers config for Vercel
│
├── frames/             # 151 JPGs for the scroll-scrubbed cinema sequence (hero → about)
├── feature-bg.jpg      # Feature section video poster
├── feature-bg.mp4      # Feature section background video
│
├── work-*.jpg          # Frames & Moments gallery
├── ind-*.jpg           # India gallery
├── nat-*.jpg           # Nature gallery
├── sa-*.jpg            # South Africa gallery
└── str-*.jpg           # Street gallery
```

---

## Running locally

No build step needed. Open `index.html` directly in a browser, or use any static file server:

```bash
# Python
python3 -m http.server 8000

# Node (npx)
npx serve .
```

Then visit `http://localhost:8000`.

---

## Deploying to Vercel

### First time

1. Push this folder to a GitHub repository.
2. Go to [vercel.com](https://vercel.com) → **Add New Project**.
3. Import the GitHub repository.
4. Leave all settings at their defaults — Vercel auto-detects a static site.
5. Click **Deploy**.

Your site will be live at `https://<your-project>.vercel.app`.

### Updating the site

```bash
git add .
git commit -m "Update photos / content"
git push
```

Vercel auto-deploys on every push to `main`.

---

## Replacing photos

All photos are standard `<img>` tags inside the gallery frames. To swap one:

1. Add your new file to the project root.
2. Open `index.html` and find the frame — search for the current filename (e.g. `work-seagull.jpg`).
3. Replace the `src` value with your new filename.
4. Adjust `object-position` on the same `<img>` if the crop needs tweaking.

---

## The scroll-driven About sequence

Scrolling from the hero into About plays back the `frames/` image sequence on a `<canvas>`, synced 1:1 to scroll position, with staged text "beats" fading in/out over it. A single wheel/touch/keyboard gesture auto-scrolls smoothly between the hero and the About end-state; native smooth-scrolling is intentionally suspended during that animation to avoid double-easing.

---

## Sections

| Section | ID |
|---|---|
| Hero + About (cinema) | `#cinema` |
| Frames & Moments | `#work` |
| Scenes & Series index | `#index` |
| South Africa | `#south-africa` |
| India | `#india` |
| Nature | `#nature` |
| Street | `#street` |
| Stats | — |
| Feature quote | — |
| Contact | `#contact` |

---

## Tech

- Vanilla HTML / CSS / JS — no framework, no build step
- React 18 + Babel standalone — Tweaks panel only
- Google Fonts: Archivo, Anton, Space Mono, Space Grotesk
- Custom drag-and-drop `<image-slot>` web component
