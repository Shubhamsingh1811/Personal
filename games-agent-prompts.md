# Games — Code Check + Big Prompt for the other AI agent (100 tokens/day)

Date: 14 Nov 2026. Owner: Shubham. Rule: the other agent does the coding work
so Muse's tokens are saved. Muse only checks code and writes prompts.
Both games are single-file HTML, full English, touch-first for phones.
DO NOT break that: no external CDN, no separate CSS/JS files, everything inline.

## 1. Code check — what I found

### Game 1: Run & Transform (`run_and_transform.html`, 702 KB, 1362 lines)
- A runner game: run, then TRANSFORM into a vehicle (car / plane) to cross
  different terrain. Has START, BOSS level, LEVEL CLEAR, GAME OVER, Retry, Menu.
- The file is big because a minified 3D/engine library is bundled inline
  (function names like se, ae, oe — minified code). That is normal, do not
  remove the library.
- MISSING / WEAK:
  1. **No save at all** — `localStorage` appears 0 times. Close the game and
     level, score and unlocks are gone. Add save: highest level reached,
     best score, total coins.
  2. **No real sound** — no music, no transform whoosh, no win jingle.
     Add small WebAudio beeps (no audio files, no internet needed) + a
     mute button on the HUD.
  3. **No pause button, no How to Play screen** — new players do not know
     when to transform. Add a 3-line How to Play on the menu + Pause button.
  4. **No coins / rewards** — add coins on the track, a simple shop to
     change the runner colour (3 colours, costs 50 / 100 / 200 coins).
  5. **No level select** — add a level select screen (levels 1-10 with
     lock/unlock + stars).

### Game 2: Arrow Escape — Tap to Clear (`arrow_escape_20_levels.html`, 40 KB, 823 lines)
- A puzzle game: tap arrows, each arrow flies out in its direction only if
  its path is clear. 20 levels in one `LEVELS` array, 4x4 up to 10x10 grids.
- GOOD already: localStorage save works, 3-4 hearts per level, 3 hints,
  stars per level, WebAudio blip sounds, level names, clean readable code.
- MISSING / WEAK:
  1. **No Undo button** — one wrong tap costs a heart. Add Undo (1 per level,
     or costs 1 hint).
  2. **Only 20 levels** — add levels 21-30 (11x11 and 12x12, harder, more
     blocked arrows). Keep the same LEVELS format.
  3. **No move counter / timer** — add moves used + best moves per level
     (saved in localStorage), show stars from moves: 3 stars = fewest moves.
  4. **No level select grid** — add a grid showing all 20+ levels with
     stars earned, so the player can replay any level.
  5. **No win celebration** — add a small confetti burst on level clear
     (canvas confetti, no library, no internet).

## 2. MASTER PROMPT — paste this into the other AI agent (with BOTH game files attached)

> You are an expert HTML5 game developer. I will upload TWO single-file HTML
> games. Work on ONE game at a time and return the COMPLETE updated single
> HTML file every time — never return only a code snippet, never split the
> file into separate CSS/JS files, and never use any external CDN, library
> link, image URL or font URL. Everything must be inline in one HTML file,
> offline, and must open by double-clicking the file on a phone or laptop.
> All visible text must be in FULL ENGLISH only, no Hindi.
>
> GAME 1 — "Run & Transform" (run_and_transform.html, a runner where the
> character transforms into a car / plane to cross terrain, with START, BOSS,
> LEVEL CLEAR and GAME OVER screens):
> 1. Add localStorage save: highest level unlocked, best score, total coins.
>    Show best score on the menu. Progress must survive closing the browser.
> 2. Add WebAudio sound effects with no audio files: jump beep, transform
>    whoosh, coin ding, win jingle, lose sound. Add a mute button on the HUD.
> 3. Add a Pause button and a How to Play screen on the menu (3 short lines
>    explaining when to transform).
> 4. Add coins on the track and a simple colour shop on the menu (3 runner
>    colours costing 50 / 100 / 200 coins, saved in localStorage).
> 5. Add a level select screen (levels 1-10, locked levels greyed out,
>    stars for completed levels).
> 6. Do NOT change the core running/transform controls. Do NOT remove the
>    bundled engine code. Test mentally: menu loads, START works, transform
>    works, game over and level clear both work, reload keeps the save.
>
> GAME 2 — "Arrow Escape" (arrow_escape_20_levels.html, a tap puzzle: tap an
> arrow, it flies out only if its path is clear; 20 levels in a LEVELS array,
> hearts, hints, stars, localStorage save already work):
> 1. Add an Undo button (1 free undo per level; a second undo costs 1 hint).
> 2. Add levels 21-30 in the SAME LEVELS array format (bigger grids up to
>    12x12, harder layouts, more blocked arrows). All 30 levels must be
>    solvable — verify each level's solution path before finishing.
> 3. Add a move counter and best-moves record per level in localStorage.
>    Stars: 3 stars if moves <= best solution, 2 stars if +2 moves, else 1.
> 4. Add a level select grid (all levels with stars earned, locked levels
>    greyed out).
> 5. Add a small canvas confetti burst on level clear (no library, no net).
> 6. Do NOT change the tap rules or the existing 20 levels. Test mentally:
>    level 1 is solvable, a blocked arrow shows the blocked feedback, hints
>    still work, reload keeps stars and unlocked levels.
>
> For BOTH games: keep the file single-file and offline, keep all text in
> English, keep the touch controls big enough for a phone, and at the end
> list exactly what you changed in 5 bullet points and what you tested.

