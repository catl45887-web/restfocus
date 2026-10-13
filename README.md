# Restfocus PWA

Restfocus is a local-first, responsive focus timer PWA for iPhone, iPad, and desktop browsers. It includes count-up and countdown focus modes, task sets, one-time and recurring tasks, per-session time allocation, and daily/monthly statistics. Before each focus round, choose quiet rest or one saved video and set a five- or fifteen-minute rest duration. Saved MP4 videos form one flat, reorderable list with custom names, manual durations, and favorites. The video files are stored in the browser's IndexedDB on the current device; they are not uploaded or synced.

## Run locally

Serve this folder from a local web server (service workers require HTTPS or localhost). For example, with Python:

```sh
python -m http.server 8000
```

Open the displayed localhost address. Do not open `index.html` directly with a `file://` URL: browsers can deny IndexedDB access on file origins, which is required for storing MP4 files. The app stores task and session metadata in local storage and uploaded MP4 files in IndexedDB.

## Install on iPhone or iPad

Publish this folder to a static HTTPS host. Open the URL in Safari, tap Share, then **Add to Home Screen**. A PWA can run its timer while open, but iOS may suspend a page in the background and does not guarantee an exact locked-screen timer or notification. The service worker caches the app shell; data stays on that browser/device and does not sync between devices.

Select an MP4 from the device when adding a rest video. If the browser blocks playback with sound after the five-second preparation countdown, Restfocus starts the video muted and shows a button to enable sound. Existing link-based entries from an earlier version are marked for re-upload as local MP4 files.

