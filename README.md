
# Accessibility Widget (SkillBlend Internship Assignment)

## Overview
This project is a **Floating Accessibility Widget** built with **Vue 3** and **Vite**.  
It enables users to customize their browsing experience for improved accessibility and usability.  

The widget is embedded via a floating button at the bottom-right corner of the page, which expands into a menu containing multiple accessibility options.

---

## Features

### Visual Adjustments
- **High Contrast Mode** – Enhances overall color contrast.
- **Bigger Text** – Increases font size for better readability.
- **Text Spacing** – Increases letter and line spacing.
- **Dyslexia-Friendly Font** – Uses a dyslexia-friendly font (Atkinson Hyperlegible).
- **Color Blind Mode** – Applies a grayscale filter to improve color distinction.

### Behavior Controls
- **Hide Images** – Hides all images on the page.
- **Pause Animations** – Pauses CSS and JS animations for motion-sensitive users.

### Interface Tools
- **Highlight Links** – Emphasizes links with a red underline.
- **Show Page Structure** – Outlines all headings to visualize page hierarchy.

### Additional
- **Floating Button** – Always visible at the bottom-right, expands into the accessibility menu.
- **Persistent Settings** – User preferences are saved in `localStorage` and re-applied on page reload.

---

## Tech Stack
- **Vue 3 (Composition API)** – Component-based architecture.
- **Vite** – Modern build tool for fast development.
- **CSS Variables & Classes** – Lightweight approach for accessibility effects.
- **LocalStorage** – Stores user settings for persistence.

---

## Project Structure
```
a11y-widget/
├── src/
│   ├── App.vue
│   ├── components/
│   │   ├── FloatingButton.vue
│   │   └── MenuPanel.vue
│   ├── main.js
│   └── assets/
├── index.html
├── package.json
├── vite.config.js
└── README.md
```

---

## Setup & Run

### Prerequisites
- Node.js (>= 16.x)
- npm (>= 8.x)

### Installation
```bash
# Clone repository
git clone https://github.com/Abqariyahhh/accessibility_widget.git

# Navigate to project folder
cd accessibility_widget.git

# Install dependencies
npm install
```

### Start Development Server
```bash
npm run dev
```
The app will be available at `http://localhost:5173`.

---

## Implementation Choices
1. **Scoped Content Filters** – Contrast & color blind filters applied only on `.content-container` to prevent floating button shifts.
2. **Font Selection** – Used [Atkinson Hyperlegible](https://brailleinstitute.org/freefont) as a dyslexia-friendly font.
3. **LocalStorage** – Ensures persistent user preferences.
4. **Separated Components** – `FloatingButton` and `MenuPanel` split for clarity and reusability.
5. **Removed Tooltips** – Browser-native tooltips were not reliable and were excluded for simplicity.

---


## Demo
- **Video**: https://www.loom.com/share/47754b4a03af4c70ac09e92662759c13?sid=d97eb007-8b5d-42d2-93e2-3798ec24a30b 

---

## Author
Abqariyah Yakheen
Developed as part of the **SkillBlend Internship Assignment**.

---

## License
This project is released under the MIT License.
