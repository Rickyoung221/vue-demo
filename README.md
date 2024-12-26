# vue-demo

A project for self-learning Vue.js (Vue 3) and Element Plus. This project includes a **mini snake game** built entirely with Vue.

## Features

- **Mini Snake Game**: A classic snake game implemented with Vue.js.
- **Responsive Grid Layout**: Built using modern CSS for smooth gameplay.
- **Dynamic State Management**: Efficient handling of the snake's movement, collisions, and food generation.
- **Element Plus Integration**: Leverages Element Plus for styling and component integration.

---

## Getting Started

Follow these steps to run the project locally.

### Prerequisites

Ensure you have the following installed:

- **Node.js**: [Download and install Node.js](https://nodejs.org/).
- **npm**: Comes with Node.js.

### Installation

Clone the repository and install dependencies:

```
git clone https://github.com/your-username/vue-demo.git
cd vue-demo
npm install
```

### Running the Development Server

To start the development server and play the game:

```
npm run serve
```

Open your browser and navigate to: http://localhost:8080.

### Building for Production

To build the project for production:

```
npm run build
```

The compiled files will be available in the `dist` directory.

### Linting and Code Fixes

To lint your files and automatically fix issues:

```
npm run lint
```

---

## How to Play the Snake Game

1. Click the **"Start Game"** button to begin.
2. Use the **arrow keys** (`↑`, `↓`, `←`, `→`) to control the snake's movement.
3. Eat the food (red cells) to grow the snake and increase your score.
4. Avoid hitting the walls or the snake's own body; otherwise, the game will end.

---

## Technologies Used

- **Vue.js (Vue 3)**: Progressive JavaScript framework for building user interfaces.
- **Element Plus**: Vue 3 UI library for modern, elegant designs.
- **CSS Grid**: For building the game board and ensuring responsiveness.
- **JavaScript (ES6)**: For handling game logic and state management.

---

## Project Structure

```
vue-demo/
├── public/              # Static assets
├── src/
│   ├── assets/          # Project-specific assets
│   ├── components/      # Vue components, including the Snake Game
│   ├── App.vue          # Root Vue component
│   ├── main.js          # Entry point for the Vue app
│   └── styles/          # Global and component-specific styles
├── package.json         # Project metadata and dependencies
└── README.md            # Project documentation
```

---

## Customize the Project

To modify the project or extend its functionality, see the [Vue.js Configuration Reference](https://cli.vuejs.org/config/).

---

## Screenshots

### Game Board

<img src="https://p.ipic.vip/k8wafk.png" alt="image-20241226023616725" style="zoom:33%;" />

---

## Contributing

Feel free to fork this project and submit pull requests. Contributions are welcome!

---

## License

This project is licensed under the MIT License.
