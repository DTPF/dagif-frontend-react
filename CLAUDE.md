# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

DaGif (gif_challenge_react) — a React SPA for uploading, browsing, and sharing GIFs. Users authenticate via Auth0, upload GIFs to Cloudinary, and browse/search by category. Production: https://dagif.dtpf.es/

## Commands

- `npm run dev` — start dev server on localhost:5170
- `npm run build` — production build
- `npm test` — run tests (Jest via react-scripts)

## Architecture

**Build system:** Create React App (react-scripts) with TypeScript. Absolute imports from `src/` (tsconfig `baseUrl: "src"`).

**State management:** React Context + useReducer (Redux-like pattern). Four contexts wrap the app in `App.tsx`:
- `UserProvider` — Auth0 user + DB user, dispatches via `reducers/user/`
- `GifProvider` — global GIF list, dispatches via `reducers/gif/`
- `MyGifsProvider` — authenticated user's GIFs, dispatches via `reducers/myGifs/`
- `SearchProvider` — search query state

Each context has: `context/<name>/` (Provider, Context, initialState) paired with `reducers/<name>/` (reducer + action creators).

**Routing:** React Router v6 with `createBrowserRouter`. All pages are lazy-loaded with `Suspense`. Route protection via `ProtectedUser` and `ProtectedGif` middleware components in `router/user.middelware.ts`.

**API layer:** `src/api/` contains `gif.api.ts`, `user.api.ts`, `category.api.ts`. Base URL switches between `localhost:4000/api/v1` (dev) and same-origin `/api/v1` (prod) via `api/utils/config.ts`.

**Auth:** Auth0 with separate client IDs and audiences for development vs production (determined by `utils/isLocalhost`).

**UI:** Ant Design (`antd`) component library + SCSS for custom styles. Dark theme configured via Ant Design `ConfigProvider` token.

**Views structure:**
- `views/pages/` — route-level page components
- `views/components/basic/` — feature components (allGifs, categories, gifForm, etc.)
- `views/components/UI/` — small reusable UI components
- `views/layouts/` — layout wrappers (BasicLayout with header/footer)
- `views/utils/` — HelmetSEO for page meta tags

## Environment Variables

Copy `.env.example` to `.env`. Required vars: Auth0 domain, client IDs (dev/prod), audiences (dev/prod), public URL. Default port: 5170.
