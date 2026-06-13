#!/bin/bash
set -e

GITHUB_USER="eFlexor"
REPO_NAME="bootstrap-vite-pro-starter"
PROJECT_DIR="$REPO_NAME"

echo "🚀 Creating $PROJECT_DIR..."
mkdir -p "$PROJECT_DIR" && cd "$PROJECT_DIR"

# ─── Directories ───
mkdir -p .github/workflows
mkdir -p .husky
mkdir -p public
mkdir -p src/js/utils
mkdir -p src/scss/components
mkdir -p src/assets/images
mkdir -p tests

# ─── .gitignore ───
cat > .gitignore << 'EOF'
node_modules
dist
.DS_Store
*.log
coverage
.env
.vscode/*
!.vscode/extensions.json
EOF

# ─── .nvmrc ───
cat > .nvmrc << 'EOF'
20.10.0
EOF

# ─── .editorconfig ───
cat > .editorconfig << 'EOF'
root = true

[*]
charset = utf-8
end_of_line = lf
indent_style = space
indent_size = 2
insert_final_newline = true
trim_trailing_whitespace = true
EOF

# ─── vite.config.js ───
cat > vite.config.js << 'EOF'
import { defineConfig } from 'vite';

export default defineConfig({
  root: 'src',
  build: {
    outDir: '../dist',
    emptyOutDir: true,
    sourcemap: true,
  },
  server: {
    port: 3000,
    open: true,
  },
  css: {
    devSourcemap: true,
  },
});
EOF

# ─── vitest.config.js ───
cat > vitest.config.js << 'EOF'
import { defineConfig } from 'vitest/config';

export default defineConfig({
  test: {
    environment: 'jsdom',
    globals: true,
    setupFiles: './tests/setup.js',
  },
});
EOF

# ─── eslint.config.js (Flat Config) ───
cat > eslint.config.js << 'EOF'
import globals from 'globals';
import js from '@eslint/js';

export default [
  js.configs.recommended,
  {
    languageOptions: {
      globals: {
        ...globals.browser,
        ...globals.node,
      },
      ecmaVersion: 'latest',
      sourceType: 'module',
    },
    rules: {
      'no-unused-vars': 'warn',
      'no-console': 'off',
    },
  },
];
EOF

# ─── prettier.config.js ───
cat > prettier.config.js << 'EOF'
export default {
  semi: true,
  singleQuote: true,
  tabWidth: 2,
  trailingComma: 'es5',
  printWidth: 100,
  endOfLine: 'lf',
};
EOF

# ─── package.json ───
cat > package.json << 'EOF'
{
  "name": "bootstrap-vite-pro-starter",
  "private": true,
  "version": "1.0.0",
  "type": "module",
  "engines": { "node": ">=20.0.0" },
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "test": "vitest",
    "test:coverage": "vitest --coverage",
    "lint": "eslint .",
    "lint:fix": "eslint . --fix",
    "format": "prettier --write .",
    "format:check": "prettier --check .",
    "prepare": "husky"
  },
  "dependencies": {
    "@popperjs/core": "^2.11.8",
    "bootstrap": "^5.3.3"
  },
  "devDependencies": {
    "@eslint/js": "^9.17.0",
    "@testing-library/jest-dom": "^6.6.3",
    "@vitest/coverage-v8": "^2.1.8",
    "eslint": "^9.17.0",
    "globals": "^15.14.0",
    "husky": "^9.1.7",
    "jsdom": "^25.0.1",
    "lint-staged": "^15.3.0",
    "prettier": "^3.4.2",
    "sass": "^1.83.0",
    "vite": "^6.0.7",
    "vitest": "^2.1.8"
  },
  "lint-staged": {
    "*.{js,ts}": ["eslint --fix", "prettier --write"],
    "*.{scss,css,json,html,md}": ["prettier --write"]
  }
}
EOF

# ─── public/robots.txt ───
cat > public/robots.txt << 'EOF'
User-agent: *
Allow: /
EOF

# ─── public/favicon.svg (simple inline placeholder) ───
cat > public/favicon.svg << 'EOF'
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100">
  <rect width="100" height="100" rx="20" fill="#0d6efd"/>
  <text x="50" y="65" font-size="45" text-anchor="middle" fill="white" font-family="sans-serif">B</text>
</svg>
EOF

# ─── src/index.html ───
cat > src/index.html << 'EOF'
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta name="description" content="A modern JavaScript and Bootstrap starter template." />
    <meta name="theme-color" content="#0d6efd" />

    <meta property="og:title" content="Bootstrap Vite Pro Starter" />
    <meta property="og:type" content="website" />

    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <link rel="preconnect" href="https://fonts.googleapis.com" />

    <title>Bootstrap Vite Pro Starter</title>

    <script type="module" src="./js/main.js"></script>
  </head>
  <body>
    <nav class="navbar navbar-expand-lg bg-body-tertiary">
      <div class="container">
        <a class="navbar-brand fw-bold" href="#">Bootstrap Vite Pro</a>
      </div>
    </nav>

    <main class="container py-5">
      <div class="p-5 mb-4 bg-body-tertiary rounded-3 border">
        <div class="container-fluid py-5">
          <h1 class="display-5 fw-bold">Ready to build 🚀</h1>
          <p class="col-md-8 fs-4 text-secondary">
            Modern JS, Bootstrap Sass, Vite, and testing configured out of the box.
          </p>
          <button class="btn btn-primary btn-lg" type="button" data-bs-toggle="tooltip" title="Bootstrap JS works!">
            Test Bootstrap JS
          </button>
        </div>
      </div>

      <div class="row align-items-md-stretch">
        <div class="col-md-6">
          <div class="h-100 p-5 text-white bg-primary rounded-3">
            <h2>Vite Powered</h2>
            <p>Lightning fast HMR and optimized builds with zero config bloat.</p>
          </div>
        </div>
        <div class="col-md-6">
          <div class="h-100 p-5 bg-body-tertiary border rounded-3">
            <h2>Bootstrap Sass</h2>
            <p>Import only the components you need. Theme with Sass variables.</p>
          </div>
        </div>
      </div>
    </main>

    <footer class="container py-3 text-center text-secondary border-top">
      <small>&copy; Bootstrap Vite Pro Starter</small>
    </footer>
  </body>
</html>
EOF

# ─── src/scss/_variables.scss ───
cat > src/scss/_variables.scss << 'EOF'
// Bootstrap overrides
$primary: #0d6efd;
$enable-shadows: true;
$enable-gradients: true;
$font-family-base: 'Inter', system-ui, -apple-system, sans-serif;

// Required Bootstrap parts
@import "bootstrap/scss/functions";
@import "bootstrap/scss/variables";
@import "bootstrap/scss/variables-dark";
@import "bootstrap/scss/maps";
@import "bootstrap/scss/mixins";
@import "bootstrap/scss/root";

// Layout & components (pick what you need)
@import "bootstrap/scss/reboot";
@import "bootstrap/scss/type";
@import "bootstrap/scss/images";
@import "bootstrap/scss/containers";
@import "bootstrap/scss/grid";
@import "bootstrap/scss/buttons";
@import "bootstrap/scss/nav";
@import "bootstrap/scss/navbar";
@import "bootstrap/scss/helpers";

// Utilities API last
@import "bootstrap/scss/utilities/api";
EOF

# ─── src/scss/main.scss ───
cat > src/scss/main.scss << 'EOF'
@import "variables";

// Your custom components below
EOF

# ─── src/js/utils/helpers.js ───
cat > src/js/utils/helpers.js << 'EOF'
/**
 * Format a date to a readable string
 * @param {Date} date
 * @returns {string}
 */
