# Tutorial: Running a Vue 3 Project with Vite

This tutorial will guide you through setting up a Vue 3 project using Vite. We'll cover installing dependencies, running the development server, and building the project for production.

---

## Prerequisites

Before starting, ensure you have the following installed:

1. **Node.js** (version 16 or higher) — [Download Node.js](https://nodejs.org/).
2. **npm** (comes with Node.js) or **yarn** (optional).

---

## Setting Up the Project

1. **Download the Project**:
   - If you're using Git, run:
     ```bash
     git clone https://github.com/your-repository/your-project.git
     ```
   - If the project is downloaded as an archive, extract it.

2. **Navigate to the Project Directory**:
   ```bash
   cd your-project
   ```

3. **Install Dependencies**:
   - Run the following command:
     ```bash
     npm install
     ```
   - This will install all the necessary packages listed in `package.json`.

---

## Running the Project

1. **Start the Development Server**:
   - Run the following command:
     ```bash
     npm run dev
     ```
   - After the server starts, your browser will open with the address `http://localhost:5173`.

2. **Edit the Code**:
   - Any changes you make to the project files will automatically reflect in the browser thanks to Hot Module Replacement (HMR).

---

## Building the Project for Production

1. **Build the Project**:
   - Run the following command:
     ```bash
     npm run build
     ```
   - The built files will be placed in the `dist` folder.

2. **Preview the Production Build**:
   - To locally test the production build, run:
     ```bash
     npm run preview
     ```
   - This will start a server, and you can open the project in your browser at `http://localhost:4173`.

---

## Project Structure

```
your-project/
├── node_modules/          # Installed dependencies
├── public/                # Static files (e.g., images, fonts)
│   └── favicon.ico        # Site icon
├── src/                   # Project source code
│   ├── assets/            # Resources (images, styles, etc.)
│   ├── components/        # Vue components
│   ├── App.vue            # Root application component
│   └── main.js            # Application entry point
├── index.html             # Main HTML file
├── package.json           # Project dependencies and scripts
├── vite.config.js         # Vite configuration
└── README.md              # Project documentation
```

---

## Available Commands

- **`npm run dev`**: Start the development server.
- **`npm run build`**: Build the project for production.
- **`npm run preview`**: Preview the production build locally.

---

## Configuring the Project

- **Adding Components**: Create new `.vue` files in the `src/components/` folder and import them into `App.vue` or other components.
- **Adding Styles**: Use global styles in `src/assets/` or local styles within components.
- **Configuring Vite**: Modify the `vite.config.js` file to customize the build, add plugins, or set up aliases.

---

## Example Code

### `App.vue`
```vue
<template>
  <div id="app">
    <h1>Welcome to Vue 3 + Vite!</h1>
    <p>This is a starter template for building modern web applications.</p>
  </div>
</template>

<script setup>
// Component logic
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
```

---

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

Now you're ready to start developing with Vue 3 and Vite! 🚀
