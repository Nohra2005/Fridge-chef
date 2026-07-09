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

## Deploy

**Option A — Netlify (drag & drop):** go to [app.netlify.com/drop](https://app.netlify.com/drop) and drag this folder in. Done.

**Option B — GitHub Pages:** push this folder to a repo, then in the repo go to **Settings → Pages → Build from branch → main / root**. Your app is live at `https://<user>.github.io/<repo>/`.

## ⚠️ Important: protect your API key

The Gemini API key is embedded in `index.html` so the app works as a static site. On a **public** site or repo, that key is visible to anyone. Client-side keys can't be hidden — instead, **restrict** it so it's useless to others:

1. Open [Google Cloud Console → Credentials](https://console.cloud.google.com/apis/credentials).
2. Click your API key → **Application restrictions → Websites (HTTP referrers)**.
3. Add your site only, e.g. `https://your-site.netlify.app/*` and `https://<user>.github.io/*`.
4. Save. The key now works only from your site, and the free tier caps usage.

If a key ever leaks or gets abused, delete it at [aistudio.google.com/apikey](https://aistudio.google.com/apikey) and paste a new one into the `BAKED_KEY` line near the top of the `<script>` in `index.html`.

## Diet

Tuned for clean keto / animal-based eating: beef, eggs, chicken, avocado, greek yogurt, nuts, fruit, sweet potato, and occasional clean carbs. Edit the `DIET` constant in `index.html` to change the style.
