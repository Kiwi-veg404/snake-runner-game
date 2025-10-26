# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

Snake Runner is a classic snake game built with vanilla JavaScript, HTML5 Canvas, and CSS. It's a simple, self-contained browser game with no build process or dependencies.

## Architecture

### Core Components

**game.js** - Main game engine containing:
- **Game Loop**: `update()` runs at 100ms intervals via `setInterval`
- **State Management**: Global variables track snake position array, direction vector, food position, score, and game status (running/paused)
- **Collision Detection**: Separate checks for wall collision (boundary detection) and self-collision (snake body overlap)
- **Rendering Pipeline**: `draw()` function handles canvas rendering including grid, snake with gradient effect, and food with shine effect
- **LocalStorage Integration**: High scores persist in browser storage via `localStorage.getItem/setItem`

**index.html** - DOM structure with:
- Canvas element (600x400px fixed size)
- Score/high-score display panels
- Start/Pause button controls
- Instructions panel

**style.css** - Visual styling with purple gradient theme

### Key Technical Details

- **Grid System**: 20px grid size, 30x20 tile game board (600x400 canvas)
- **Movement**: Direction stored as vector `{x, y}`, prevents 180-degree turns by checking current direction axis
- **Snake Growth**: Implemented by adding new head position without removing tail when food is eaten
- **Food Placement**: Randomized with validation to avoid spawning on snake body
- **Visual Effects**: Snake body uses gradient opacity based on segment distance from head; food has circular shine overlay

## Development Commands

### Running the Game

```bash
# Open directly in browser (Windows)
start index.html

# Or serve with local web server (Python)
python -m http.server 8000
# Then navigate to http://localhost:8000

# Or serve with Node.js
npx http-server
```

### Testing
No automated tests exist. Manual testing via browser.

### Debugging
Use browser DevTools. The game state is accessible via global variables in the console:
- `snake` - Current snake segments array
- `score` - Current game score
- `highScore` - Stored high score
- `gameRunning` / `gamePaused` - Game state flags

## Code Modification Guidelines

### Adding Features
- All game logic lives in `game.js` as a single file
- Use existing global state pattern (no modules or frameworks)
- Maintain 100ms game loop interval for consistent gameplay
- Follow existing naming: camelCase for functions/variables

### Modifying Game Mechanics
- Snake movement: Modify `update()` function
- Collision detection: Wall collision at line 103, self-collision at line 109
- Scoring: Points awarded at line 121, currently hardcoded as +10
- Rendering: All canvas drawing in `draw()` function starting at line 156

### Canvas Rendering Pattern
All drawing uses 2D context (`ctx`). Current pattern:
1. Clear canvas with background fill
2. Draw grid (optional decorative element)
3. Draw snake segments (head to tail with gradient)
4. Draw food with shine effect
5. Game over overlay drawn separately in `gameOver()`

### State Persistence
Only high score uses localStorage. To add more persistent data, follow pattern at lines 14 and 128.

## File Structure
```
snake-runner-game/
├── index.html    # HTML structure and DOM elements
├── style.css     # Visual styling (purple gradient theme)
├── game.js       # All game logic (canvas rendering, physics, input)
└── README.md     # User-facing documentation
```

## Important Constraints
- No package manager or dependencies
- No build/compile step required
- Vanilla JavaScript only (ES6 features used: arrow functions, const/let, template literals)
- Must work in browser without transpilation
- Canvas API and LocalStorage are only external APIs used
