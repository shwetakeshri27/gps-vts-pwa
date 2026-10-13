# GPS-VTS Annexure Manager: PWA package

This folder is the installable Progressive Web App version of the demo.

## Files

- `index.html`: the complete app (HTML, CSS and JavaScript in one file)
- `manifest.webmanifest`: app name, colours, icons and display mode
- `sw.js`: service worker that caches the app for offline use
- `icons/`: app icons (192 px, 512 px, maskable 512 px)

## How to deploy

1. Upload the whole folder to any HTTPS web host (for example Nginx, Apache, Netlify, Azure Static Web Apps or an S3 bucket behind CloudFront). A PWA must be served over HTTPS; `http://localhost` also works for testing.
2. Open the site in Chrome or Edge on desktop or Android and choose **Install app**. On iPhone or iPad, open it in Safari and choose **Share → Add to Home Screen**.
3. After the first visit the app opens offline.

To test locally: run `npx serve .` (or `python -m http.server 8080`) in this folder, then open the address it prints, for example `http://localhost:3000` or `http://localhost:8080`. The service worker and Install app also work on localhost.

Do not open `index.html` by double-clicking it (a `file://` address): the app still runs, but it cannot be installed and does not work offline.

## Data storage in this package

This standalone build saves data in the browser (localStorage) on each device. It is for demonstration. In the production build, the React frontend calls the Spring Boot REST APIs described in `Road_GPS_VTS_Website_Requirements.md`, and data is stored in PostgreSQL.

## Updating

When you change `index.html`, increase the `CACHE` version in `sw.js` (for example `gpsvts-v2`) so installed apps pick up the new version.
