# Repository Guidelines

Whatever action you can do yourself, please do it yourself, this includes starting apps and verification.

## Project Structure & Module Organization

This is an Astro 5 marketing site. Routes live in `src/pages/`; use lowercase, hyphenated names such as `sobre-nosotros.astro`. Shared page chrome belongs in `src/layouts/Layout.astro`. Reusable UI is under `src/components/`, with page sections grouped by feature and primitives in `atoms/`. Imported logos live in `src/assets/`; directly served fonts and videos live in `public/`. Treat `DESIGN.md` as the visual-system source of truth. Do not commit `.astro/`, `dist/`, or `node_modules/`.

There is currently no dedicated test directory. If tests are introduced, colocate unit tests as `Component.test.ts` or place browser tests in `tests/`.

## Build, Test, and Development Commands

- `npm install` installs the locked dependencies from `package-lock.json`.
- `npm run dev` starts Astro's local development server.
- `npm run build` creates `dist/` and is required before review.
- `npm run preview` serves the production build locally for final browser checks.
- `npm run astro -- --help` exposes additional Astro CLI commands.

No automated test, lint, or format script is configured yet. Do not claim those checks passed; use `npm run build` and focused manual testing.

## Coding Style & Naming Conventions

Use two-space indentation, UTF-8, ES modules, and Astro's strict TypeScript configuration. Name components in PascalCase (`GoldenTouch.astro`), variables and functions in camelCase, and CSS classes in kebab-case. Keep component styles scoped; place shared tokens, fonts, and base rules in `Layout.astro`. Prefer semantic HTML, Spanish alt text, keyboard-accessible controls, and existing CSS custom properties. Use GSAP only for sequences CSS cannot express, and support `prefers-reduced-motion`.

## Testing Guidelines

For UI changes, verify desktop and mobile layouts, navigation keyboard behavior, media loading, and reduced-motion fallbacks. Confirm all routes build and inspect the affected pages with `npm run preview`. New test tooling should include an `npm test` script and document its scope here.

## Commit & Pull Request Guidelines

History uses short, focused subjects such as `Hero changes` and `Height fix`; there is no strict Conventional Commits policy. Prefer a clearer imperative subject, for example `Improve mobile hero spacing`, and keep unrelated changes separate. Pull requests should explain the intent, list affected routes/components, report validation commands, link relevant issues, and include before/after screenshots or recordings for visual and motion changes.

## Security & Configuration

Never commit `.env` files or credentials. Keep public assets free of private client material and use `rel="noopener noreferrer"` on external links opened in new tabs.
