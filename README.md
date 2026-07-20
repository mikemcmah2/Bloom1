# Two of Us — Cycle Tracker (v4: fully self-contained, no external scripts)

## What changed

Every previous version loaded React from an external CDN (unpkg, then jsdelivr). The persistent "Script error." you kept seeing is the generic message browsers show when a *cross-origin* script fails — meaning something was blocking those CDN requests, most likely a content/ad blocker.

This version has **zero external script dependencies**. React and ReactDOM are embedded directly inside `index.html` itself — there is nothing left to block. The only external requests this page makes are for the Google Fonts stylesheet (cosmetic only; the app works fine without it loading).

I tested this exact file in a browser with every external network request blocked, and it renders perfectly — so this should now work regardless of any blocker or filter on your device.

## Files to upload (all 8, same as before)

- `index.html` (now much bigger — ~600KB, since React is embedded in it)
- `bloom-icon.svg`
- `apple-touch-icon.png`
- `icon-192.png`, `icon-512.png`
- `favicon-32.png`, `favicon-16.png`
- `manifest.json`

## Deploy

Same as always: upload these to the root of your `Bloom` repo (overwrite existing files), commit, wait ~30–60 seconds, reload.

## About your data

Since this is a fresh reload of the page, nothing about your previously-entered data changes — it's still sitting in this browser's `localStorage`, keyed by the site's origin, completely separate from the app's code. If you do want a clean start, you're welcome to just start re-entering your last few cycles once this version is confirmed working.

## Notes

- Password is hashed and stored in `localStorage`; it deters casual snooping, it isn't encryption.
- Data lives in `localStorage` in whatever browser you use — no sync between devices.
- If anything still fails to load, the page shows the exact error as readable text — but there's very little left that could fail now.
