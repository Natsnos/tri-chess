# Tri-Dimensional Chess

A 3D, browser-based take on tri-dimensional chess: three stacked 4×4 main levels plus four movable 2×2 attack boards, rendered with three.js. Also includes the 5×5×5 Raumschach cube.

**Play it:** publish this repo with GitHub Pages (Settings → Pages → Deploy from branch → `main` / root), then open `https://<your-name>.github.io/tri-chess/`.

## Features
- Full-window 3D board with a slide-out menu; orbit, zoom, tilt, auto full screen, opening fly-in
- Variants: standard tri-dimensional, shuffled starting setup, and Raumschach (5×5×5, with unicorns)
- 11 piece sets including themed armies (Vampires vs Werewolves, Star Knights, Starship Fleet, Dragon Realm, Gothic Cathedral), mix-and-match per side, an army designer for custom colors, and your own `.glb` models
- Scenery and generative background music that match the armies; glow, idle animations, capture effects and battle close-ups
- Play the computer (Casual, Thoughtful, Strong), a six-opponent campaign, or a friend on one screen
- Full rules: castling, en passant, promotion, attack-board moves, check/mate/stalemate, 50-move and repetition draws
- Coach and hints, threat view, press-and-hold to preview any piece's moves, move timeline and replay, post-game review with accuracy
- 16 built-in checkmate puzzles plus a daily puzzle and a generator for new ones
- Chess clocks, stats and achievements, autosave and shareable game codes
- Keyboard shortcuts (press `?`), color-blind friendly highlights, high-contrast board
- Installable app that works offline after the first visit

## Install as an app
- **Phone:** open the site, then use your browser's *Add to Home Screen*. It launches full screen.
- **Desktop Chrome/Edge:** click the install icon in the address bar.
- After one visit with internet, the game works offline. When you publish a new `index.html`, bump `VERSION` in `sw.js` so players get the update.

## Online play (optional)
Online play on GitHub uses a free Firebase project:
1. Create a project at [console.firebase.google.com](https://console.firebase.google.com) and add a **Web app**.
2. **Authentication → Sign-in method:** enable **Anonymous**.
3. **Firestore Database:** create a database, then paste these rules under **Rules**:
   ```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{db}/documents {
       match /games/{code} {
         allow read, create, update: if request.auth != null;
       }
       match /ratings/{uid} {
         allow read: if request.auth != null;
         allow write: if request.auth != null && request.auth.uid == uid;
       }
     }
   }
   ```
4. Copy the web app's config into `config.js` (replace `null`) and commit.

Players enter a name in the online panel. Create a game and share the 6-letter code, or pick one from the open-games list. Finished games update everyone's rating on the leaderboard.

## Notes
- Everything runs from `index.html`; three.js and fonts load from public CDNs and are cached for offline use.
- The coach's spoken explanations, read-aloud moves and voice input use Claude and are available in the Claude-hosted version. Here the coach uses the built-in engine, and typed move commands work everywhere.
- Progress, settings, custom colors and models are stored in your browser only.
