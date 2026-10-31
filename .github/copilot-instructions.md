# Copilot instructions

## Project shape and data flow

- This is a self-contained Korean space quiz in `index.html`: semantic markup, inline CSS, question data, and application logic all live in that file. Keep it directly openable in a browser without a server or external dependencies.
- The `questions` array is the quiz source of truth. Each item has `question`, `answers`, zero-based `correct`, and explanatory `fact` fields. `renderQuestion()` renders the current item and progress; `selectAnswer()` locks choices, updates the score, and shows feedback; the next button advances or calls `showResults()`; restart resets the state.
- If changing the number of questions, keep the progress, score denominator, result copy/thresholds, and visible totals consistent with `questions.length`.

## Repository conventions

- Keep all user-facing copy in Korean and retain `<html lang="ko">`.
- Use native `<button>` elements for choices and actions. Preserve the existing focus flow: focus the new question after advancing and the restart button on results. Keep progress and feedback exposed with their current ARIA semantics.
- Keep colors in CSS custom properties, with light-mode overrides in `@media (prefers-color-scheme: light)`. Preserve the reduced-motion override when adding animations.
- JavaScript uses `questionIndex` and `score` as state; question rendering updates the existing DOM hooks by ID. Keep dynamic answer text assigned as text rather than interpolated into HTML.
- There are no repository-defined build, test, or lint commands. Verify changes by opening `index.html` directly in a browser and exercising answer selection, scoring, progress, results, restart, keyboard focus, and both color schemes.
