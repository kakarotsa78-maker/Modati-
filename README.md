# ModatiAR

**ModatiAR** is a bilingual (Arabic / English) Minecraft mod browser. It connects live to the [Modrinth](https://modrinth.com) API, so the catalog of mods, search, and download links are always current — there's no static database to maintain.

## Features

- **Live Modrinth integration** — searches and lists mods directly from the Modrinth API (`api.modrinth.com`). No backend or API key required; all requests run client-side.
- **Bilingual interface (AR / EN)** — a toggle in the header switches the entire UI, including layout direction (the page flips to right-to-left automatically in Arabic).
- **Search and filter** — full-text search plus category filters (adventure, magic, optimization, etc.), with pagination via a "Load more" button.
- **Guided downloads** — clicking **Download** on a mod opens a popup where the user must choose:
  1. **Mod loader** (Fabric, Forge, Quilt, NeoForge, etc.)
  2. **Game version** (e.g. `1.20.1`, `1.8.9`)

  The app checks Modrinth for a file that matches both choices and only enables the Download button once a valid file is found. The actual file then downloads directly from Modrinth's CDN.
- **Dark, distinctive UI** — a near-black "obsidian" theme with a single warm amber accent and a green secondary accent, custom typography (Sora + IBM Plex Mono, Tajawal for Arabic), and a small animated "crafting grid" graphic in the hero section as a nod to Minecraft.

## How it works

This is a single self-contained `modatiar.html` file — no build step, no server, no dependencies to install.

1. Open `modatiar.html` in any modern browser.
2. The page automatically loads the latest mods from Modrinth on startup.
3. Use the search bar or category chips to narrow results.
4. Click **Download** on any mod card, pick a loader and game version, then click **Download** in the popup to fetch the file.

## Tech notes

- All data comes from the public Modrinth API endpoints:
  - `GET /v2/search` — mod search and category filtering
  - `GET /v2/project/{id}/version` — available versions, loaders, and download files for a specific mod
- No user data is collected or stored; the site makes anonymous requests straight to Modrinth from the visitor's own browser.
- Because it's a single HTML file, it can be hosted anywhere (GitHub Pages, Netlify, a plain web server) or simply opened locally.

## Credits

Mod data, files, and authorship information are provided by [Modrinth](https://modrinth.com). ModatiAR is an independent browser interface and is not affiliated with Mojang, Microsoft, or Modrinth.
