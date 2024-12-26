<template>
  <div class="game-container">
    <h1>Snake Game</h1>
    <div class="game-board">
      <div
        v-for="(cell, index) in grid"
        :key="index"
        class="cell"
        :class="{ snake: isSnakeCell(index), food: isFoodCell(index) }"
      ></div>
    </div>
    <div class="controls">
      <button @click="startGame">Start Game</button>
      <p>
        Score: <span>{{ score }}</span>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      gridSize: 20, // The size of the game grid
      grid: Array(400).fill(null), // 20x20 grid represented as a 1D array
      snake: [42, 41, 40], // Snake's initial position
      direction: "RIGHT", // Snake's initial direction
      foodPosition: null, // Food's position on the grid
      gameInterval: null, // Interval ID for game loop
      score: 0, // Player's score
    };
  },
  methods: {
    // Start the game
    startGame() {
      this.resetGame();
      this.spawnFood();
      this.gameInterval = setInterval(this.moveSnake, 200);
      window.addEventListener("keydown", this.changeDirection);
    },
    // Reset the game to its initial state
    resetGame() {
      clearInterval(this.gameInterval);
      this.snake = [42, 41, 40]; // Reset snake position
      this.direction = "RIGHT"; // Reset direction
      this.foodPosition = null;
      this.score = 0;
    },
    // Spawn food at a random position
    spawnFood() {
      let newFoodPosition;
      do {
        newFoodPosition = Math.floor(Math.random() * this.grid.length);
      } while (this.snake.includes(newFoodPosition)); // Ensure food is not on the snake
      this.foodPosition = newFoodPosition;
    },
    // Move the snake
    moveSnake() {
      const head = this.snake[0];
      let newHead;

      switch (this.direction) {
        case "UP":
          newHead = head - this.gridSize;
          break;
        case "DOWN":
          newHead = head + this.gridSize;
          break;
        case "LEFT":
          newHead = head - 1;
          break;
        case "RIGHT":
          newHead = head + 1;
          break;
      }

      // Check for collisions
      if (
        newHead < 0 || // Collides with the top
        newHead >= this.grid.length || // Collides with the bottom
        (this.direction === "LEFT" && head % this.gridSize === 0) || // Collides with the left wall
        (this.direction === "RIGHT" && newHead % this.gridSize === 0) || // Collides with the right wall
        this.snake.includes(newHead) // Collides with itself
      ) {
        alert(`Game Over! Your score: ${this.score}`);
        this.resetGame();
        return;
      }

      // Check if food is eaten
      if (newHead === this.foodPosition) {
        this.snake.unshift(newHead); // Grow the snake
        this.score += 10; // Update score
        this.spawnFood(); // Spawn new food
      } else {
        this.snake.pop(); // Remove the tail
        this.snake.unshift(newHead); // Add a new head
      }
    },
    // Change the snake's direction
    changeDirection(event) {
      const keyDirectionMap = {
        ArrowUp: "UP",
        ArrowDown: "DOWN",
        ArrowLeft: "LEFT",
        ArrowRight: "RIGHT",
      };
      const newDirection = keyDirectionMap[event.key];

      if (newDirection) {
        const oppositeDirections = {
          UP: "DOWN",
          DOWN: "UP",
          LEFT: "RIGHT",
          RIGHT: "LEFT",
        };

        // Prevent the snake from reversing direction
        if (newDirection !== oppositeDirections[this.direction]) {
          this.direction = newDirection;
        }
      }
    },
    // Check if the cell is part of the snake
    isSnakeCell(index) {
      return this.snake.includes(index);
    },
    // Check if the cell is the food
    isFoodCell(index) {
      return index === this.foodPosition;
    },
  },
  beforeUnmount() {
    clearInterval(this.gameInterval);
    window.removeEventListener("keydown", this.changeDirection);
  },
};
</script>

<style scoped>
.game-container {
  text-align: center;
  margin-top: 20px;
  font-family: Arial, sans-serif;
}

.game-board {
  display: grid;
  grid-template-columns: repeat(20, 20px);
  grid-template-rows: repeat(20, 20px);
  gap: 1px;
  margin: 20px auto;
  width: 420px;
  height: 420px;
  background-color: #fafafa;
  border: 2px solid #333;
}

.cell {
  width: 20px;
  height: 20px;
  background-color: #e0e0e0;
}

.cell.snake {
  background-color: #4caf50;
}

.cell.food {
  background-color: #f44336;
}

.controls {
  margin-top: 10px;
}

button {
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  border: none;
  background-color: #4caf50;
  color: white;
  border-radius: 5px;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #45a049;
}
</style>