## 3. Daily split — 100 tokens/day, paste ONE chunk per day (do not paste all at once)

**Day 1 — Run & Transform, save + sound only:**
> Open run_and_transform.html (attached). Return the COMPLETE single HTML
> file. Add ONLY these two things: (1) localStorage save for highest level,
> best score and total coins, shown on the menu, surviving reload; (2)
> WebAudio sound effects with no audio files (jump, transform whoosh, coin,
> win, lose) plus a mute button. Do not change anything else. No CDN, no
> separate files, all English.

**Day 2 — Run & Transform, pause + coins + level select:**
> Open the Day 1 updated run_and_transform.html. Return the COMPLETE single
> HTML file. Add ONLY: (1) Pause button + How to Play screen (3 short
> English lines); (2) coins on the track + a colour shop (3 colours, 50 /
> 100 / 200 coins, saved); (3) level select screen 1-10 with locks and
> stars. Do not change controls or sound. No CDN, single file, all English.

**Day 3 — Arrow Escape, undo + moves + level select:**
> Open arrow_escape_20_levels.html (attached). Return the COMPLETE single
> HTML file. Add ONLY: (1) Undo button, 1 free per level, second costs 1
> hint; (2) move counter + best moves per level in localStorage, stars from
> moves; (3) level select grid with stars. Do not change tap rules or the
> 20 levels. No CDN, single file, all English.

**Day 4 — Arrow Escape, levels 21-30 + confetti:**
> Open the Day 3 updated arrow_escape_20_levels.html. Return the COMPLETE
> single HTML file. Add ONLY: (1) levels 21-30 in the same LEVELS format,
> up to 12x12, harder, every level verified solvable; (2) canvas confetti
> on level clear, no library. Do not change anything else. No CDN, single
> file, all English.

## 4. Flow credits plan — use before 11 Dec 2026

- Main account (shubham61690@gmail.com): **970 credits left, reset 11 Dec
  8:38 AM**. 1 Veo Fast clip = 20 credits. 970 / 20 = **48 clips = 8 full
  videos** (6 clips each). Do NOT use Quality (100/clip).
- Second account: **50 credits/day = 2 clips/day free**. Use it FIRST every
  day, then the main account for the rest.
- Order: (1) finish the WebSetu full explainer video (6 clips, file:
  ~/workspace/websetu-video/websetu-full-explainer-video.md, Hindi voice in
  Clipchamp, Aarti voice); (2) one short video per sample site/service
  (Sunrise, Dental, Gym, Salon, Restaurant, Review QR, GBP setup) — 1 video
  every 2-3 days. If a clip fails, regenerate it the same day; do not let
  credits sit unused till 10 Dec.

## 5. Free AI tools — what each one is actually for (use the right one)

- **Gemini app (gemini.google.com, Google AI Pro via Jio recharge):**
  chat for scripts, captions, ideas, explanations. Ask in Hinglish, get
  drafts. Do NOT judge it by coding — use it for words, not code.
- **AI Studio (aistudio.google.com):** Google's free builder. "Build" tab:
  describe an app/game in plain words, it builds a working preview. Also
  gives a free Gemini API key (free tier) for apps. Use for quick prototypes.
- **Stitch (stitch.google.com):** DESIGN ONLY, not a game engine. Describe a
  screen ("a login screen for a coaching app, blue and white"), it gives a
  UI design as HTML/CSS. Then add real logic in Antigravity / the other
  agent / Muse. Never expect a playable game from Stitch alone.
- **Antigravity (antigravity.google/download):** Google's free coding agent
  (free plan, weekly quota; Pro $20/mo). Describe a website/app in plain
  words, the agent writes and tests the code. Best for full websites and
  frontend demos. Hosting is separate: GitHub Pages / InfinityFree.
- **GitHub Copilot Free (VS Code):** free with a GitHub account, no card:
  2,000 completions + 50 chats/month. Best for fixing code line by line
  while you type.
- **Muse (this chat):** free plan has weekly limits — use it for checking,
  planning, prompts and verification, and let the other agent / Antigravity
  do the heavy code writing. That is the whole point of this file.
