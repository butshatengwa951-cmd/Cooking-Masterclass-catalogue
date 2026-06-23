MasterClass Food & Drink Instructors - Vue 3
Project Overview
A responsive Vue 3 single-page app that displays a carousel of premium cooking instructors and masterclasses. Users can browse chef profiles, view course details, pricing in South African Rand (ZAR), and save courses to a wishlist. Built with Vue 3 Composition API, <script setup> syntax, and CSS-only animations for the chef name glow effect.

Key Features

Interactive instructor cards with hover effects
Wishlist functionality with live count via HelloWorld component
ZAR currency formatting using Intl.NumberFormat with en-ZA locale
Responsive horizontal scroll carousel
Sold-out state handling with overlay
CSS spotlight + gradient text animations
Installation and Run Instructions
1. Prerequisites
Make sure you have these installed:

Node.js v18 or higher
npm v9 or higher
Check your versions:

bash
node -v
npm -v
2. Install Dependencies
Clone the repository and install packages:

Bash
git clone <your-repo-url>
cd masterclass-food-instructors
npm install
Main dependency: vue@^3.4.0. This project uses Vite as the build tool.

3. Run Development Server
Start the local dev server with hot-reload:

Bash
npm run dev
The app will be available at http://localhost:5173

4. Build for Production
Create an optimized production build in the dist/ folder:

Bash
npm run build
Preview the production build locally:

Bash
npm run preview
5. Project Structure
Code
├── src/
│   ├── App.vue                 # Main app: instructor carousel + wishlist logic
│   ├── components/
│   │   └── HelloWorld.vue      # Displays wishlist count in header
│   ├── assets/
│   │   └── logo.svg            # MasterClass logo
│   └── main.js                 # App entry point
├── public/
├── index.html
├── package.json
├── vite.config.js
└── README.md

7 lines hidden
Configuration Notes
All prices are in South African Rand (ZAR) and formatted with en-ZA locale
To add/edit instructors, update the instructors array in src/App.vue
Images are currently loaded from external URLs. Replace img fields with local paths if needed
Wishlist state is stored in memory only - it resets on page refresh
Tech Stack
Vue 3 - Composition API with <script setup>
Vite - Build tool and dev server
CSS3 - Scoped styles, animations, responsive layout
