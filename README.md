# Simple Template

Useful for presenting snippets and simple widgets.

## Features

- Loading animation,
- responsive menu,
- theme switcher.

[View on GitPage](https://chrisnajman.github.io/simple-template)

## JavaScript

Built with **vanilla ES6 JavaScript**, focusing on modern syntax and browser APIs.

The JavaScript has been split into separate modules, improving code modularity:

- `module-placeholder.js`: Empty module, imported into `index.js`.
- `hamburger-button.js`: See [Accessible Mobile Menu Git repository](https://github.com/chrisnajman/accessible-mobile-menu)
- `loader.js`: See [Loader Git repository](https://github.com/chrisnajman/loader)
- `theme.js`: Handles theme toggling (light/dark mode) and local storage management.

---

## Theme Toggling

The application includes a dark mode and light mode toggle:

- The current theme state is stored in **local storage** and applied automatically on page reload.
- Accessible buttons with appropriate ARIA attributes are used to improve usability.

> [!IMPORTANT]
> Remember to change `const LOCAL_STORAGE_PREFIX` in `js-modules/theme.js` to a unique identifier.

---

## Accessibility

The site is fully navigable using tab keys and up/down arrows.

---

## Testing and Compatibility

The application has been tested on the following platforms and browsers:

- **Operating System**: Windows 10
- **Browsers**:
  - Google Chrome
  - Mozilla Firefox
  - Microsoft Edge

### Device View Testing

The layout and functionality have been verified in both browser and device simulation views to ensure responsiveness and usability.

---

## How to Run

1. Clone or download the repository to your local machine.
2. Open the project folder and start a simple HTTP server (e.g., using `Live Server` in VS Code or Python's `http.server` module).
3. Open the project in a modern browser (e.g., Chrome, Firefox, or Edge).

---

## Build & Deployment Setup for `/docs` Folder

If you want to deploy a minified version of this project to **GitHub Pages**, read on.

### 1. Install Required Packages

Run this once in your project root to install dev dependencies:

```bash
npm install
```

### 2. Run the full build process

> [!IMPORTANT]
> Any assets not described in `package.json` must be added. In the current project we don't have an `img` folder. If you create one and add images to it, you have to add this to `copy:assets`, e.g.

#### Current `package.json`

```
"copy:assets": "shx cp -r  site.webmanifest favicon.ico favicon-16x16.png favicon-32x32.png apple-touch-icon.png android-chrome-192x192.png android-chrome-512x512.png docs/",
```

#### Updated `package.json` with "img"

```
"copy:assets": "shx cp -r  img site.webmanifest favicon.ico favicon-16x16.png favicon-32x32.png apple-touch-icon.png android-chrome-192x192.png android-chrome-512x512.png docs/",
```

etc, etc.

Then in the terminal, run:

```bash
npm run build
```

### 3. Deploy to GitHub Pages

Once you've created a repository and pushed the files,

- go to `https://github.com/[your-name]/[your-project-name]/settings/pages`.
- Under "Build and deployment > Branch" make sure you set the branch to `main` and folder to `/docs`.
- Click "Save".

> [!NOTE]
> For a detailed description of the build process, configuration files and npm packages see my [GitHub Pages Optimised Build](https://github.com/chrisnajman/github-pages-optimised-build).
