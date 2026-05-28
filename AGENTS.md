# parse-dashboard

## Stack
Node.js 18/20/22, Express, React, SCSS, Webpack

## Structure
- `Parse-Dashboard/`: Server entry points, Express middleware, CLI helper, authentication logic
- `src/components/`: Reusable React UI components with `.react.js` suffix and `.scss` styles
- `src/dashboard/`: Main application views, routing, and data management
- `src/lib/`: Utilities, stores (Analytics, Jobs, Schema), and helper functions
- `src/login/`: Authentication UI components
- `webpack/`: Build configurations for dev, production, and the component styleguide (PIG)
- `ci/`: CI/CD validation scripts

## Run & test
```bash
npm install
npm start                    # Dev server on :4040
npm test                     # Run test suite
npm run build               # Production build
parse-dashboard --dev --appId <id> --masterKey <key> --serverURL <url>  # CLI mode
```

## Conventions
- React components use PascalCase with `.react.js` extension; styles use matching `.scss` filename
- Component examples live alongside as `.example.js`; tests as `.test.js`
- Server supports both CLI standalone and Express middleware programmatic use
- Configuration via `parse-dashboard-config.json` or environment variables (`PARSE_DASHBOARD_*`)
- Security: HTTPS enforced in production; Basic Auth and MFA supported via config
- Icons and static assets served from configurable folders relative to config file

## Key files
- `Parse-Dashboard/index.js`: Main module export and CLI entry
- `Parse-Dashboard/server.js`: Express app initialization and middleware setup
- `src/dashboard/Dashboard.js`: Root React component with routing
- `src/lib/AppsManager.js`: App configuration and data fetching logic
- `package.json`: Scripts, dependencies, and engine requirements

## Rules
- **Never** use `--dev` flag in production (disables HTTPS checks, auth, and master key encryption)
- **Never** commit master keys or passwords in configuration files; use environment variables
- **Always** deploy behind HTTPS when not using `--dev`
- Maintain compatibility with Parse Server >= 2.1.4 and Node.js LTS versions (18, 20, 22)
- Support both single-app and multi-app configurations in all features
