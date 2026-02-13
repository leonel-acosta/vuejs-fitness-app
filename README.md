# Fitness App

A Vue.js fitness tracker that guides you through a 30-day workout program following a **Push / Pull / Legs** split.

Built by following [this YouTube tutorial](https://www.youtube.com/watch?v=JAgeFLJYrUY).

## Features

- **Welcome page** - Introduces the training plan and the challenge to complete all 30 days
- **Dashboard** - Displays a grid of all 30 workout days, a random daily health tip, and a button to jump into the next incomplete workout
- **Workout page** - Shows warmup and workout exercises with sets, reps, and weight input fields; includes an exercise description modal for each exercise
- **Progress tracking** - Persists workout data to `localStorage` so progress is saved between sessions
- **Completion logic** - Prevents advancing to future workouts until the current one is complete, and locks the "Complete" button until all weight fields are filled in
- **Reset** - Clears all saved progress and starts over

## Tech stack

- **Vue 3** with Composition API (`<script setup>`)
- **Vite** for dev server and build
- **Font Awesome** for icons
- **localStorage** for data persistence

## Project structure

```
src/
  App.vue                         # Root component, state management, page routing
  utils/index.js                  # Workout program data, exercise descriptions, health facts
  components/
    layouts/Layout.vue            # Header, main content slot, footer
    Portal.vue                    # Teleport-based modal overlay
    Grid.vue                      # 30-day workout button grid
    pages/
      Welcome.vue                 # Landing page with challenge prompt
      Dashboard.vue               # Main hub with daily tip and workout grid
      Workout.vue                 # Exercise list with weight inputs
```

## Getting started

```bash
npm install
npm run dev
```

To build for production:

```bash
npm run build
npm run preview
```

## Acknowledgments

- Tutorial: [YouTube - Vue.js Fitness App](https://www.youtube.com/watch?v=JAgeFLJYrUY)
- [Vue.js Documentation](https://vuejs.org/)
- [Vite Documentation](https://vitejs.dev/)
