# DayFrame — free photo organiser

A local-first, installable mobile web app (PWA). No account, server, or paid service is needed for photo processing.

## Features
- Import an entire Google Photos downloaded album ZIP, plus individual images or folders. ZIP extraction happens locally in the browser.
- Read Google Photos JSON sidecar timestamps when included in the ZIP. ZIP imports work best in up-to-date Chrome.
- Read **JPEG EXIF DateTimeOriginal** when present. Otherwise use date embedded in filename (YYYYMMDD or YYYY-MM-DD), then file last-modified date (clearly flagged as uncertain).
- Group photos by calendar day; sort oldest/newest; select entire days or individual images.
- Export original image bytes into a ZIP with one folder per day, for later extraction and Instagram upload.
- Works offline after initial visit when hosted over HTTPS and installed.

## Start locally on a computer
1. Unzip the archive.
2. Open a terminal in the `dayframe` folder.
3. Run `python -m http.server 8000` (or `py -m http.server 8000` on Windows).
4. Open `http://localhost:8000` in your browser.

## Install on Android
For phone installation, host the folder on a free HTTPS static host (for example, GitHub Pages or Netlify). Open the HTTPS URL in Chrome on Android, tap the three-dot menu, and choose **Add to Home screen** / **Install app**.

### Free GitHub Pages publishing
1. Sign in to https://github.com and create a new **public** repository named `dayframe`.
2. Choose **Add file → Upload files** and upload the *contents* of this `dayframe` folder (not the ZIP).
3. Commit changes.
4. In the repository choose **Settings → Pages → Build and deployment → Deploy from a branch**.
5. Select branch `main`, folder `/(root)`, then Save.
6. After deployment, visit `https://YOUR-GITHUB-USERNAME.github.io/dayframe/` on your phone.
7. In Chrome, choose **Install app** or **Add to Home screen**.

## Important limitations
- Google Photos album auto-sync is **not** included. In Google Photos, select/download photos to your phone and then import them in DayFrame. Browser file pickers may also expose Google Photos through Android's system photo picker, depending on device.
- For non-JPEG images (including HEIC/HEIF) the app does not decode embedded capture metadata. It falls back to a filename date or file modified date. JPEG EXIF dates have no timezone; the calendar day is preserved as recorded in EXIF.
- Some images imported from Google Photos lose original EXIF capture dates during download or editing; these are marked as uncertain if no date is found.
- Imports are **session-only**. Reloading or closing the app clears the imported list; original photos on the phone are untouched.
- ZIP creation is memory-intensive. Export smaller batches; a maximum of 300 photos / approximately 700 MB per export is enforced.
- This app prepares photo packs but does not automatically post to Instagram or make Instagram-sized crops.
- For privacy, the app makes no network uploads of your photos. GitHub Pages serves only the app's static code.

## Update an existing GitHub Pages deployment
Upload the changed `index.html`, `app.js`, `sw.js` and other app files to the repository root, choosing to replace files with the same names. Commit changes and refresh the site after deployment.

Note: very large album ZIPs may exhaust phone memory; use a laptop browser for huge archives. ZIP64 and uncommon ZIP compression methods are not supported. Google Photos album downloads do not always contain JSON sidecars, so uncertain dates will be flagged.
