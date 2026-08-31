# Stack Shift — Build Log

## Project summary

**Stack Shift** is a browser-based Tetris-inspired game created as a standalone HTML experience. The current public build includes classic block-stacking mechanics, progressive difficulty, target-row challenges, combo scoring, a rechargeable SHIFT meter, and a player-controlled bomb.

- Public game: <https://asalomon715.github.io/stack-shift/>
- Source repository: <https://github.com/asalomon715/stack-shift>
- Current public deployment: <https://github.com/asalomon715/stack-shift/actions/runs/33438003586>
- Latest deployed game commit: `e9f666e80e689888eb8c3a3af8ee569b1e54098f`

## Major prompts and resulting changes

### 1. Initial playable prototype

**Prompt:** Create a mini Tetris game that could be tested and improved through play.

**Changes:**

- Built a 10-column by 20-row game board.
- Added all seven standard tetromino shapes with shuffled-bag generation.
- Added movement, rotation, soft drop, hard drop, pause, and restart controls.
- Added scoring, cleared-line totals, levels, a ghost piece, and next-piece preview.
- Added keyboard and mobile touch controls.
- Created the neon arcade visual identity and **Stack Shift** title.

### 2. Faster and more compact play

**Prompt:** Increase drop speed and reduce the height so the game fits on a 13-inch computer screen.

**Changes:**

- Reduced the initial visual board size for smaller laptop displays.
- Increased the starting automatic drop speed.
- Tightened header, footer, and surrounding spacing.
- Added responsive rules for short screens.

### 3. Progressive difficulty

**Prompt:** Make drops accelerate over time, then level out at a high speed so the game does not become impossible.

**Changes:**

- Added a continuous four-minute speed ramp.
- Added a minimum drop-delay cap to prevent unlimited acceleration.
- Made the displayed level advance every 30 seconds or after each ten cleared lines.
- Added a small additional acceleration bonus for each ten cleared lines.

### 4. Layout experimentation and selected visual version

**Prompts:** Explore using more of the screen, then return to the second visual version while keeping the newer speed system.

**Changes:**

- Tested a full-window layout and a compressed three-column layout.
- Restored the preferred wide, airy second-version layout.
- Restored **Archivo Black** headings and **IBM Plex Mono** interface text.
- Preserved the newer progressive-speed logic during the visual rollback.
- Converted the game into a self-contained `index.html` with inline CSS and JavaScript.

### 5. Final board positioning

**Prompts:** Use a 270×540 game block and move the board upward so its top aligns with “SHIFT.”

**Changes:**

- Set the visible game canvas to 270×540 pixels.
- Set its bordered container to 272×542 pixels.
- Raised the desktop board by 52 pixels.
- Preserved normal mobile positioning.

### 6. First public release

**Prompt:** Export the game to GitHub and provide a public shareable link.

**Changes:**

- Published the standalone game to `asalomon715/stack-shift`.
- Added an automated GitHub Pages deployment workflow.
- Enabled the public game at <https://asalomon715.github.io/stack-shift/>.

### 7. Clearer player instructions

**Prompt:** Add short instructions explaining how to clear rows and avoid running out of space.

**Changes:**

- Added the opening instructions:
  - “Complete full rows to clear them.”
  - “Don’t let the stack reach the top.”
- Kept movement controls separate from the objective.

### 8. New entertainment mechanics

**Prompt:** Add bombs, a meter, target-row challenges, and scoring bonuses.

**Changes:**

- Added a rechargeable **SHIFT meter**.
- Each cleared row charges the meter by 25%.
- Added periodic gold target rows with a three-piece deadline.
- Clearing a gold target awards 500 points and 50% SHIFT charge.
- Added consecutive-clear combo multipliers up to ×5.
- Added floating messages, glow effects, bomb flashes, and new sound cues.
- Added five-second Surge mode with slower gravity and double scoring.

### 9. Bomb control revision

**Prompt:** Use the letter `B` for bombs and display “CLICK B FOR BOMB” when one becomes available.

**Changes:**

- Changed special-mode activation from `S` to `B`.
- Added a large **CLICK B FOR BOMB** availability popup.
- Changed the meter button to **Press B · Bomb ready** when fully charged.
- Added a mobile **BOMB** button.
- Made the next piece a one-block bomb after activation.
- Bomb placement removes a 3×3 area and awards bonus points.

### 10. Final instruction placement

**Prompt:** Remove bomb information from the opening instructions and place it below the sidebar.

**Changes:**

- Restored the opening screen to only the core row-clearing and survival rules.
- Added this explanation below the SHIFT section:
  - “Clear rows to fill SHIFT. When ready, press B to clear a 3×3 area.”

### 11. Final speed adjustment

**Prompt:** Reduce the latest experimental speed by 15%.

**Changes:**

- Changed the starting drop delay from 364 ms to 419 ms.
- Changed the maximum-speed delay from 67 ms to 77 ms.
- Scaled the ten-line acceleration adjustment from 20 ms to 23 ms.
- Retained the four-minute speed ramp.

## Current gameplay specification

### Standard controls

| Input | Action |
|---|---|
| `←` / `→` | Move piece |
| `↑` | Rotate piece |
| `↓` | Soft drop |
| `Space` | Hard drop |
| `B` | Activate a ready bomb and Surge mode |
| `P` | Pause or resume |
| `R` | Restart |

### Difficulty

- Starting automatic drop delay: **419 ms per row**.
- Maximum-speed delay: **77 ms per row**.
- Time to reach maximum speed: **four minutes of active play**.
- Paused time does not advance difficulty.
- Every ten cleared lines increases difficulty slightly sooner.

### SHIFT and bomb system

- One cleared row adds **25%** SHIFT charge.
- A cleared gold target adds **50%** SHIFT charge.
- At 100%, the game displays **CLICK B FOR BOMB**.
- Pressing `B` activates five seconds of slowed gravity and double scoring.
- The next piece becomes a bomb.
- A placed bomb destroys a **3×3** area.

### Target-row challenges

- The first target appears after eight placed pieces.
- A target must be cleared within three additional pieces.
- Successful targets award 500 points and return after nine pieces.
- Missed targets return after six pieces.

### Bonuses

- Consecutive piece placements that clear rows build a multiplier.
- The multiplier increases up to **×5**.
- Surge mode doubles scoring.
- Bomb placement awards an additional score bonus.

## Publishing workflow

The public site deploys automatically when `index.html` is updated on the repository’s `main` branch. GitHub Actions packages the repository as a Pages artifact and deploys it to the public URL.

The current local supporting files are:

- `index.html` — standalone public game containing its CSS and JavaScript.
- `styles.css` — editable stylesheet source retained for development.
- `game.js` — editable game-engine source retained for development.
- `BUILD_LOG.md` — this development record.

