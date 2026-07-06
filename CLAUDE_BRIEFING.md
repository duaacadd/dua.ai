# Dua.ai — Project Briefing for Claude Code

## What is this?
A personalised birthday gift website for Absaar (my fiancé) built by Dua.
It's a fake "search engine" called Dua.ai where he can ask Dua questions and she answers them manually.

## Live site
https://duaacadd.github.io/dua.ai

## File structure
- `index.html` — main website (search engine + Q&A + about page)
- `game.html` — mini runner game "The Journey"
- `DuacaddHandwriting-Regular.otf` — Dua's actual handwriting font (used for answers)

---

## index.html — How it works

### Design
- Pink to purple pastel gradient background (`#f5d6e8` → `#e8d5f5` → `#d4b8f0`)
- Font: Poppins for UI, DuaHandwriting for all answers
- Glassmorphism cards (frosted white, backdrop-filter blur)
- Logo "Dua.ai" in Poppins, each letter a different purple/pink shade

### 3 tabs (nav):
1. **Search** — main search engine page
2. **My Questions** — live Q&A feed, auto-refreshes every 30 seconds
3. **About 💜** — Dua's letter to Absaar, written in her handwriting font
4. **Play 🎮** — links to game.html

### How questions/answers work:
- He types a question → hits "Dua Search"
- It submits silently to a **Google Form**
- Dua gets an email notification
- Dua types the answer in **Google Sheets** (column C)
- The website reads the sheet via CSV export every 30s
- His answer appears in her handwriting font

### Google Form details:
- Form URL: `https://docs.google.com/forms/d/1t9tUbhAhbSp9iViM7qkki-AZ_axNFISQzHILtd6Gcwk/formResponse`
- Entry ID: `entry.1630975485`

### Google Sheet details:
- Sheet CSV URL: `https://docs.google.com/spreadsheets/d/1nh7zs1taA07l6bennk1b9ikouNHUgduNIMRtqf0QsZ0/export?format=csv&gid=1297939200`
- Columns: A=Timestamp, B=Question, C=Answer, D=Answer Date
- Sheet is set to public viewer access

### Special features:
- **Confetti** (pink/purple) only on July 3rd (Absaar's birthday) and Feb 26th (Dua's birthday)
- Answers display in Dua's actual handwriting font
- Timestamps show when question was asked AND when Dua answered
- "My Questions" tab shows all Q&As newest first, live updating

### About page letter text:
"Hello my love, I know this is a little different from my usual gifts, but one day I just had this idea pop into my head. I must admit I entered into this project with only a vision and no knowledge to actually help me bring it to life. Thankfully for me we live in an age of AI, and with a little learning along the way I made this for you. It's very basic, but it's my way of showing that for you I would go to any length, for you I would learn coding. You have brought so much into my life and enriched it in a way that no one else has so far. You have given me a best friend, a lover and a sort of mentor all in one person. I love you very much and I hope any questions you have, this 'search engine' manages to answer them."
Signed: "Yours always, Dua.human 💜" — Date: July 3rd, 2026

---

## game.html — The Journey

### Concept
A side-scrolling runner game. A boy jumps over obstacles to reach a girl waiting with 3 cats.

### Characters needed (Dua is going to draw custom sprites):
- **Boy** — glasses, purple outfit, running
- **Girl** — glasses, pink dress, long dark hair, waiting
- **Fat orange tabby cat** — chonky
- **Tall lean orange tabby cat** — slim and tall
- **Normal grey tabby cat** — medium size, GREEN eyes

### Gameplay:
- 10 obstacles to clear (heart 💜, star ⭐, moon 🌙 pillars)
- Space / Tap to jump, double tap for double jump
- Progress bar showing how close he is
- When he reaches her: hearts float up, original chiptune love song plays
- Win message: "Just like in real life — he always finds his way to her"

### Audio:
- Jump sound: two quick ascending tones
- Death sound: descending tones
- Win song: original 8-bit chiptune melody (NOT Taylor Swift — copyright)
  plays automatically when boy reaches girl

### Current issue to fix:
- Dua wants to draw the characters herself and use them as sprites
- Waiting for her drawings before finalising characters

---

## ourspace.html — Our Space  ✅ BUILT & LIVE (as of July 7, 2026)

### Status
Finished and pushed live. Linked from index.html nav ("Our Space ✨").
Live at: https://duaacadd.github.io/dua.ai/ourspace.html
(It was previously a "coming soon" placeholder to protect the surprise — that
is now replaced with the real scene.)

### Concept
An interactive cozy-room scene built ON TOP of Dua's hand-drawn illustration
(`ourspace.png`, a transparent PNG at 3840×2160). It shows the couple on a
purple couch with their 3 cats, a sunset window, plants, a gramophone, and two
mugs. The room starts DARK; the visitor flips a switch to light it up.

### Key files
- `ourspace.html` — the whole scene (self-contained HTML/CSS/JS)
- `ourspace.png` — Dua's illustration (transparent bg; a dark purple wall+floor
  gradient shows through behind it via the `.bg` div)

### How it works / interactions
- **Light switch** (bottom-left, glows + pulses): click to toggle the room
  between dark and warm-lit. Dark = veil + dimmed illustration; on = warm glow,
  fairy lights twinkle, overlays fade in.
- **Fairy lights** strung across the top — SVG bulbs generated by JS along
  `FAIRY_POINTS`; they twinkle/spark only when lights are on.
- **Steam** rises from the two mugs on the right side table (SVG wisps).
- **Gramophone** (left side table, click target = `#gramoHotspot`): click to
  open a Spotify player panel; music notes drift out of it while a track plays.
  Playlist id = `3zwdfvPr50nMfvgTI8DZmH`. Uses the Spotify iFrame API to know
  when audio is actually playing.
- **Press `G`** toggles a 10% alignment grid (dev helper for positioning
  overlays on the illustration).

### Coordinate system (important for future overlay tweaks)
The SVG overlay uses the illustration's own pixel space: `viewBox="0 0 3840 2160"`.
So steam/gramophone hotspot are placed in image px. The light switch, timer, and
japan overlays use percent-of-scene CSS vars (`--sw-*`, `--tmr-*`, `--jp-*`).

### Dead code (safe to ignore or clean up)
- `.timer` and `.japan` CSS classes + their `--tmr-*` / `--jp-*` vars exist but
  have NO matching elements in the HTML, so nothing renders for them.
- `japan_src.avif` and `ourspace_whitebg_backup.png` were deleted (unused).

---

## Things still to do / known issues:
- [ ] "My Questions" and "About" tabs may not be switching properly — verify onclick works
- [ ] Game characters need replacing with Dua's custom drawn sprites
- [ ] Test that Google Form submission actually works end to end

## Git workflow reminder:
git add .
git commit -m "your message"
git push

## Colours reference:
- Primary purple: #9b5de5
- Light purple: #b06ab3
- Pink: #c47fc9 / #e07898
- Dark text: #3d2c4e
- Background gradient: #f5d6e8 → #e8d5f5 → #d4b8f0
