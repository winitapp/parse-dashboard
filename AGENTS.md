# parse-dashboard

## Stack
Node.js 18/20/22, React + Express, Webpack.

## Structure
- `Parse-Dashboard/` - Express server, CLI entry points, and authentication logic
- `src/` - React frontend source
  - `components/` - Reusable React components (.react.js files with .scss)
  - `dashboard/` - Main dashboard views, routing, and app management
  - `lib/` - Utilities, Flux-like stores, AJAX helpers, and constants
- `webpack/` - Build configurations (base, prod, PIG for component guide)
- `ci/` - Continuous integration scripts and version checks

## Run & test
```bash
npm install
npm run dev                    # Start development server
npm test                       # Run Jest tests
parse-dashboard --config parse-dashboard-config.json  # Production CLI mode
```

## Conventions
- React components use `.react.js` extension with co-located `.scss` and `.example.js`
- Test files use `.test.js` suffix in `src/lib/tests/` or adjacent to components
- Flux pattern: stores in `src/lib/stores/` (e.g., SchemaStore, JobsStore)
- CLI tools organized in `Parse-Dashboard/CLI/` (mfa.js, utils.js)
- Dashboard configuration via JSON file or `PARSE_DASHBOARD_*` environment variables
- PIG (Parse Interface Guide) for component documentation in `src/parse-interface-guide/`

## Key files
- `Parse-Dashboard/app.js` - Express app configuration and middleware setup
- `Parse-Dashboard/server.js` - HTTP/HTTPS server initialization
- `Parse-Dashboard/Authentication.js` - Basic auth and MFA logic
- `src/dashboard/Dashboard.js` - Root React component and routing
- `src/lib/AJAX.js` - HTTP client for Parse Server API communication
- `package.json` - Scripts, dependencies, and engine requirements

## Rules
- **Never** use `--dev` flag in production (disables HTTPS enforcement and auth checks)
- Always deploy with HTTPS and Basic Authentication enabled in production
- Never expose `masterKey` as plain strings in config; use Functions or env vars
- Set `trustProxy: 1` only when behind verified load balancers to avoid security bypasses
- Use `masterKeyTtl` when providing masterKey as a Function to enable caching
