# Space Quiz — Copilot Instructions

## What this is
A single self-contained static page: `index.html`. There is no build step, no package
manager, no bundler, and no test suite — all CSS and JavaScript live inline in `<style>`
and `<script>` tags in that one file.

## Running / testing changes
There is nothing to install or build. To preview changes, just open `index.html` directly
in a browser (or serve the folder with any static file server, e.g. `npx serve .`) and
reload. Verify behavior manually in the browser; there are no automated tests or linters
configured.

## Architecture (all in `index.html`)
- **Data**: `questions` is a hardcoded array of objects `{ q, options, answer }`, where
  `answer` is the index into `options` of the correct choice. Add/edit quiz content by
  editing this array directly.
- **State**: three module-level variables drive everything — `current` (question index),
  `score`, and `answered` (guards against double-answering a question).
- **Render flow**: `renderQuestion()` paints the current question and resets UI state;
  `selectAnswer(i, btn)` locks in an answer, applies `.correct`/`.wrong` classes, updates
  the score, and reveals the `next-btn`; the `next-btn` click handler advances `current`
  and either re-renders or calls `showResults()`; `showResults()` swaps `#question-view`
  for `#results-view` and picks an emoji/verdict based on score percentage; `restart-btn`
  resets state and re-renders from question 0.
- Everything is wired via `document.getElementById` lookups done once at the top of the
  IIFE — there's no framework, no modules, and no build-time templating.

## Conventions
- Keep everything in the single `index.html` file unless there's a strong reason to split
  it out (this is a deliberate "no tooling" project).
- Theming uses CSS custom properties on `:root` with a `prefers-color-scheme: dark`
  override block — add new colors there rather than hardcoding hex values in rules.
- UI state transitions are done by toggling classes (`.show`, `.hidden`, `.correct`,
  `.wrong`) rather than inline style manipulation; follow that pattern for new UI states.
