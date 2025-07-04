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
- `primary-navigation.js` and `hamburger-button.js`: See [Accessible Mobile Menu Git repository](https://github.com/chrisnajman/accessible-mobile-menu)
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

## Build and Deployment Notes

The following assumes you have `node` installed on your machine.

### Installing Dependencies

Before running the build commands, install the required packages (`esbuild postcss postcss-nesting postcss-cli cssnano`) as dev dependencies:

```bash
npm i
```

### Why `/docs`?

- The `/docs` folder contains optimized production-ready assets, including:
  - `bundle.js`: the JavaScript bundled into a single file (no modules)
  - `style.min.css`: the CSS processed with nesting flattened and minified
- The original source files (`index.js`, files in `js-modules/`, `style.css` with nesting, etc.) remain in the project root for easier development and editing.
- GitHub Pages is configured to serve the site from the `/docs` folder instead of the root, so your published site uses these optimized files.

> [!IMPORTANT]
> If you're publishing on GitHub Pages, make sure the Pages setting is configured to serve from the `/docs` folder on the `main` branch.

### The `postcss.config.js` file

- Located in the project root, this configuration file instructs PostCSS how to process your CSS:
  - It enables CSS nesting support with `postcss-nesting`.
  - It minifies the final CSS using `cssnano`.
- This file is automatically used during the **build** process when PostCSS runs.

### Build Script

> [!IMPORTANT]
> Before running the build script:

- Make sure you have _manually_ **copied** all files (images, favicons, etc ) that are used in the site from the project root to `/docs`.
- Make sure you have _manually_ **copied** all HTML files from the project root to `/docs` (excluding e.g. `README.md`, `LICENSE` and `.gitignore`).
- Ensure that the `script` and `link rel="stylesheet"` tags in the updated HTML files in `/docs` are coded as:

```html
<script
  src="./bundle.js"
  defer
></script>
<link
  rel="stylesheet"
  href="./style.min.css"
/>
```

... instead of the code in the HTML found in the project root:

```html
<script
  src="./index.js"
  type="module"
></script>
<link
  rel="stylesheet"
  href="./style.css"
/>
```

#### Run the Build Script

To update the built assets in `/docs` after editing source files, run:

```bash
npm run build
```

This runs the following tasks:

- Bundles and minifies JavaScript using `esbuild`.
- Processes and minifies CSS using `postcss`.

---
