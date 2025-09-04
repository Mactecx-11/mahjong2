# Mahjong Duel — 2P (Netlify-ready)

A modern, two‑player Mahjong web game with peer‑to‑peer sync over WebRTC. It supports two connection modes:

1) **Nearby (QR/manual, no internet):** Uses WebRTC with bundled ICE (no STUN) and manual SDP exchange via a short code or QR. Works on the same Wi‑Fi or offline if both devices can connect locally.
2) **Remote (Firebase):** Uses Firebase Realtime Database as a free signaling server and a public STUN server for NAT traversal.

> Note: Browsers do **not** allow direct Bluetooth or Wi‑Fi Direct connections between pages. This project offers the closest equivalents available on the web platform.

## Features
- Complete 2‑player Mahjong flow: draw, discard, claim Chow/Pung/Kong, win check (four melds + pair).
- Real‑time synced state via WebRTC DataChannels.
- **Power Tile** (fun twist): set once per game for a bonus if included when you win.
- **Speed Mode**: optional 10‑minute round timer.
- Hints: simple discard suggestions.
- Mobile‑friendly, no server code required for gameplay.
- Netlify‑ready static site.

## Setup

### 1) Remote play (Firebase)
- Create a Firebase project → Realtime Database (test mode) enabled.
- Copy web app config and paste into `config.js`.
- Deploy to Netlify (drag‑and‑drop this folder or connect GitHub).
- On the site, enter a Room ID and **Host/Join**.

### 2) Nearby play (QR/manual)
- Open the site on both devices (HTTPS recommended).
- One clicks **Create Offer** and shares the code (or QR) to the other.
- The other uses **Paste Offer** (button in UI) to generate an Answer, and returns that code.
- The first pastes the **Answer** back and the data channel opens.

> The demo includes a minimal QR generator and stub scanner. Replace `libs/jsqr.js` with a real scanner (e.g., jsQR or ZXing) for camera-based scanning.

## Local Dev
- Serve with any static server (e.g., `npx http-server .`).
- Modern evergreen browsers required.

## Roadmap ideas
- Richer scoring, Riichi/HK variants as pluggable rulesets
- Rejoins, reconnection
- Spectator mode
- Analytics (privacy‑friendly)
