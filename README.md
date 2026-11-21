# Tri-Dimensional Chess

A 3D, browser-based take on tri-dimensional chess: three stacked 4×4 main levels plus four movable 2×2 attack boards, rendered with three.js.

**Play it:** open `index.html` in a browser, or publish the repo with GitHub Pages (Settings → Pages → Deploy from branch → `main` / root).

## Features
- Full-window 3D board with a slide-out menu; rotatable, zoomable stand with lighting, shadows, glow, and scenery that matches your armies
- 11 piece sets, including themed armies (Vampires vs Werewolves, Star Knights, Starship Fleet, Dragon Realm, Gothic Cathedral), mix-and-match per side, and your own `.glb` models
- Play the computer (four strengths, campaign of six opponents) or a friend on one screen with auto-turning board
- Full rules: castling, en passant, promotion, attack-board moves, check/mate/stalemate, 50-move and repetition draws
- Hints, threat view, move timeline and replay, chess clocks, 16 verified checkmate puzzles
- Sound effects, capture effects, battle close-ups, stats and achievements
- Autosave plus shareable game codes

## Notes
- Everything is in the single `index.html` file; three.js and fonts load from public CDNs.
- Online play, reading moves aloud, and voice input rely on the Claude-hosted version and are hidden or disabled when run elsewhere. Typed move commands work everywhere.
- Progress, settings and custom models are stored in your browser only.
