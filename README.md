# zoesunicorndash
Activities for kids
# Unicorn Dash

A single-file, canvas-based endless runner. Your unicorn auto-runs across
a neon dusk landscape — jump and glide over rocks, collect stars and
rainbow gems for points, and try to beat your best score.

No build step, no dependencies, no backend — everything (markup, styles,
game logic) lives in one file: `unicorn_dash.html`.

## How to Run It

Just open `unicorn_dash.html` in any modern browser — locally (double-click
the file) or hosted from any static file server / GitHub Pages. There's
nothing to install and no other files it depends on.

## How to Play

| Action | Keyboard | Touch / Mouse |
|---|---|---|
| Start / Restart | `Space` or `↑` | Tap / click the canvas |
| Jump | `Space` or `↑` | Tap / click and release |
| Glide (fall slower) | Hold `Space` or `↑` | Press and hold |

- The unicorn jumps once from the ground (no double-jump) and can only
  glide while airborne.
- **Rocks** (two sizes/heights) are obstacles — touching one ends the run.
- **Stars** are worth **1 point**; the rarer **rainbow gems** (~15% spawn
  chance) are worth **5 points**.
- Your score is labeled "Sparkles" in the HUD; your **Best** score is
  saved automatically in the browser via `localStorage`
  (`unicornDashBest`) and persists across sessions on the same device/
  browser.
- The game gradually speeds up the longer you survive.

## Game States

1. **Menu** — title screen with a "Begin the Run" button.
2. **Playing** — the endless runner itself.
3. **Game Over** — "The Vale Grows Quiet" screen showing sparkles
   gathered (and a "new best!" note if you beat your record), with a
   "Run Again" button to restart instantly.

## Technical Notes

- Pure HTML/CSS/JS — rendering is done on an HTML5 `<canvas>` element via
  `requestAnimationFrame`; no external libraries or web fonts are loaded
  (the `Fredoka` font reference falls back to system fonts if it isn't
  installed locally).
- Responsive: the canvas resizes with the window via a `resize` listener
  and is capped at a 900px-wide, 16:9 frame.
- Best score persistence is wrapped in `try/catch` around `localStorage`
  calls, so the game still works (it just won't remember your best) in
  environments where `localStorage` is blocked (e.g. some in-app browsers
  or private/incognito modes with storage disabled).
- No network calls, no analytics, no external assets — fully self-contained
  and works offline once loaded.
