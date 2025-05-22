> This game is inspired by the “Wall Go” game featured in **Devil’s Plan 2 (魔鬼的計謀 2)**, a Netflix reality show where strategy and psychological warfare collide. This is a faithful and minimalist implementation of that mini-game in the browser, open-sourced for fans, educators, and curious coders.

# Wall‑Go 🧱♟️

A minimalist **React + TypeScript** implementation of the “Wall Go / 牆壁圍棋” mini‑game seen in *Devil’s Plan 2*.  
Builds to a completely static site so it can be served on **GitHub Pages** (or any static host).

---

## Demo

> (Once deployed) https://schaoss.github.io/wall-go/

---

## Features

* 7 × 7 board, dynamic 0–2‑step movement, wall building on four sides — just like in *Devil’s Plan 2*
* ABBA… stone placement order, auto‑skip turns when a player is blocked  
* Auto end‑game detection + scoring, live score board, “Play again” reset  
* Zustand for state, Tailwind CSS v4 for styling, Bun as package manager / dev server

---

## Tech Stack

This project uses the following tools and libraries:

| Tool / Library      | Purpose                               |
|---------------------|----------------------------------------|
| **Bun**             | Runtime, package manager, and dev server |
| **React**           | UI framework                          |
| **TypeScript**      | Type-safe development                 |
| **Vite**            | Lightning-fast bundler                |
| **Tailwind CSS v4** | Utility-first styling                 |
| **Zustand**         | Lightweight state management          |
| **gh-pages**        | Deployment helper to GitHub Pages     |

---

## Quick Start

```bash
# Clone
git clone https://github.com/schaoss/wall-go.git
cd wall-go

# Install deps (Bun)
bun install

# Local dev (hot reload)
bun run dev

# Production build
bun run build        # outputs to /dist
```

Open <http://localhost:5173> and start placing stones!

---

## Deploy to GitHub Pages

1. **Add the homepage field**

   In `package.json`:

   ```jsonc
   {
     "homepage": "https://schaoss.github.io/wall-go"
   }
   ```

2. **Install the gh‑pages helper (already in dev deps)**  
   ```bash
   bun add -D gh-pages
   ```

3. **One‑shot manual deploy**

   ```bash
   bun run build
   bun run deploy      # runs gh-pages -d dist
   ```

   This pushes `dist/` to the `gh-pages` branch and your site will be live at the URL above.

### CI Deploy (recommended)

Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GH‑Pages
on:
  push:
    branches: [main]
jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: oven-sh/setup-bun@v1
        with:
          bun-version: "latest"
      - run: bun install
      - run: bun run build
      - uses: peaceiris/actions-gh-pages@v4
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
```

Push to `main` and GitHub Actions will automatically build and publish.

---

## Customising

| What | Where |
|------|-------|
| Board size | `BOARD_SIZE` in `src/lib/types.ts` |
| Player colours | `color()` helper in `src/App.tsx` + Tailwind safelist |
| Stones per player | `STONES_PER_PLAYER` in `src/store.ts` |
| Add more players | Edit the `PLAYERS` array and safelist new colours |

---

## License

MIT © 2025 Gary Chu
