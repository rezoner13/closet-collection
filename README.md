# Collection Closet

A standalone, installable Progressive Web App (PWA) for tracking your comic book collection — issues, condition, value, key issues, and optional AI-powered cover scanning.

This is a plain HTML/CSS/JS site — no build step, no framework, no account required. Your data is stored locally on your device (via IndexedDB), so once it's installed it works fully offline.

## What's in this folder

- `index.html` — the app shell
- `styles.css` — all styling
- `app.js` — all app logic (storage, rendering, scanning)
- `manifest.json` — makes the app installable
- `service-worker.js` — enables offline use
- `icons/` — app icons

## 1. Deploy it somewhere (so it has a real URL)

Pick whichever is easiest for you — all are free:

### Option A: Do it entirely from your phone (GitHub)
1. In your phone's browser, go to https://github.com and sign up / log in (free)
2. Tap the **+** icon (top right) → **New repository**
3. Give it any name (e.g. `collection-closet`), set it to **Public**, tap **Create repository**
4. On the new repo page, tap **"uploading an existing file"**
5. Tap to browse, then select **all the files in this folder at once** (they're all flat, no subfolders, so your phone's file picker can multi-select them in one go)
6. Scroll down and tap **Commit changes**
7. Go to the repo's **Settings → Pages**
8. Under "Build and deployment", set Source to **Deploy from a branch**, branch to **main**, folder to **/ (root)**, then **Save**
9. Wait about a minute, then refresh that Pages settings screen — it'll show your live URL, something like `https://yourusername.github.io/collection-closet/`

### Option B: Netlify (easiest from a computer, drag-and-drop)
1. Go to https://app.netlify.com/drop
2. Drag this whole folder onto the page
3. You'll get a live URL like `https://your-app-name.netlify.app`

### Option C: Vercel
1. Go to https://vercel.com and sign up (free)
2. Use their web dashboard's "Add New Project" → upload this folder
3. Deploy — you'll get a URL like `https://your-app.vercel.app`

**Important:** PWAs require HTTPS (except on `localhost`). All three options above serve over HTTPS automatically.

## 2. Install it on your phone

Once it's live at a URL:

**Android (Chrome):**
1. Open the URL in Chrome
2. Tap the three-dot menu → "Add to Home screen" or "Install app"
3. Confirm — you'll get a real home screen icon

**iPhone (Safari):**
1. Open the URL in Safari
2. Tap the Share icon (square with an arrow) → "Add to Home Screen"
3. Confirm — you'll get a real home screen icon

From then on, tapping the icon launches the app in its own window (no browser bar), and it works offline.

## 3. (Optional) Turn on cover scanning

The camera-scan-to-autofill feature calls the Anthropic API directly from your browser, so it needs your own API key:

1. Get a key at https://console.anthropic.com/settings/keys
2. Open the app, tap the gear icon (top right), paste your key in, and save
3. Now the camera button will read a comic cover and auto-fill the title, issue number, publisher, year, and key-issue flag

**Security note:** the key is stored only in your browser's local storage on that device — it's never sent anywhere except directly to Anthropic's API when you scan a cover. Anyone with access to that browser's dev tools could technically read it, so:
- Only use this on a device you trust
- Consider setting a spending limit on the key in the Anthropic Console
- Scanning is entirely optional — you can always add comics by typing the details in

## Notes on how data is stored

- Comics (including any scanned cover photo) are saved in your browser's IndexedDB — this is local to that specific browser and device.
- If you install the app on multiple devices, they won't automatically sync with each other (there's no shared backend in this version). Each install has its own local collection.
- Clearing your browser's site data/history for this app will delete your collection, so avoid "clear all site data" on this URL if you want to keep your comics.
