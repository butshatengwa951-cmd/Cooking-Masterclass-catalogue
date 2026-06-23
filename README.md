# MasterClass Food & Drink Instructors - Vue 3

## Project Overview

A responsive Vue 3 single-page application showcasing premium food and drink instructors through an interactive carousel experience. Users can browse chef profiles, explore masterclass details, view pricing in South African Rand (ZAR), and save courses to a wishlist.

The application is built using Vue 3's Composition API with `<script setup>` syntax and includes modern CSS animations such as glowing chef names, spotlight hover effects, and responsive layouts.

---

## Key Features

* Interactive instructor cards with hover animations
* Wishlist functionality with real-time course count updates
* South African Rand (ZAR) currency formatting using `Intl.NumberFormat`
* Responsive horizontal scrolling carousel
* Sold-out course state with visual overlay indicators
* CSS spotlight effects and animated gradient text
* Modern Vue 3 Composition API architecture

---

## Installation & Setup

### Prerequisites

Ensure the following are installed on your system:

* Node.js v18 or higher
* npm v9 or higher

Verify your installation:

```bash
node -v
npm -v
```

---

### Install Dependencies

Clone the repository and install the required packages:

```bash
git clone <your-repository-url>
cd masterclass-food-instructors
npm install
```

**Main Dependency:**

```json
vue@^3.4.0
```

This project uses **Vite** as the build tool and development server.

---

### Run the Development Server

Start the local development environment with hot module replacement (HMR):

```bash
npm run dev
```

The application will be available at:

```text
http://localhost:5173
```

---

### Build for Production

Generate an optimized production build:

```bash
npm run build
```

The compiled files will be created in the `dist/` directory.

To preview the production build locally:

```bash
npm run preview
```

---

## Project Structure

```text
masterclass-food-instructors/
├── src/
│   ├── App.vue
│   │   └── Main application component containing:
│   │       - Instructor carousel
│   │       - Wishlist functionality
│   │       - Course display logic
│   │
│   ├── components/
│   │   └── HelloWorld.vue
│   │       └── Displays wishlist count in the header
│   │
│   ├── assets/
│   │   └── logo.svg
│   │       └── MasterClass logo asset
│   │
│   └── main.js
│       └── Application entry point
│
├── public/
├── index.html
├── package.json
├── vite.config.js
└── README.md
```

---

## Configuration Notes

### Currency Formatting

All course prices are displayed in **South African Rand (ZAR)** using:

```javascript
new Intl.NumberFormat("en-ZA", {
  style: "currency",
  currency: "ZAR",
})
```

### Managing Instructors

To add, edit, or remove instructors, update the `instructors` array located in:

```text
src/App.vue
```

### Image Sources

Instructor images are currently loaded from external URLs. To use local images:

1. Add image files to the `src/assets/` directory.
2. Import them into `App.vue`.
3. Replace the corresponding `img` property values.

### Wishlist Storage

Wishlist data is currently stored in application memory only and will reset whenever the page is refreshed.

---

## Tech Stack

### Frontend Framework

* Vue 3
* Composition API
* `<script setup>` syntax

### Build Tooling

* Vite

### Styling

* CSS3
* Scoped component styles
* Responsive design techniques
* Custom animations and hover effects

---

## Future Improvements

Potential enhancements for future versions include:

* Persisting wishlist data using Local Storage
* Course search and filtering functionality
* Instructor detail pages
* Backend integration for dynamic content
* User authentication and profiles
* Dark mode support

---

## License

This project is intended for educational and portfolio purposes. Modify and distribute according to your project's licensing requirements.
![Uploading Screenshot 2026-06-23 120817.png…]()

