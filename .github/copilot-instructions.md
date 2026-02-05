# Tailwind Playground - AI Coding Instructions

## Project Overview
Minimal Tailwind CSS v4 playground powered by Vite. Used for rapid UI prototyping and experimenting with Tailwind utilities.

## Tech Stack
- **Tailwind CSS v4** with the new `@tailwindcss/vite` plugin (not the older PostCSS approach)
- **Vite 7** as the dev server and bundler
- **ES Modules** (`"type": "module"` in package.json)

## Key Architecture Patterns

### Tailwind v4 Setup
This project uses Tailwind CSS v4's new architecture:
- CSS entry point: [src/styles.css](src/styles.css) uses `@import "tailwindcss"` (not `@tailwind` directives)
- Vite plugin: [vite.config.js](vite.config.js) uses `@tailwindcss/vite` instead of PostCSS config
- No `tailwind.config.js` needed—Tailwind v4 uses CSS-based configuration

### UI Rendering Pattern
All UI is rendered via JavaScript in [src/main.js](src/main.js):
- Import styles first: `import './styles.css'`
- Inject HTML with Tailwind classes into `document.body.innerHTML`
- Use template literals for multi-line HTML with embedded Tailwind classes

## Developer Workflows

### Development
```bash
npm run dev    # Start Vite dev server with HMR
```

### Production Build
```bash
npm run build   # Build to dist/
npm run preview # Preview production build locally
```

## Conventions

### Styling
- Use Tailwind utility classes directly in HTML—no custom CSS
- For gradients: `bg-gradient-to-{direction} from-{color} to-{color}`
- For hover states: `hover:` prefix (e.g., `hover:bg-indigo-700`)
- For transitions: `transition-{property}` utilities

### Component Structure
When adding new UI components, follow the pattern in `main.js`:
```javascript
document.body.innerHTML = `
<div class="...container classes...">
  <div class="...card/component classes...">
    <!-- content -->
  </div>
</div>
`
```
