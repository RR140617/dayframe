# DayFrame v3 — Google Photos ZIP importer fix

Upload **all seven files** in this folder to the root of your existing `dayframe` GitHub repository. Commit changes. The new file `pako_inflate.min.js` must be uploaded alongside `app.js` and `index.html`.

Then open https://rr140617.github.io/dayframe/ and refresh with Ctrl+F5 (on a computer). On Android, close and reopen the app after the site updates.

Choose **Import album ZIP** and select the original downloaded Google Photos ZIP. No manual unzipping is required. Images are extracted locally in your browser.

### Limitations
- Albums over 900 MB may exceed device memory; use smaller ZIP files.
- JPEG EXIF and Google Photos JSON metadata are used when available; some photo dates may remain uncertain.
- Existing Google Photos albums cannot be automatically synced via this app.
- ZIP64 archives are not supported.
- Photo import is session-only; reopening the app requires reimport.
- Photos are never uploaded to GitHub.
