# Music Kollab — Marketing Site

Landing page and marketing website for [Music Kollab](https://musickollab.app).

## Overview

This is a static marketing site for collecting waitlist signups before the Music Kollab app launches.

**Live site:** https://musickollab.app

## Tech Stack

- Static HTML/CSS/JS
- Hosted on Vercel
- Email collection via ConvertKit (TODO: connect)

## Local Development

Just open `public/index.html` in your browser, or use a local server:

```bash
# Using Python
python -m http.server 8000 --directory public

# Using Node
npx serve public
```

## Deployment

This repo is connected to Vercel. Push to `main` to deploy.

```bash
git push origin main
```

## Structure

```
marketing-site/
├── public/
│   ├── index.html      # Landing page
│   ├── favicon.svg     # Site favicon
│   └── og-image.png    # Social sharing image (TODO: create)
├── vercel.json         # Vercel config
└── README.md
```

## TODO

- [ ] Connect form to ConvertKit/Buttondown
- [ ] Create og-image.png (1200x630) for social sharing
- [ ] Create apple-touch-icon.png (180x180)
- [ ] Add Google Analytics or Plausible
- [ ] Create /privacy and /terms pages

## Related Repos

- [kollab-app](https://github.com/pdreed17/kollab-music-app) — React Native mobile app

---

© 2026 Music Kollab
