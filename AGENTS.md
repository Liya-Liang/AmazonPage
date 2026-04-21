# Repository Guidelines

## Project Structure & Module Organization

This repository stores static pages published through GitHub Pages. Keep the root `index.html` as a lightweight directory page, and place each business page in its own folder.

- `index.html`: repository landing page listing available pages
- `README.md`: repository-level publishing notes
- `fba-advisor-page/index.html`: current FBA advisor page entry point
- `fba-advisor-page/assets/`: page-specific downloads and supporting files
- `fba-advisor-page/README.md`: local run and publishing notes
- `fba-advisor-page/SPEC.md`: content and design reference

For new pages, follow the same pattern: `page-name/index.html` with a local `assets/` directory when needed.

## Build, Test, and Development Commands

There is no build pipeline. Edit static files directly and preview locally.

- `cd /tmp/github/AmazonPage/fba-advisor-page && python3 -m http.server 8080`  
  Run a local static server at `http://localhost:8080`.
- `cd /tmp/github/AmazonPage/fba-advisor-page && npx serve .`  
  Alternative local preview command.
- `git status`  
  Check changed files before committing.

## Coding Style & Naming Conventions

Use semantic HTML, readable CSS sections, and minimal inline JavaScript. Match the existing 2-space indentation across HTML, CSS, and JS. Prefer relative links such as `./assets/returns-guide.pdf`; never commit local machine paths like `file:///C:/...`.

Use lowercase kebab-case for new page folders, for example `returns-dashboard/`. Keep top-level filenames conventional: `README.md`, `AGENTS.md`, `index.html`.

## Testing Guidelines

There is no automated test suite yet. Validate changes manually before opening a PR:

- run a local static server
- verify layout on desktop and mobile widths
- confirm anchor links and downloads work
- confirm published paths remain under `/AmazonPage/<page-folder>/`

## Commit & Pull Request Guidelines

Follow the existing Conventional Commit style seen in history, such as `feat: add fba advisor static page under subdirectory for GitHub Pages` or `feat: move desktop credit info from sidebar to footer`.

PRs should include a short summary, affected page paths, screenshots for visual changes, and the expected GitHub Pages URL when relevant.

## GitHub Pages Notes

GitHub Pages is served from the `main` branch root. Do not move a page into the repository root unless the site structure is being intentionally redesigned.
