# Farm Copilot — merged workspace

This folder contains two projects wired together for local development:

- `frontend/` — your React + Vite app (UI, pages, components — untouched)
- `backend/` — your friend's Express API (routes, agents, data — untouched)

They were **already compatible out of the box**: the frontend calls relative
`/api/...` paths, and `frontend/vite.config.js` already proxies `/api` and
`/uploads` to `http://localhost:5005`, which matches the backend's default
port. No source code was rewritten to connect them.

## 1. Install dependencies

```bash
npm run install:all
```

(This runs `npm install` inside both `backend/` and `frontend/`, plus
installs `concurrently` at the root for the `dev` script below.)

## 2. Set up environment variables

Both projects ship an `.env.example` with variable **names only** — no
secrets are included anywhere in this zip.

```bash
cp backend/.env.example backend/.env
cp frontend/.env.example frontend/.env
```

Then fill in real values in each `.env` (these files are already git-ignored):

**backend/.env**
- `PORT` (defaults to 5005 if unset)
- `GEMINI_API_KEY`
- `GOOGLE_MAPS_API_KEY`
- `OPENWEATHER_API_KEY`
- `ANTHROPIC_API_KEY`

**frontend/.env**
- `VITE_GOOGLE_MAPS_API_KEY`

## 3. Run both together

```bash
npm run dev
```

This starts the backend on `:5005` and the frontend on `:5173`
simultaneously (via `concurrently`), with the Vite dev server proxying API
calls to the backend. Open `http://localhost:5173`.

To run them separately instead: `npm run backend` / `npm run frontend`.

## What already works end-to-end

- Crop diagnosis — `POST /api/advisory`
- Weather + disease risk — `GET /api/weather`, `GET /api/weather/forecast-alerts`
- Treatment lookup — `POST /api/treatment`, `GET /api/treatment/diseases`, `GET /api/treatment/nearby-shops`
- Product catalog — `GET /api/products`
- AI handshake test — `GET /api/verify/gemini-handshake`
- Product authenticity check — `POST /api/verify`

## What the backend doesn't implement yet

The frontend already has try/catch around every API call, so these will
fail gracefully (error state, not a crash) — but they won't function until
the backend adds the routes:

- `/api/auth/*` — login, signup, geocode, reverse-geocode
- `/api/vendor/*` — orders CRUD, delivery updates, shops, sync-shops
- `/api/equipment/*` — types, owners, requests, accept flows, self-register
- `/api/farms/*` — CRUD
- `/api/soil/*` — tests, analyze
- `/api/treatment/ip-location`

`backend/agents/*.js` (orchestrator, diagnosisAgent, productAgent,
safetyAgent, authenticityAgent) are present but empty (0 bytes) and not
imported by `index.js` — dead scaffolding your friend hasn't filled in yet.

No fake endpoints or mock data were added to hide these gaps — the plan was
to preserve real backend behavior, not simulate it.
