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
- **Start server**: `npm start` (runs `node index.js`) or `node index.js` directly.
- **Development mode**: `npm run dev` (uses nodemon for auto-reload on file changes).
- **Edit content**: Update `haikus.json` - contains array of objects with `text` and `image` properties.
- **Change UI**: Edit `views/index.ejs` for HTML structure and `public/css/main.css` for styling.
- **Add images**: Place files in `public/images/` and reference them in `haikus.json`.

## Patterns & Conventions
- All server logic is in `index.js` (no routes folder).
- EJS is used for templating; see `views/index.ejs` for variable usage.
- Static assets are referenced relative to `/public` (e.g., `/css/main.css`, `/images/filename.jpg`).
- No test framework or build step is present.
- Minimal dependencies: `express`, `ejs` (production), `nodemon` (development).
- Haiku data structure: `{ "text": "multiline\nhaiku\ntext", "image": "filename.jpg" }`
- Images are expected to be in `public/images/` directory.

## Integration Points
- No external APIs or databases; all data is local in `haikus.json`.
- Designed for easy deployment in Codespaces and similar environments.
- Azure App Service ready with `web.config` for IIS deployment.
- PM2 configuration in `process.json` for production process management.
- Environment variable `PORT` supported (defaults to 3000).

## Example: Rendering Haikus
```js
// index.js - Complete server setup
const haikus = require('./haikus.json');
app.get('/', (req, res) => {
  res.render('index', { haikus });
});
```

```json
// haikus.json - Data structure
[
  {
    "text": "rain in seattle,\ndon't forget an umbrella,\nor it will be gloom",
    "image": "puddle_jumper_octodex.jpg"
  }
]
```

## Key Files
- `index.js`: Main server file (13 lines, Express setup)
- `haikus.json`: Content data (array of haiku objects)
- `views/index.ejs`: HTML template (loops through haikus array)
- `public/css/main.css`: Responsive styling with mobile breakpoints
- `public/images/`: Static image assets (5 GitHub Octocat themed images)
- `package.json`: Dependencies and npm scripts
- `process.json`: PM2 configuration for production
- `web.config`: IIS/Azure App Service configuration

---
For questions about unclear conventions or missing documentation, ask the user for clarification or examples from their workflow.