export function formatDate(date) {
  return new Intl.DateTimeFormat('en-US', {
    month: 'short',
    day: 'numeric',
    year: 'numeric',
  }).format(date);
}

/**
 * Capitalize first letter of a string
 * @param {string} str
 * @returns {string}
 */
export function capitalize(str) {
  if (!str) return '';
  return str.charAt(0).toUpperCase() + str.slice(1);
}
EOF

# ─── src/js/app.js ───
cat > src/js/app.js << 'EOF'
import { formatDate } from './utils/helpers.js';

export function initApp() {
  console.log(`App initialized on ${formatDate(new Date())}`);
}
EOF

# ─── src/js/main.js ───
cat > src/js/main.js << 'EOF'
import '../scss/main.scss';
import * as bootstrap from 'bootstrap';
import { initApp } from './app.js';

document.addEventListener('DOMContentLoaded', () => {
  initApp();

  const tooltipTriggerList = document.querySelectorAll('[data-bs-toggle="tooltip"]');
  [...tooltipTriggerList].map((el) => new bootstrap.Tooltip(el));
});
EOF

# ─── tests/setup.js ───
cat > tests/setup.js << 'EOF'
import '@testing-library/jest-dom/vitest';
EOF

# ─── tests/utils.test.js ───
cat > tests/utils.test.js << 'EOF'
import { describe, it, expect } from 'vitest';
import { formatDate, capitalize } from '../src/js/utils/helpers';

