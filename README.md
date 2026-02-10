# 🏋️ Vue.js Fitness Tracker App

A modern fitness tracking application built with Vue.js that allows users to log workouts, track progress, and achieve their fitness goals.

[![Vue.js](https://img.shields.io/badge/Vue.js-3.x-4FC08D?logo=vue.js&logoColor=white)](https://vuejs.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📋 Table of Contents

- [Features](#-features)
- [Demo](#-demo)
- [Technologies](#-technologies)
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Usage](#-usage)
- [Project Structure](#-project-structure)
- [Available Scripts](#-available-scripts)
- [Roadmap](#-roadmap)
- [Contributing](#-contributing)
- [License](#-license)
- [Contact](#-contact)
- [Acknowledgments](#-acknowledgments)

## ✨ Features

- 📊 **Interactive Dashboard** - Visualize your progress with charts and statistics
- 💪 **Workout Logging** - Record exercises, sets, reps, and weight
- 📅 **Training Calendar** - Plan and schedule your workout sessions
- 🎯 **Goal Setting** - Define and achieve your fitness goals
- 📈 **Progress Tracking** - Monitor your evolution over time
- 🔐 **User Authentication** - Secure login and registration system
- 📱 **Responsive Design** - Compatible with mobile devices and tablets
- 🌙 **Dark Mode** - Adaptable interface to visual preferences

## 🎥 Demo

_[Coming soon: Add screenshots or GIF of the application in action]_

## 🛠 Technologies

This project is built with the following technologies:

- **Frontend Framework:** [Vue.js 3](https://vuejs.org/)
- **Build Tool:** [Vite](https://vitejs.dev/)
- **Routing:** [Vue Router](https://router.vuejs.org/)
- **State Management:** [Pinia](https://pinia.vuejs.org/) / [Vuex](https://vuex.vuejs.org/)
- **Styling:** CSS3 / [Tailwind CSS](https://tailwindcss.com/) / [Bootstrap](https://getbootstrap.com/)
- **Charts:** [Chart.js](https://www.chartjs.org/) / [ApexCharts](https://apexcharts.com/)
- **Icons:** [Font Awesome](https://fontawesome.com/) / [Heroicons](https://heroicons.com/)
- **Backend/Database:** [Firebase](https://firebase.google.com/) / [Supabase](https://supabase.com/) _(optional)_

## 📦 Prerequisites

Before you begin, make sure you have installed:

- [Node.js](https://nodejs.org/) (version 16.x or higher)
- [npm](https://www.npmjs.com/) (version 8.x or higher) or [yarn](https://yarnpkg.com/)
- [Git](https://git-scm.com/)

Verify installed versions:

```bash
node --version
npm --version
git --version
```

## 🚀 Installation

### 1. Clone the repository

```bash
git clone https://github.com/leonel-acosta/vuejs-fitness-app.git
cd vuejs-fitness-app
```

### 2. Install dependencies

With npm:
```bash
npm install
```

With yarn:
```bash
yarn install
```

### 3. Configure environment variables

Create a `.env` file in the root of the project:

```bash
cp .env.example .env
```

Edit the `.env` file with your credentials:

```env
VITE_APP_TITLE=Fitness Tracker
VITE_API_URL=https://your-api.com
VITE_FIREBASE_API_KEY=your_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_domain
# ... other variables as needed
```

### 4. Start development server

```bash
npm run dev
```

The application will be available at `http://localhost:5173`

## 💻 Usage

### Development

```bash
# Start development server with hot-reload
npm run dev

# Compile and minify for production
npm run build

# Preview production build
npm run preview

# Run linter
npm run lint

# Format code with Prettier
npm run format
```

### Build for production

```bash
npm run build
```

Optimized files will be generated in the `dist/` directory.

### Deployment

#### Netlify
```bash
npm run build
netlify deploy --prod
```

#### Vercel
```bash
npm run build
vercel --prod
```

#### GitHub Pages
```bash
npm run build
npm run deploy
```

## 📁 Project Structure

```
vuejs-fitness-app/
├── public/              # Static files
├── src/
│   ├── assets/         # Images, fonts, global styles
│   ├── components/     # Reusable components
│   │   ├── common/    # Common components (buttons, cards, etc.)
│   │   ├── workout/   # Workout-related components
│   │   └── charts/    # Data visualization components
│   ├── views/         # Application views/pages
│   │   ├── Home.vue
│   │   ├── Dashboard.vue
│   │   ├── Workouts.vue
│   │   └── Profile.vue
│   ├── router/        # Vue Router configuration
│   ├── store/         # Global state (Pinia/Vuex)
│   ├── composables/   # Vue 3 composable functions
│   ├── services/      # API services and business logic
│   ├── utils/         # Helper functions
│   ├── types/         # TypeScript types (if applicable)
│   ├── App.vue        # Root component
│   └── main.js        # Entry point
├── .env.example       # Environment variables example
├── .gitignore
├── index.html
├── package.json
├── vite.config.js     # Vite configuration
└── README.md
```

## 📜 Available Scripts

| Script | Description |
|--------|-------------|
| `npm run dev` | Starts the development server |
| `npm run build` | Compiles the application for production |
| `npm run preview` | Preview the production build |
| `npm run lint` | Runs the linter to check code |
| `npm run format` | Formats code with Prettier |
| `npm test` | Runs unit tests |
| `npm run test:e2e` | Runs end-to-end tests |

## 🗺 Roadmap

- [x] Initial project structure
- [x] Authentication system
- [x] Workouts CRUD
- [ ] Integration with wearables (Fitbit, Apple Watch)
- [ ] Offline mode / PWA
- [ ] Share achievements on social media
- [ ] Challenge system between users
- [ ] Nutrition and meal planning
- [ ] Data export (PDF, CSV)
- [ ] Native mobile app (React Native / Flutter)

## 🤝 Contributing

Contributions are welcome! If you'd like to contribute to this project:

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

Please make sure to update tests as appropriate and follow the project's style guidelines.

### Bug Reports

If you find a bug, please open an issue with:
- Clear description of the problem
- Steps to reproduce
- Expected vs. actual behavior
- Screenshots (if applicable)
- Browser version and operating system

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## 📧 Contact

**Leonel Acosta**

- GitHub: [@leonel-acosta](https://github.com/leonel-acosta)
- LinkedIn: [Your LinkedIn](https://linkedin.com/in/your-profile)
- Email: your.email@example.com

Project Link: [https://github.com/leonel-acosta/vuejs-fitness-app](https://github.com/leonel-acosta/vuejs-fitness-app)

## 🙏 Acknowledgments

- Tutorial followed: [YouTube Video Link](https://www.youtube.com/watch?v=JAgeFLJYrUY)
- [Vue.js Documentation](https://vuejs.org/)
- [Vite Documentation](https://vitejs.dev/)
- [Vue Router Documentation](https://router.vuejs.org/)
- [Pinia Documentation](https://pinia.vuejs.org/)
- Vue.js community on Discord and forums

---

⭐ If you found this project helpful, consider giving it a star on GitHub!

**Made with ❤️ and Vue.js**