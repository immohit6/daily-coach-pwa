# Daily Coach — install on your iPhone

Three self-contained web apps living in one folder: **Daily Coach** (daily
plan, goal, streak), **Gym Coach** (7-day gym cycle, rest timer, workout log),
and **Hydration Coach** (water intake, target ring, streak). No build step,
no server code, no dependencies.

## Files
- `index.html` — Daily Coach
- `manifest.webmanifest` / `icon-*.png` — Daily Coach install assets
- `gym.html` — Gym Coach
- `gym-manifest.webmanifest` / `gym-icon-*.png` — Gym Coach install assets
- `hydration.html` — Hydration Coach
- `hydro-manifest.webmanifest` / `hydro-icon-*.png` — Hydration Coach install assets
- `sw.js` — shared service worker, gives all three apps offline access

Keep all files in the **same folder**. Don't rename anything. The three apps
link to each other from their header, and each installs to your home screen
as its own separate icon.

---

## Step 1 — Put it online (10 min, free)

It has to be served over HTTPS. GitHub Pages is the simplest free option.

1. Create a free account at github.com
2. Click **New repository**. Name it `daily-coach`. Set it to **Public**. Create.
3. On the repo page click **uploading an existing file**.
4. Drag in all the files from this folder. Click **Commit changes**.
5. Go to **Settings → Pages**.
6. Under "Build and deployment", set Source = **Deploy from a branch**, Branch = **main**, folder = **/ (root)**. Save.
7. Wait 1–2 minutes, refresh. Your URL appears at the top:
   `https://YOURNAME.github.io/daily-coach/`

Note: a public repo means anyone with the URL can open the app. It does NOT expose
your tasks — your data never leaves your phone. But if you'd rather keep the code
private, use Netlify Drop (netlify.com/drop) instead: drag the folder in, get a URL,
no account needed to start.

## Step 2 — Install on your iPhone

1. Open the URL in **Safari** (must be Safari, not Chrome).
2. Tap the **Share** button (square with the arrow).
3. Scroll down, tap **Add to Home Screen**.
4. Name it "Daily Coach", tap **Add**.

You now have an app icon. It opens full-screen with no browser bar and works offline.

To also install **Gym Coach** or **Hydration Coach** as their own separate
icons, open `https://YOURNAME.github.io/daily-coach/gym.html` or
`.../hydration.html` in Safari and repeat the same three steps. Each gets its
own home screen icon, distinct from the others.

## Step 3 — First run

The app seeds itself with your standard 11 tasks on first launch. Edit anything
you like, then tap **Save as standard** so the template matches what you actually do.

---

## Backing up your data

Your data lives in this app's local storage on this device only. It is not synced
and not in iCloud. iOS can clear it if the phone runs very low on space, or if you
clear Safari website data, or if you delete the icon.

**Once a month:** tap **Export backup**, save the `.json` file to iCloud Drive or
send it to yourself on WhatsApp. To restore on a new phone: install the app, tap
**Import backup**, pick the file.

## Updating the app later

Re-upload the changed file to GitHub (Add file → Upload files → commit). The
service worker is network-first, so the next time you open the app online it picks
up the new version automatically.
