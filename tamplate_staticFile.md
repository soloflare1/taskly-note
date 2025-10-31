# Tailwind CSS Setup with PostCSS in Django

## 1. Install Tailwind CSS

You can install Tailwind CSS using PostCSS:

```bash
npm install tailwindcss @tailwindcss/postcss postcss
```

Or define it in **`package.json`**:

```json
{
  "devDependencies": {
    "autoprefixer": "^10.4.20",
    "postcss": "^8.4.49",
    "tailwindcss": "^3.4.16"
  },
  "scripts": {
    "build:tailwind": "npx tailwindcss -i ./static/css/tailwind.css -o ./static/css/output.css --minify",
    "watch:tailwind": "npx tailwindcss -i ./static/css/tailwind.css -o ./static/css/output.css --watch"
  }
}
```

**Notes:**

* `watch:tailwind` → continuously watches your files and auto rebuilds `output.css`.
* `build:tailwind` → builds Tailwind CSS once and minifies it.

Run the following in terminal:

```bash
npm install
```

Check that the following were created:

* `node_modules/` folder
* `package-lock.json` file

---

## 2. Create `postcss.config.js`

At the project root, create a file called `postcss.config.js`:

```javascript
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
};
```

---

## 3. Initialize Tailwind CSS

Run in terminal:

```bash
npx tailwindcss init
```

Check that **`tailwind.config.js`** file is created.

Edit **`tailwind.config.js`**:

```javascript
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

### Configure template paths

* **Project-level templates:** `./templates/**/*.html`
* **App-level templates:** `./**/templates/**/*.html`

Final **`tailwind.config.js`**:

```javascript
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./templates/**/*.html",     // Templates at project level
    "./**/templates/**/*.html",  // Templates inside apps
  ],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

---

## 4. Create Tailwind CSS File

Inside `static/css/`, create **`tailwind.css`** and add:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

---

## 5. Build or Watch CSS
don’t need to run the build/watch commands separately because they are already defined in package.json
* To build once (minified):

```bash
npm run build:tailwind
```

* To watch continuously:

```bash
npm run watch:tailwind
```

Output file will be:

```
static/css/output.css
```
