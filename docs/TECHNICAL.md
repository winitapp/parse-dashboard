# parse-dashboard

## What it does
Standalone web dashboard for managing Parse Server applications. Provides data browsing, push notifications, user management, and Cloud Code execution through a React-based interface.

## Stack
| Layer | Technology |
|-------|------------|
| Runtime | Node.js 18, 20, 22 |
| Frontend | React 18, SCSS |
| Backend | Express.js 4 |
| Build | Webpack 5, Babel |
| Testing | Jest |

## Architecture
```
┌─────────────┐      ┌─────────────────┐      ┌──────────────┐
│   Browser   │──────│ Parse Dashboard │──────│ Parse Server │
│ (React SPA) │      │  (Express App)  │      │  (REST API)  │
└─────────────┘      └─────────────────┘      └──────────────┘
                            │
                    ┌───────┴───────┐
                    │  Auth Layer   │
                    │ (Basic/MFA)   │
                    └───────────────┘
```

## Run locally
1. `npm install`
2. Create `parse-dashboard-config.json` with serverURL, appId, masterKey
3. `npm run dev` (starts on localhost:4040)
4. Or CLI: `parse-dashboard --dev --config parse-dashboard-config.json`

## Request flow
1. Express serves built React bundle or handles CLI startup
2. User authenticates via Basic Auth or OTP (MFA)
3. React app bootstraps and fetches configured apps via `/apps` endpoint
4. Dashboard components query Parse Server REST API through `src/lib/AJAX.js`
5. Express proxies requests to Parse Server using provided masterKey

## External dependencies
- Parse Server — Target backend for data and push notifications
- MongoDB/Postgres — Database backing Parse Server
- Docker — Optional containerization (Dockerfile provided)
- Nginx — Recommended reverse proxy for SSL termination
