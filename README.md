# 🥑 Fridge Chef

A clean-keto / animal-based cooking companion. Snap your fridge, plan your week, or roll a random meal — all in one lightweight web app. No build step, no backend: a single `index.html` you can host anywhere.

## Features

- **📸 Fridge Scanner** — take a photo of your fridge; AI detects the ingredients. It confirms uncertain items one by one (showing a cropped photo of each), lets you correct or add anything, then suggests fast meals with real dish photos, plus a shopping list and "bonus" meals unlocked by a quick shop.
- **🗓️ Weekly Plan** — generates a 7-day meal plan (breakfast + a quick main each day) that adapts to what you've cooked recently, and builds a consolidated shopping cart for the week.
- **🎲 Surprise Me** — one random clean-keto meal in a tap, with a reroll.
- **🛒 Shopping Cart** — everything you send from meals and plans lands here; tap to check off items while you shop. Saved locally on the device.
- **Context aware** — tapping "I cooked this" logs the meal, so the weekly plan and random suggestions avoid repeats and vary your proteins.

Everything is stored in the browser (`localStorage`) — no account, no server.

## Tech

- Plain HTML/CSS/JS, single file.
- [Google Gemini](https://ai.google.dev/) (free tier) for vision + meal generation.
- [TheMealDB](https://www.themealdb.com/) (free) for dish photos.

