# 55murphy-site

Quartz 4 static site for the 55 Murphy Rd renovation project. Published to GitHub Pages at `rmrny.github.io/55murphy-site`.

## Stack
- **Framework:** Quartz 4.5.2 (Markdown → static site generator)
- **Content:** Obsidian-flavored Markdown in `content/`
- **Config:** `quartz.config.ts` (site settings), `quartz.layout.ts` (layout)
- **Build:** `npx quartz build` / `npx quartz build --serve` for dev

## Commands
- Dev server: `npx quartz build --serve`
- Build: `npx quartz build`
- Format: `npm run format`
- Type check: `npm run check`

## Content Structure
Content lives in `content/` — subdirectories include budget, bom, drawings, schedules, selections. Obsidian ignore patterns: `private`, `templates`, `.obsidian`.