describe('Utils', () => {
  it('formats date correctly', () => {
    const date = new Date('2024-01-01');
    expect(formatDate(date)).toBe('Jan 1, 2024');
  });

  it('capitalizes a string', () => {
    expect(capitalize('hello')).toBe('Hello');
    expect(capitalize('')).toBe('');
  });
});
EOF

# ─── .github/workflows/ci.yml ───
cat > .github/workflows/ci.yml << 'EOF'
name: CI

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version-file: '.nvmrc'
          cache: 'npm'

      - run: npm ci
      - run: npm run lint
      - run: npm run format:check
      - run: npm run test:coverage
      - run: npm run build
EOF

# ─── .husky/pre-commit ───
cat > .husky/pre-commit << 'EOF'
npx lint-staged
EOF
chmod +x .husky/pre-commit

# ─── README.md ───
cat > README.md << EOF
# Bootstrap Vite Pro Starter

[![CI](https://github.com/$GITHUB_USER/$REPO_NAME/actions/workflows/ci.yml/badge.svg)](https://github.com/$GITHUB_USER/$REPO_NAME/actions)

> A modern, opinionated starter for vanilla JavaScript + Bootstrap 5 projects.

## Features

- ⚡ **Vite** for lightning-fast HMR and builds
- 🎨 **Bootstrap Sass** with variable overrides (no CDN bloat)
- 📦 Native ES Modules
- 🧪 **Vitest** + jsdom for unit testing
- 🧹 **ESLint v9 flat config** + Prettier
- 🐶 **Husky** + lint-staged pre-commit hooks
- 🚀 GitHub Actions CI/CD

## Quick Start

\`\`\`bash
nvm use              # Uses .nvmrc (Node 20+)
npm install
npm run dev          # Starts http://localhost:3000
\`\`\`

## Scripts

| Command | Description |
|---------|-------------|
| \`npm run dev\` | Start Vite dev server |
| \`npm run build\` | Production build (outputs to \`dist/\`) |
| \`npm run preview\` | Preview production build |
| \`npm run test\` | Run unit tests in watch mode |
| \`npm run test:coverage\` | Run tests with coverage |
| \`npm run lint\` | Lint JavaScript |
| \`npm run lint:fix\` | Lint and auto-fix issues |
| \`npm run format\` | Format all files with Prettier |
| \`npm run format:check\` | Check formatting without writing |

## Project Structure

\`\`\`
src/
├── index.html          # Entry HTML
├── js/
│   ├── main.js         # Entry script (imports SCSS + Bootstrap)
│   ├── app.js          # App initialization
│   └── utils/
│       └── helpers.js  # Shared utilities
├── scss/
│   ├── _variables.scss # Bootstrap overrides + imports
│   └── main.scss       # Your custom styles
└── assets/
    └── images/
\`\`\`

## Customizing Bootstrap

Edit \`src/scss/_variables.scss\`. Override variables **before** importing Bootstrap (e.g., \`$primary: #yourColor;\`). Only the Bootstrap components listed in that file are included, so remove any you don't need to reduce bundle size.

## License

MIT
EOF

# ─── LICENSE ───
cat > LICENSE << 'EOF'
MIT License

Copyright (c) 2024 eFlexor

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
EOF

# ─── Git init & push ───
git init
git add .
git commit -m "feat: initial modern starter with Vite + Bootstrap Sass + Vitest"

echo ""
echo "=========================================="
echo "✅ Project scaffolded at: $(pwd)"
echo "=========================================="
echo ""
echo "Next steps:"
echo "1. Create an EMPTY repo on GitHub named: $REPO_NAME"
echo "   (No README, no license, no .gitignore)"
echo ""
echo "2. Then run:"
echo ""
echo "   git remote add origin https://github.com/$GITHUB_USER/$REPO_NAME.git"
echo "   git branch -M main"
echo "   git push -u origin main"
echo ""
echo "3. Finally, install dependencies:"
echo ""
echo "   cd $REPO_NAME"
echo "   npm install"
echo "   npm run dev"
echo ""
