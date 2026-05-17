# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A single-file browser-based Tic Tac Toe game with a South Park theme. No build tools, dependencies, or package manager — everything lives in `tic-tac-toe.html`.

## Running the Game

Open the file directly in a browser:
- **Windows:** `Start-Process "tic-tac-toe.html"` (PowerShell) or double-click in Explorer
- **Local server (optional):** `python -m http.server 3000 --directory .` then visit `http://localhost:3000/tic-tac-toe.html`

## Architecture

Everything is contained in `tic-tac-toe.html` in three sections:

**CSS (`<style>`)** — Responsive layout using `min(22vmin, 115px)` for cells so the board always fits in the viewport. Colorado mountain scene background via CSS gradient. Winner cells use a `pulse` keyframe animation.

**HTML (`<body>`)** — Static 3×3 grid of `.cell` divs with `data-i` attributes (0–8). Score display and a single restart button.

**JavaScript (`<script>`)** — Inline, no frameworks.
- `cartmanSVG` / `stanSVG` — inline SVG strings injected into cells via `innerHTML` on click (Cartman = X, Stan = O)
- `board[]` — flat 9-element array tracking `'X'`, `'O'`, or `''`
- `WINS` — hardcoded array of all 8 winning index triplets
- `checkWinner()` — iterates `WINS`, returns `{ winner, line }` or `{ winner: 'draw' }` or `null`
- `init()` — resets board array, clears cell `innerHTML`, restores `className`
- Score is kept in memory only (`score.X`, `score.O`, `score.D`) — resets on page reload

## GitHub

Remote: `https://github.com/NivKonst/tic-tac-toe` (branch: `master`)

**Always commit and push every change made to this project to the GitHub repository above.** No change should be left uncommitted.

```bash
git add tic-tac-toe.html
git commit -m "your message"
git push
```
