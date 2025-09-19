# Copilot Instructions for AI Coding Agents

## Project Overview
This is a Node.js web application for demoing Codespaces, based on the Azure node sample. The app serves haikus and static assets, using Express and EJS for templating.

## Architecture & Key Components
- **index.js**: Main entry point. Sets up Express server, routes, and EJS view engine.
- **public/**: Static assets (CSS, images). Served via Express static middleware.
- **views/index.ejs**: Main HTML template rendered for the root route.
- **haikus.json**: Data file containing haikus displayed on the site.

## Data Flow
- On GET `/`, the server loads haikus from `haikus.json` and renders them using `views/index.ejs`.
- Static files (CSS/images) are served from `public/`.

## Developer Workflows
- **Start server**: `node index.js` (or use `npm start` if defined in `package.json`).
- **Edit haikus**: Update `haikus.json`.
- **Change UI**: Edit `views/index.ejs` and `public/css/main.css`.

## Patterns & Conventions
- All server logic is in `index.js` (no routes folder).
- EJS is used for templating; see `views/index.ejs` for variable usage.
- Static assets are referenced relative to `/public`.
- No test framework or build step is present.
- Minimal dependencies; see `package.json` for details.

## Integration Points
- No external APIs or databases; all data is local.
- Designed for easy deployment in Codespaces and similar environments.

## Example: Rendering Haikus
```js
// index.js
const haikus = require('./haikus.json');
app.get('/', (req, res) => {
  res.render('index', { haikus });
});
```

## Key Files
- `index.js`, `haikus.json`, `views/index.ejs`, `public/css/main.css`

---
For questions about unclear conventions or missing documentation, ask the user for clarification or examples from their workflow.
