# 🥑 Fridge Chef

A clean-keto / animal-based cooking companion. Snap your fridge, plan your week, or roll a random meal — all in one lightweight web app. No build tooling, no backend: a single `index.html`, deployed straight to GitHub Pages.

**Live:** https://nohra2005.github.io/Fridge-chef/

## Features

- **📸 Fridge scanner** — take a photo of your fridge; AI detects the ingredients. It confirms uncertain items one at a time (showing a cropped photo of each), lets you correct or add anything, then suggests fast meals with a real photo of each dish, a shopping list, and "bonus" meals unlocked by a quick shop.
- **🗓️ Weekly plan** — a 7-day plan (breakfast + a quick main each day) that adapts to what you've cooked recently, plus a consolidated shopping cart for the week.
- **🎲 Surprise me** — one random clean-keto meal in a tap, with a reroll.
- **🛒 Shopping cart** — everything you send from meals and plans lands here; tap to check items off while you shop. Saved on the device.
- **Context aware** — tapping "I cooked this" logs the meal, so the weekly plan and random suggestions avoid repeats and vary your proteins.

All state is stored in the browser (`localStorage`) — no account, no server.

## Tech

- Plain HTML / CSS / JS, single file.
- [Google Gemini](https://ai.google.dev/) (free tier) for fridge vision + meal generation.
- [Openverse](https://openverse.org/) (free, no key) for real dish photos.

## How the API key is handled

A browser-only app can't truly hide an API key, but this repo keeps the key **out of the source** and only injects it at deploy time:

1. The key lives in a GitHub **repository secret** named `GEMINI_KEY` (Settings → Secrets and variables → Actions).
2. On every push, the workflow in `.github/workflows/deploy.yml` replaces the `__GEMINI_KEY__` placeholder in `index.html` with the secret, then publishes to GitHub Pages.
3. The committed source only ever contains the placeholder, so the key is never in the repo and won't be auto-disabled as "leaked."

The key is still visible in the deployed page (unavoidable for any client-side app), so it's also **restricted** in Google Cloud so it only works from this site.

## Deploy (GitHub Pages)

1. **Settings → Pages → Source → GitHub Actions.**
2. **Settings → Secrets and variables → Actions → New repository secret:** name `GEMINI_KEY`, value = your Gemini key from [aistudio.google.com/apikey](https://aistudio.google.com/apikey).
3. Push to `main`. The Actions workflow injects the key and deploys automatically.

## Restrict your key (do this once)

In [Google Cloud Console → Credentials](https://console.cloud.google.com/apis/credentials), open the key and set:

- **Application restrictions → Websites →** `https://nohra2005.github.io/*`
- **API restrictions →** allow **Generative Language API** (or "Don't restrict key").

## Diet

Tuned for clean keto / animal-based eating: beef, eggs, chicken, avocado, greek yogurt, nuts, fruit, sweet potato, and occasional clean carbs. Edit the `DIET` constant near the top of the script in `index.html` to change the style.
