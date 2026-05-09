# Universal Calculator — PWA Deploy Guide (Android + GitHub Pages)

You'll do this once. Total time: ~10 minutes.

## What's in this folder

- `index.html` — the calculator
- `manifest.webmanifest` — tells phones it's an installable app
- `service-worker.js` — caches files so it works offline
- `icon-192.png`, `icon-512.png`, `icon-512-maskable.png` — app icons

Don't rename anything.

## Part 1 — Put it on GitHub Pages

1. Go to **https://github.com** and sign in (or sign up if you don't have an account — free).
2. Click the **`+`** in the top-right → **New repository**.
3. Name it something like **`calculator`**. Set it to **Public** (Pages requires public on free accounts). Leave everything else default. Click **Create repository**.
4. On the empty repo page, click **uploading an existing file** (it's a link in the middle of the page).
5. **Drag every file from this folder** (`index.html`, `manifest.webmanifest`, `service-worker.js`, all three `.png` icons) onto the upload area. Wait for them all to show as ready.
6. Scroll down, click **Commit changes**.
7. In the repo, click **Settings** (top-right tab) → **Pages** (left sidebar).
8. Under **Source**, pick **Deploy from a branch**. Branch: **`main`**, folder: **`/ (root)`**. Click **Save**.
9. Wait ~1 minute. Refresh the Pages page — you'll see a green box with your URL, something like:
   `https://YOUR-USERNAME.github.io/calculator/`

That's your app URL.

## Part 2 — Install on your Android phone

1. Open **Chrome** on your phone (must be Chrome — Samsung Internet works too, but built-in browsers like Mi Browser sometimes don't).
2. Visit the GitHub Pages URL from step 9 above.
3. Use the calculator once to confirm it works.
4. Tap the **⋮ menu** (top right) → **Install app** (or **Add to Home screen**, depending on Chrome version).
5. Confirm. The icon will appear on your home screen and in your app drawer.

When you open it from the home screen, it launches in its own window — no browser bars, no tabs. It looks and behaves like a real app, including showing up in the recent-apps switcher.

## Updating the app later

If you change `index.html`:

1. In the GitHub repo, click `index.html` → pencil icon → make edits → **Commit changes**. (Or drag-and-drop a new version.)
2. Bump the cache version: open `service-worker.js`, change `'universal-calculator-v1'` to `'-v2'`, commit.
3. On your phone, open the app. It'll download the new version in the background; close and reopen once to see it.

## Troubleshooting

- **"Install app" option doesn't appear** → make sure you opened Chrome (not a built-in browser), the URL starts with `https://`, and you've reloaded the page once.
- **Icon looks generic instead of the calculator** → wait a few seconds and reload. Service worker needs one load to register the icons.
- **Currency rates feel stale** → tap the Currency tab → "Edit reference rates" → paste fresh numbers, Save. They persist on your phone.
- **App doesn't work offline** → load it once while online so the service worker can cache files, then it'll work with no signal.
