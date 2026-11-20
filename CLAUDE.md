# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Arcade Vault: an online platform for playing games and competing for the highest scores. The project follows spec-driven development (`/spec` and `/spec-impl` workflow, per README; skills from `Klerith/fernando-skills`, installed via `npx skills@latest add Klerith/fernando-skills`). Currently a fresh Create Next App scaffold (only `app/layout.tsx`, `app/page.tsx`, `app/globals.css`).

## Commands

- `npm run dev` — dev server (Turbopack) at http://localhost:3000
- `npm run build` / `npm start` — production build / serve
- `npm run lint` — ESLint (flat config, `eslint.config.mjs`). No test runner is configured yet.

## Next.js version caveat

Next 16.4.6 / React 19.3 — has breaking changes vs. typical training data. Per `AGENTS.md`, read the relevant guide in `node_modules/next/dist/docs/` (`01-app`, `02-pages`, `03-architecture`, `04-community`) before writing Next.js code, and heed deprecation notices.

## Configuration notes

- `next.config.ts` enables `cacheComponents`, `partialPrefetching`, and `experimental.agentFeedback`. `cacheComponents` changes caching/rendering semantics for App Router code, so check the docs before using data fetching or dynamic APIs.
- Tailwind v4 is wired through a Turbopack rule (`@tailwindcss/turbopack` loader for `*.css`) in `next.config.ts`, not PostCSS. Theme tokens are defined in `app/globals.css` via `@theme inline` (light/dark via `prefers-color-scheme`).
- Path alias: `@/*` maps to the repo root (e.g. `@/app/...`).
- App Router only (`app/` directory at the root, no `src/`).
