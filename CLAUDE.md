# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project structure

Single-file application: `basketball_stats.html` — all HTML, CSS, and JavaScript lives in this one file.

No build step, no package manager, no dependencies to install. Open the file directly in a browser to run it.

## Architecture

- **Data layer**: `stats` (array of player objects) and `meta` (match info) are held in memory and persisted to `localStorage` under the key `basketball_stats_v2`.
- **Rendering**: The table is fully rebuilt via `buildTable()` on load/reset/import. Incremental DOM updates (`updateStatCell`, `updateFaltasCell`, `updateRowClass`) are used for counter changes to avoid full rebuilds.
- **Tabs**: `registro` (live stat entry), `resumen` (team totals + per-player table), `lideres` (top-5 leaders per category). The summary and leaders tabs rebuild their content on each activation.
- **Player object shape**: `{ id, num, nombre, faltas, reb, asist, blq, rob, tp, pts }`.
- **Icons**: Tabler Icons loaded from CDN (`@tabler/icons-webfont`).

## Key functions

| Function | Purpose |
|---|---|
| `buildTable()` | Full DOM rebuild of the players table |
| `createRow(p)` | Creates a `<tr>` for a player with inline event handlers |
| `inc(id, key)` / `dec(id, key)` | Increment/decrement any stat, save, and patch DOM |
| `setFalta(id, n)` | Toggle-style falta setter (click active falta to undo) |
| `saveToStorage()` / `loadFromStorage()` | localStorage persistence |
| `exportJSON()` / `importJSON(event)` | File-based backup/restore |

## Lint / validation

No linter is configured. If adding one, prefer a browser-compatible vanilla JS validator (e.g. `eslint` with `eslint:recommended` and no module syntax rules) since the script uses global functions and inline `onclick` handlers intentionally.
