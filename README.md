# LYVO — installable PWA

LYVO is a mobile-first personal dashboard built with plain HTML, CSS and JavaScript. It does not need a framework or a build step.

## Included

- First-run setup asks for the user's name; no tasks, rhythms, goals or notes are prefilled.
- Create, edit and delete tasks and rhythms; daily completion is stored by date.
- Goals with individual colors and editable progress from 0–100%.
- Colored, editable notes.
- Weekly activity graph with independently configurable weekdays and per-day mood.
- User-selectable interface accent color.
- Local persistence in browser storage plus JSON backup export/import.
- PWA manifest, icons and service worker for offline app-shell use.

## Publish it (no build required)

The app needs to be served over **HTTPS** for installation and offline service-worker support. Opening `index.html` directly from the phone's file manager is not enough.

### Simple route: Netlify Drop

1. On a computer, unzip `LYVO-PWA-project.zip`.
2. Open `https://app.netlify.com/drop` and sign in or create an account if prompted.
3. Drag the extracted **`lyvo-pwa` folder's contents** into the drop area (the `index.html` file should be at the published site's root, not inside an extra nested folder).
4. Wait for Netlify to publish and copy the HTTPS website URL it gives you.
5. Open that URL in Chrome on Android while connected to the internet.
6. Open Chrome's `⋮` menu and choose **Install app** or **Add to Home screen**. The wording can vary by Chrome version.
7. Launch LYVO from the new home-screen icon. Open it online once before relying on offline mode.

### Alternative: GitHub Pages

1. Create a repository on `https://github.com/`.
2. Upload the contents of this folder to the repository root.
3. In repository settings, open **Pages**, choose deployment from the `main` branch and the root folder, and save.
4. Wait for the HTTPS Pages URL, then install from Chrome on Android as described above.

## Data and privacy

LYVO stores entries in the browser's local storage on the device. The data is not automatically synced between devices. Clearing browser/site storage can erase it, so use **Settings → Export JSON** periodically. Use **Import JSON** to restore a backup. Keep backup files private because they contain your personal entries.

## Offline behaviour

The service worker caches the app shell after its first successful online load. The interface and locally stored entries can then work offline. A new deployment may take a reload or reopening to update the cached app shell.

## Local preview for developers

From this folder, run a local static server, for example:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000`. `localhost` is allowed for service-worker development. A deployed phone installation must use HTTPS.
