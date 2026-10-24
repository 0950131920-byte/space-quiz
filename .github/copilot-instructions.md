# Copilot instructions

## Project shape

This is a dependency-free, single-page Spanish space-exploration quiz. The whole app lives in the root `index.html`: semantic markup, inline CSS, the question data, and browser-native JavaScript. Open that file directly in a browser; no server or install step is required.

The `questions` array is the source of truth for quiz content. Runtime state (`current`, `score`, and `answered`) drives `renderQuestion`, answer feedback, progress, and the final results screen. Keep quiz changes consistent across those flows rather than duplicating question or scoring data in the markup.

## Build, test, and lint

There are no package manifests or configured build, test, or lint commands. For a local run, open `index.html` directly in a browser. For a browser smoke test, answer questions through the final screen and verify correct/incorrect feedback, score and progress updates, question transitions, keyboard focus, and the displayed final score. Repeat with both light and dark system color schemes when changing theme styles.

## Code conventions

- Keep the app self-contained in `index.html`; use browser APIs and avoid adding a framework, external runtime dependency, or server requirement.
- Keep visible interface copy in Spanish. Add or edit quiz prompts, choices, correct-answer indexes, and explanations in the `questions` array.
- Define visual tokens as CSS custom properties in `:root` and override theme values in `@media (prefers-color-scheme: dark)`. Keep decorative astronomy elements behind the app content and non-interactive.
- Preserve semantic native controls and accessibility behavior: answer and navigation controls are buttons; progress uses a labeled `progressbar`; feedback uses a status region; focus moves to the new question or result heading after transitions. Keep visible keyboard focus and honor `prefers-reduced-motion`.
- Render dynamic question text with `textContent` and build answer controls with DOM methods. The results screen currently uses a template string for its fixed result copy and score.
