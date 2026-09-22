# Bree Foods

A tiny picker that saves me from that daily 6pm standoff where we both stare at the kitchen and ask each other *"so... what do you want to eat?"* for twenty minutes.

I built this so my lady doesn't have to figure out what to cook — the app does the thinking. It knows every meal we actually make, knows which ones we love, and knows what we just ate recently, so it only suggests things we're actually in the mood for.

## What it does

- Loads the menu straight from `foods.ts` — ugaali, rice, and chapati combos (29 meals).
- Picks a main suggestion plus two alternates, weighted randomly.
- Meals you've starred as **favorites** show up way more often.
- Meals logged in the **last 14 days** are quietly pushed aside so we don't eat the same thing twice in a row.
- When you *Accept & log* a pick, it's recorded with today's date and kept in your browser.

## Live site

Deployed at <https://her.ladha.co.ke>.

## Running it locally

Any static file server works — or just open `index.html` directly:

```sh
python3 -m http.server 8000
# open http://localhost:8000/index.html
```

## Deploying it

The app is a single HTML file that reads `foods.ts` at runtime, so hosting is just serving these two files as static assets — it works on any static host or CDN (GitHub Pages, Netlify, Cloudflare Pages, NGINX, etc.). There's no build step and no server-side logic; make sure the `.ts` file is served alongside the HTML in the same folder. It's currently at <https://her.ladha.co.ke>.

## Adding a new meal

Just edit `foods.ts`, add it to the right list, save, and hit **Reload** in the app. No rebuilding, no syncing — the page reads the file fresh every time.

All your favorites and history live in the browser's localStorage (key: `bree_foods_state`). Clearing site data wipes the history, which is also a handy reset.