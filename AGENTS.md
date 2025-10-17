# Repository Guidelines

## Project Structure & Module Organization
- Root contains standalone “bubbles” as HTML apps: `index.html`, `duplicator-showdown.html`, `pokemon-sim-gemini.html`, etc.
- `images/` stores thumbnails and in‑app assets.
- `src/` holds placeholders for future modularization (`app/`, `components/`, `data/`, `lib/`, `types/`). Today, bubbles are self‑contained files.
- No formal build system; pages are static HTML/CSS/JS.

## Build, Test, and Development Commands
- Run locally (no build step):
  - Python: `python3 -m http.server 5173` → open `http://localhost:5173/index.html`.
  - Node (no package.json needed): `npx serve -l 5173 .` or `npx http-server -p 5173`.
- Format (optional but encouraged): `npx prettier -w "*.{html,css,js}"`.
- Quick quality check: `npx lighthouse http://localhost:5173/index.html --view`.

## Coding Style & Naming Conventions
- Indentation: 2 spaces. Keep lines ≈100 chars.
- HTML: semantic elements; add `aria-*`/labels for interactive controls.
- CSS: prefer custom properties; BEM‑ish class names (`.bubble__title`, `.bubble--active`).
- JS: `camelCase` for variables/functions; avoid globals; keep scripts scoped per page.
- Filenames: kebab‑case, no spaces: `new-bubble-name.html`; assets `images/new-bubble-name.png`.

## Testing Guidelines
- Manual smoke test per bubble: load page, trigger pop/navigation, check console is clean, test reduced‑motion behavior, verify links from `index.html`.
- Cross‑browser sanity: latest Chrome and Safari.
- If adding automated tests, place in `tests/` and use Playwright; name `bubble-name.spec.ts`. Keep coverage pragmatic (core interactions only).

## Commit & Pull Request Guidelines
- Commits: short, imperative tense (e.g., `add bubble: duplicator showdown`, `ui: refine pop animation`). Group related changes.
- PRs must include: concise description, linked issues (if any), before/after screenshot or short GIF/WebM, manual test notes, and an `index.html` update when adding a new bubble.
- Keep diffs focused; avoid unrelated reformatting.

## Security & Asset Tips
- Do not commit API keys or secrets; this repo is static—use a proxy or env‑backed service if needed.
- Optimize images (<1 MB when possible); prefer `.png`/`.webp` and descriptive names.

## Agent‑Specific Instructions
- Make minimal, targeted patches; do not rename files unless required.
- Avoid adding external CDNs; keep bubbles self‑contained for portability.
