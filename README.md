# Baked Apps

Fresh apps, baked daily.

**[bakedapps.cloud](https://bakedapps.cloud)**

An App Store-inspired catalog of everything built at Baked Apps — AI tools, developer utilities, and games. Built entirely with vanilla HTML, CSS, and JS — no frameworks, no build step, no dependencies. Just edit `apps.json` and deploy.

This catalog is adapted from [f/appetit](https://github.com/f/appetit) (Appétit), the same open-source template behind [wvw.dev](https://wvw.dev).

## Features

- App Store UI — sidebar navigation, featured carousel, app cards, detail pages
- Dark & light themes — system preference detection with manual toggle, persisted in localStorage
- JSON-driven — all apps, categories, and featured items defined in a single `apps.json`
- Categories — AI, Productivity, Developer Tools, Games, Lifestyle, Web Apps
- Search — instant client-side filtering across names, descriptions, and features
- Responsive — desktop sidebar collapses on mobile
- Zero dependencies — pure HTML/CSS/JS, deploys anywhere as static files

## Quick Start

```bash
python3 -m http.server 8080
```

Open `localhost:8080` and you're running.

## Adding an app

Edit `apps.json`. Each app entry supports:

```jsonc
{
  "id": "my-app",
  "name": "My App",
  "subtitle": "A short tagline",
  "description": "One-liner for list views.",
  "longDescription": "Full description for the detail page.",
  "icon": "icons/my-app.png",         // vendored locally, or use iconEmoji: "🚀"
  "iconStyle": { "objectFit": "contain" },
  "category": ["ai", "productivity"], // see categories below
  "platform": "Web",
  "price": "Free",                    // any non-"Free" value is treated as paid/freemium
  "homepage": "https://my-app.bakedapps.cloud",
  "features": ["Feature one", "Feature two"],
  "screenshots": ["icons/my-app-1.png"]
}
```

`github`, `language`, and `requirements` are optional — the UI hides those rows entirely when they're not set, since most of these apps are closed-source products rather than open-source repos.

Categories are defined in two places that need to stay in sync: the `categories` array in `apps.json` (used for category page titles) and the hardcoded sidebar list plus icon set near the top of `app.js`.

## Setting featured apps

```json
"featured": [
  {
    "id": "my-app",
    "headline": "NEW",
    "title": "A catchy headline.",
    "subtitle": "A longer description for the featured banner."
  }
]
```

## Deploy

Push to GitHub and enable Pages, or drop the files on any static host (Netlify, Vercel, Cloudflare Pages, S3, etc). A `CNAME` file is already set to `bakedapps.cloud`.

## File Structure

```
├── index.html      Main HTML shell
├── style.css       All styles (dark + light themes)
├── app.js          Routing, rendering, carousel, modals
├── apps.json        All app data — edit this file
├── logo.svg         App icon / favicon
├── icons/           Vendored app icons
├── CNAME            Custom domain for GitHub Pages
└── .nojekyll         Prevents Jekyll processing
```

## License

MIT — same as the upstream [f/appetit](https://github.com/f/appetit) template.
