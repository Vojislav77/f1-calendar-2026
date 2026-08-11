# F1 Calendar 2026

[![Live Demo](https://img.shields.io/badge/demo-live-brightgreen)](https://yourusername.github.io/f1-calendar-2026/)
[![License](https://img.shields.io/badge/license-MIT-blue)](LICENSE)

**A modern, highly optimized Progressive Web App (PWA) built to track the 2026 Formula 1 racing season. This application functions entirely client-side, providing a fast, fluid user experience with automated dark mode integration, comprehensive data navigation, and full offline accessibility.**

![F1 Calendar Preview](https://img.shields.io/badge/Status-Active-success)

---

## Features

- **Dynamic Race Schedule:** Month-by-month browsing of the official 2026 Grand Prix schedule (23 rounds) with localized session breakdowns and race status markers.
- **Sprint Filter Toggle:** A dedicated filtering system allowing users to instantly isolate and view only the race weekends hosting Sprint events.
- **Live Championship Standings:** Automated live data syncing for both Driver and Constructor standings.
- **Official Calendar Data:** The 2026 schedule, UTC race start times, and the six Sprint weekends (China, Miami, Canada, Great Britain, Netherlands, Singapore) are based on the official FIA/F1 calendar. The live API is enriched with these times and flags so races are never shown as "TBA" and Sprints are always detected.
- **Real Results & Standings:** Completed races display real podium results and the standings reflect actual points, both live and in the offline snapshot.
- **Progressive Web App (PWA):** Equipped with a custom web application manifest and service worker configuration, making the platform completely installable on Android, iOS, and desktop platforms.
- **Advanced Offline Synchronization:** Implements a dual-layer strategy using separate cache storages:
  - Cache-First strategy for the core application shell (HTML, layout, styling, typography).
  - Network-First strategy with a 5-second fallback window for handling real-time api data, keeping statistics active even while completely disconnected.
- **Responsive Layout Architecture:** Styled using custom modern CSS variables and flex/grid architectures optimized for desktop, tablet, and mobile displays.
- **Keyboard Shortcuts:** Built-in accessibility commands featuring arrow key month-navigation (`Left` / `Right`) and deep developer metrics toggles (`Shift` + `D`).
- **Secure Rendering:** All API-driven text (race names, locations, driver/team names) is HTML-escaped before rendering, and card actions use event delegation instead of inline handlers.

---

## Live Demo

**[View Live Demo](https://vojislav77.github.io/f1-calendar-2026/)**

---

## Screenshots

### Light Mode

<img width="1263" height="1025" alt="f1l" src="https://github.com/user-attachments/assets/f0f2aa25-0749-4601-9096-c51d5d7a05e1" />

*Calendar view with race cards and standings*

### Dark Mode

<img width="1260" height="1017" alt="f1d" src="https://github.com/user-attachments/assets/3fdb8ad0-489b-414b-9d95-8022be75d8b7" />

*Sleek dark theme for night viewing*

---
## Architecture and File Structure

The workspace is highly consolidated, emphasizing zero-dependency performance:

- `index.html`: Contains the core document markup, modern CSS variable configurations, comprehensive theme switching, and main application lifecycle scripts. It also embeds the official 2026 season metadata (UTC start times + Sprint flags) and the offline fallback snapshot.
- `manifest.json`: Configuration defining app icons (including standalone maskable attributes), localized naming, accent coloration, and standalone portrait execution requirements.
- `sw.js`: The system's Service Worker script governing asset pre-caching routines and selective network proxy intercepts for the Jolpi Ergast mirror API responses (the original Ergast API was retired).

## Core Technologies Used

- Semantic HTML5
- Vanilla CSS3 (featuring responsive media queries, CSS variables, and modern blur backdrops)
- Asynchronous ECMAScript 6+ (Fetch API, Service Worker API, AbortController timeout handling)

## Data Accuracy

- **Live Mode** fetches the 2026 season from the [Jolpi Ergast mirror](https://api.jolpi.ca) (Ergast itself was retired in 2024). Since the mirror omits race times and Sprint markers, the app merges in the official FIA/F1 season metadata embedded in `index.html`, so every race shows a real start time and correct Sprint badge.
- **Offline Mode** falls back to an embedded snapshot: the official 23-round calendar plus real results and standings as of round 11 (Hungarian Grand Prix, July 2026). The snapshot is clearly labelled **Offline Mode** in the UI.
- The fallback contains no fabricated data — podiums and points reflect the actual season at the time the snapshot was taken, and the countdown, `.ics` export, and Google Calendar links all use the correct UTC start times.

## Local Development and Installation

Due to standard browser security configurations governing the Service Worker API and CORS restrictions for network tracking, the application should be served from an absolute origin rather than directly via a local file utility (`file://`).

### Running the Project Locally

1. Clone or download the repository into a directory of your choice.
2. Launch a local web server from the project's root folder using any of the following terminal commands:

   **Using Python 3:**
   ```bash
   python3 -m http.server 8000
   ```

   **Using Node.js (npx):**
   ```bash
   npx serve
   ```

3. Open your browser and navigate to http://localhost:8000 or http://localhost:3000 based on your server output.


## Installation via PWA

Once running under a secure origin (https://) or a verified local environment (localhost), an inline installation prompt will appear near the bottom of the interface. Selecting "Install" integrates the application directly into your operating system's launcher menu or home screen.

## Changelog

### 2026-08-11 — Data accuracy & hardening update

- Replaced the fallback schedule with the **official 2026 FIA/F1 calendar** (23 rounds): corrected dates, added Madrid and the Bahrain GP in Malaysia, removed the canceled Saudi Arabian GP and the dropped Emilia Romagna GP.
- Added a single source of truth for **UTC start times and Sprint weekends** (`SEASON_OVERRIDES` in `index.html`), merged into the live API schedule so live mode never shows "TBA" times and always detects the six Sprint rounds (China, Miami, Canada, Britain, Netherlands, Singapore).
- Replaced fabricated podiums and standings with **real results through round 11 and real points** (e.g. Antonelli 219, Hamilton 169) in the offline snapshot.
- **Hardened rendering:** all dynamic text is HTML-escaped and card actions (`.ics` / Share) now use event delegation instead of inline `onclick`.
- Bumped the service worker cache to `v2` so returning users receive the update.

## License

This project is open-source and available under the MIT License.

---
