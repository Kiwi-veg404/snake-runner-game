# Snake Runner

A classic snake game built with vanilla JavaScript, HTML5 Canvas, and CSS. Control the snake, collect food, and try to beat your high score!

## Features

- 🎮 Smooth snake movement with arrow key controls
- 🎯 Score tracking with localStorage-persisted high score
- 🎨 Beautiful gradient UI design
- ⏸️ Pause/Resume functionality
- 📱 Responsive canvas game board
- 💥 Collision detection (walls and self)
- ✨ Visual effects with grid, gradients, and shine

## How to Play

1. Open `index.html` in any modern web browser
2. Click "Start Game" to begin
3. Use arrow keys to control the snake:
   - ↑ Up Arrow - Move up
   - ↓ Down Arrow - Move down
   - ← Left Arrow - Move left
   - → Right Arrow - Move right
4. Collect the red food to grow your snake and earn points
5. Avoid hitting the walls or running into yourself
6. Try to beat your high score!

## Installation

No installation required! Simply:

```bash
# Clone or download this repository
cd snake-runner-game

# Open the game in your browser
start index.html  # Windows
# or
open index.html   # macOS
# or
xdg-open index.html  # Linux
```

Alternatively, you can serve it with any local web server:

```bash
# Using Python 3
python -m http.server 8000

# Using Node.js (http-server)
npx http-server

# Then open http://localhost:8000 in your browser
```

## Game Rules

- Each food item collected adds 10 points to your score
- The snake grows by one segment each time it eats food
- Game ends if the snake hits a wall or collides with itself
- Your high score is automatically saved in the browser

## Technologies Used

- HTML5 Canvas for game rendering
- Vanilla JavaScript for game logic
- CSS3 for styling and animations
- LocalStorage for high score persistence

## Project Structure

```
snake-runner-game/
├── index.html    # Main HTML structure
├── style.css     # Game styling
├── game.js       # Game logic and mechanics
└── README.md     # This file
```

## Browser Compatibility

Works on all modern browsers that support:
- HTML5 Canvas
- ES6 JavaScript
- CSS3
- LocalStorage

## License

Free to use and modify for personal and educational purposes.

## Enjoy the game! 🐍
