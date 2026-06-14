# F1 Calendar 2026

[![Live Demo](https://img.shields.io/badge/demo-live-brightgreen)](https://yourusername.github.io/f1-calendar-2026/)
[![License](https://img.shields.io/badge/license-MIT-blue)](LICENSE)

**A modern, highly optimized Progressive Web App (PWA) built to track the 2026 Formula 1 racing season. This application functions entirely client-side, providing a fast, fluid user experience with automated dark mode integration, comprehensive data navigation, and full offline accessibility.**

![F1 Calendar Preview](https://img.shields.io/badge/Status-Active-success)

---

## Features

- **Dynamic Race Schedule:** Month-by-month browsing of the 2026 Grand Prix schedule with localized session breakdowns, integrated maps, and race status markers.
- **Sprint Filter Toggle:** A dedicated filtering system allowing users to instantly isolate and view only the race weekends hosting Sprint events.
- **Live Championship Standings:** Automated live data syncing for both Driver and Constructor standings.
- **Progressive Web App (PWA):** Equipped with a custom web application manifest and service worker configuration, making the platform completely installable on Android, iOS, and desktop platforms.
- **Advanced Offline Synchronization:** Implements a dual-layer strategy using separate cache storages:
  - Cache-First strategy for the core application shell (HTML, layout, styling, typography).
  - Network-First strategy with a 5-second fallback window for handling real-time api data, keeping statistics active even while completely disconnected.
- **Responsive Layout Architecture:** Styled using custom modern CSS variables and flex/grid architectures optimized for desktop, tablet, and mobile displays.
- **Keyboard Shortcuts:** Built-in accessibility commands featuring arrow key month-navigation (`Left` / `Right`) and deep developer metrics toggles (`Shift` + `D`).

---

## Live Demo

**[View Live Demo](https://vojislav77.github.io/f1-calendar-2026/)**

---

## Screenshots

### Light Mode


*Calendar view with race cards and standings*

### Dark Mode


*Sleek dark theme for night viewing*

---
## Architecture and File Structure

The workspace is highly consolidated, emphasizing zero-dependency performance:

- `index.html`: Contains the core document markup, modern CSS variable configurations, comprehensive theme switching, and main application lifecycle scripts.
- `manifest.json`: Configuration defining app icons (including standalone maskable attributes), localized naming, accent coloration, and standalone portrait execution requirements.
- `sw.js`: The system's Service Worker script governing asset pre-caching routines and selective network proxy intercepts for Ergast / Jolpi API responses.

## Core Technologies Used

- Semantic HTML5
- Vanilla CSS3 (featuring responsive media queries, CSS variables, and modern blur backdrops)
- Asynchronous ECMAScript 6+ (Fetch API, Service Worker API, AbortController timeout handling)

## Local Development and Installation

Due to standard browser security configurations governing the Service Worker API and CORS restrictions for network tracking, the application should be served from an absolute origin rather than directly via a local file utility (`file://`).

### Running the Project Locally

1. Clone or download the repository into a directory of your choice.
2. Launch a local web server from the project's root folder using any of the following terminal commands:

   **Using Python 3:**
   ```bash
   python3 -m http.server 8000

Using Node.js (npx): npx serve

3. Open your browser and navigate to http://localhost:8000 or http://localhost:3000 based on your server output.


## Installation via PWA

Once running under a secure origin (https://) or a verified local environment (localhost), an inline installation prompt will appear near the bottom of the interface. Selecting "Install" integrates the application directly into your operating system's launcher menu or home screen.
License

## This project is open-source and available under the MIT License.

---
